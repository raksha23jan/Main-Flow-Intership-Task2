Tables to Create
 1. Students:
 ○ Already created in Task 1.
 ○ Contains student details such as student_id, name, and email.
 2. Courses:
 ○ Fields:
 ■ course_id: Primary Key.
 ■ course_name: Name of the course.
 ■ course_description: Optional field for details.
 3. Enrolments:
 ○ Fields:
 ■ enrolment_id: Primary Key.
 ■ student_id: Foreign Key referencing the Students table.
 ■ course_id: Foreign Key referencing the Courses table.
 ■ enrolment_date: Date of enrolment

(see image for code)


Task 1: List all students and the courses they are enrolled in.
 ● UseanINNERJOINtocombine Students, Courses, and Enrolments tables.
 ● Select the student name and course name for all enrolled students.
code:
SELECT Student.Name AS StudentName, Courses.CourseName AS CourseEnrolled FROM Enrollments JOIN Student ON Enrollments. StudentID = student.StudentID JOIN Courses ON Enrollments.CourseID = Courses.CourseID;

 Task 2: Find the number of students enrolled in each course.
 ● UseaLEFTJOINbetween Courses and Enrolments.
 ● UseGROUP BYtogroup results by course_id and course_name.
 ● UseCOUNT(student_id) to calculate the number of enrolled students.
 ● Ensure courses with no enrolments are included in the results.
code:SELECT Courses.CourseName, COUNT(Enrollments. EnrollmentID) AS NumberOfStudents FROM Courses LEFT JOIN Enrollments ON Courses.CourseID = Enrollments.CourseID GROUP BY Courses.CourseName; 

 Task 3: List students who have enrolled in more than one course.
 ● UsetheEnrolments table.
 ● Groupdata by student_id.
 ● UseCOUNT(course_id) to calculate the number of courses per student.
 ● UsetheHAVING clause to filter students with enrolments greater than 1.
code:SELECT student.Name AS StudentName, COUNT(Enrollments.CourseID) AS NumberOfCourses FROM Enrollments JOIN student ON Enrollments.StudentID = student.StudentID GROUP BY student.StudentID HAVING NumberOfCourses > 1; 


 Task 4: Find courses with no enrolled students.
 ● UseaLEFTJOINbetween Courses and Enrolments.
 ● UseWHERE enrolment_id IS NULLtofilter courses with no enrolments.
code:SELECT CourseName FROM Courses LEFT JOIN Enrollments ON Courses.CourseID = Enrollments.CourseID WHERE Enrollments.CourseID IS NULL; 
