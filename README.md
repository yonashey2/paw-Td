# paw-Td
Bouhala Chaimaa A2
my works in the Td Paw class
for attendance_system in php wamp server: 
CREATE DATABASE attendance_system;
CREATE TABLE students (
    id INT AUTO_INCREMENT PRIMARY KEY,
    fullname VARCHAR(100) NOT NULL,
    matricule VARCHAR(50) NOT NULL UNIQUE,
    group_id VARCHAR(50) NOT NULL
);

CREATE TABLE attendance_sessions (
    id INT AUTO_INCREMENT PRIMARY KEY,
    course_name VARCHAR(100) NOT NULL,
    group_id VARCHAR(50) NOT NULL,
    opened_by VARCHAR(100) NOT NULL,
    session_date DATE NOT NULL,
    status ENUM('open','closed') DEFAULT 'open'
);

CREATE TABLE attendance_records (
    id INT AUTO_INCREMENT PRIMARY KEY,
    session_id INT NOT NULL,
    student_id INT NOT NULL,
    status ENUM('present','absent') DEFAULT 'absent',
    FOREIGN KEY (session_id) REFERENCES attendance_sessions(id),
    FOREIGN KEY (student_id) REFERENCES students(id)
);
