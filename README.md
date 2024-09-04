# DB_Tasks

Design DB model for Guvi Zen class

— — — user — — — — — — — — — — — — — — — -

create table user(
userid int primary key auto_increment,
username varchar(25) unique,
useremail varchar(255) unique,
usermobile varchar(10) not null
);

— — — — — — — — — course — — — — — — — — — — — -

create table course(
course_id int auto_increment primary key,
userid int,
course_name varchar(25),
course_duration varchar(255),
course_fees varchar(25),
foreign key(userid) references user(userid)
);

— — — — — — — — -admissions — — — — — — — — — — — — — — -
create table admissions(
userid int,
course_id int,
admission_fees varchar(25),
foreign key(userid) references user(userid),
foreign key(course_id) references course(course_id)
);

— — — — — — — codekata — — — — — — — — — — — — — — —
create table codekata(
userid int,
solved_problem varchar(25) not null,
foreign key(userid) references user(userid)
);

— — — — — — — — — mentor — — — — — — — — — — — — — — — — -

create table mentor(
userid int,
course_id int not null,
mentor_name varchar(25) ,
foreign key(userid) references user(userid),
foreign key(course_id) references course(course_id)
);

— — — — — — — — — — — — —studentsAttendance — — — — — — — — — — — —
create table studentsAttendance(
A_id int,
userid int,
A_date datetime default now(),
status boolean default true,
foreign key(userid) references user(userid)
);

— — — — — — — — — — task — — — — — — — — —
create table task(
userid int,
submited_task varchar(25) not null,
task_mark varchar(25) ,
foreign key(userid) references user(userid)
);

— — — — — — — leaderboard — — — — — — — — — — — — — — —

create table leaderboard(
userid int,
course_id int,
batch varchar(25) not null,
submited_task varchar(25) not null,
foreign key(userid) references user(userid),
foreign key(course_id) references course(course_id)
);

— — — — — — — — — queries — — — — — — — — — — -
create table queries (
userid int,
topics varchar(2000),
reasons_queries varchar(2550),
foreign key (userid) references user(userid)
);