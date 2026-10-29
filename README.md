<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <title>Student Attendance Tracker</title>
</head>
<body>
  <h1>Student Attendance Tracker</h1>

  
  <form id="addStudentForm">
    <input type="text" id="name" placeholder="Student Name" required>
    <input type="text" id="dept" placeholder="Department" required>
    <button type="submit">Add Student</button>
  </form>

  <form id="attendanceForm">
    <input type="date" id="attDate" required>
    <select id="studentSelect" required></select>
    <button type="submit">Mark Present</button>
  </form>
</body>
</html>
Body {
  Font-family: Arial, sans-serif;
  Margin: 20px;
  Background: #f4f6f9;
  Color: #333;
}
.container {
  Max-width: 800px;
  Margin: auto;
  Background: white;
  Padding: 20px;
  Border-radius: 8px;
  Box-shadow: 0 2px 5px rgba(0,0,0,0.1);
}
Input, select, button {
  Padding: 8px;
  Margin: 5px 0;
  Border: 1px solid #ccc;
  Border-radius: 4px;
}

Button {
  Background: #2ecc71;
  Color: white;
  Border: none;
  Cursor: pointer;

}
Let students = JSON.parse(localStorage.getItem(‘students’)) || [];
Let logs = JSON.parse(localStorage.getItem(‘logs’)) || [];

Function addStudent(name, dept) {
  Students.push({ id: Date.now().toString().slice(-4), name, dept });
  saveAndRender();
}

Function markAttendance(studentId, date, status) {
  Const exists = logs.some(l => l.studentId === studentId && l.date === date);
  If (!exists) {
    Logs.push({ studentId, date, status });
    saveAndRender();
  }
}

Function saveAndRender() {
  localStorage.setItem(‘students’, JSON.stringify(students));
  localStorage.setItem(‘logs’, JSON.stringify(logs));
}
