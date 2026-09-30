# Hospital-data-base-mysql
CREATE DATABASE IF NOT EXISTS hospital;
use hospital;

-- patient details
create table patient(patient_no varchar (226) primary key unique,
first_name varchar(226),
last_name varchar(226),
diagnosis varchar(226),
age int,
marital_status varchar(226),
state_of_origin varchar(226),
gender varchar(226),
blood_group varchar (226),
payment_method enum("personal", "hmo","staff", "guardian"),
payment_status enum("cleared", "not cleared"));


-- payment details
create table payment(bill decimal(11,2),
amount_paid decimal(11,2),
balance decimal(11,2),
payment_method enum("personal","hmo","staff","guardian"),
payment_package enum("family plan", "individual plan", "one off"),
patient_no varchar (226),
foreign key(patient_no) references patient(patient_no));


-- discharge form
create table discharge(patient_relationship enum( "guardian", "siblings", "friend", "spouse"),
first_name varchar(226),
last_name varchar(226),
age int,
phone_number varchar(14),
state_of_origin varchar(226),
discharge_fee decimal(8,2),
-- note discharge fee is 5000 naira
payment_method enum("cash", "transfer"),
patient_no varchar(226),
foreign key(patient_no) references patient(patient_no));

INSERT INTO patient
(patient_no, first_name, last_name, diagnosis, age, marital_status, state_of_origin, gender, blood_group, payment_method, payment_status)
VALUES
('HPR1000', 'John', 'Okafor', 'Malaria', 28, 'Single', 'Anambra', 'Male', 'O+', 'personal', 'cleared'),
('HPR1001', 'Mary', 'Adeyemi', 'Typhoid', 34, 'Married', 'Oyo', 'Female', 'A+', 'hmo', 'cleared'),
('HPR1002', 'David', 'Eze', 'Hypertension', 52, 'Married', 'Enugu', 'Male', 'B+', 'personal', 'not cleared'),
('HPR1003', 'Grace', 'Okoro', 'Malaria', 24, 'Single', 'Delta', 'Female', 'O+', 'staff', 'cleared'),
('HPR1004', 'Daniel', 'Williams', 'Diabetes', 47, 'Married', 'Rivers', 'Male', 'AB+', 'hmo', 'not cleared'),
('HPR1005', 'Blessing', 'Afolabi', 'Typhoid', 31, 'Single', 'Ogun', 'Female', 'B+', 'personal', 'cleared'),
('HPR1006', 'Michael', 'Ibrahim', 'Asthma', 19, 'Single', 'Kaduna', 'Male', 'O-', 'guardian', 'cleared'),
('HPR1007', 'Esther', 'Nwosu', 'Pneumonia', 43, 'Married', 'Imo', 'Female', 'A+', 'hmo', 'not cleared'),
('HPR1008', 'Samuel', 'Bello', 'Malaria', 36, 'Married', 'Kano', 'Male', 'B-', 'personal', 'cleared'),
('HPR1009', 'Faith', 'Joseph', 'Migraine', 27, 'Single', 'Benue', 'Female', 'O+', 'personal', 'cleared'),
('HPR1010', 'Peter', 'Umeh', 'Ulcer', 40, 'Married', 'Anambra', 'Male', 'A-', 'staff', 'not cleared'),
('HPR1011', 'Joy', 'Ekanem', 'Malaria', 22, 'Single', 'Akwa Ibom', 'Female', 'O+', 'guardian', 'cleared'),
('HPR1012', 'Anthony', 'Obi', 'Hypertension', 61, 'Married', 'Enugu', 'Male', 'B+', 'hmo', 'cleared'),
('HPR1013', 'Janet', 'Ogunleye', 'Typhoid', 29, 'Single', 'Osun', 'Female', 'AB+', 'personal', 'not cleared'),
('HPR1014', 'Emmanuel', 'Eze', 'Diabetes', 55, 'Married', 'Abia', 'Male', 'O+', 'hmo', 'not cleared'),
('HPR1015', 'Rose', 'Ibrahim', 'Asthma', 26, 'Single', 'Kwara', 'Female', 'A+', 'personal', 'cleared'),
('HPR1016', 'Chris', 'Adekunle', 'Malaria', 33, 'Married', 'Lagos', 'Male', 'B+', 'staff', 'cleared'),
('HPR1017', 'Patience', 'Okeke', 'Pneumonia', 48, 'Married', 'Anambra', 'Female', 'O-', 'hmo', 'not cleared'),
('HPR1018', 'Victor', 'Ojo', 'Ulcer', 38, 'Single', 'Ondo', 'Male', 'A+', 'personal', 'cleared'),
('HPR1019', 'Sarah', 'Danladi', 'Typhoid', 30, 'Single', 'Plateau', 'Female', 'B+', 'guardian', 'not cleared'),
('HPR1020', 'Frank', 'Chukwu', 'Hypertension', 58, 'Married', 'Imo', 'Male', 'O+', 'hmo', 'cleared'),
('HPR1021', 'Rebecca', 'Lawal', 'Malaria', 21, 'Single', 'Kogi', 'Female', 'A+', 'personal', 'cleared'),
('HPR1022', 'George', 'Udo', 'Diabetes', 49, 'Married', 'Akwa Ibom', 'Male', 'B+', 'staff', 'not cleared'),
('HPR1023', 'Mercy', 'Balogun', 'Asthma', 35, 'Single', 'Oyo', 'Female', 'AB+', 'personal', 'cleared'),
('HPR1024', 'Joseph', 'Nnamani', 'Malaria', 44, 'Married', 'Enugu', 'Male', 'O+', 'hmo', 'not cleared'),
('HPR1025', 'Helen', 'Okafor', 'Pneumonia', 39, 'Married', 'Abia', 'Female', 'A-', 'personal', 'cleared'),
('HPR1026', 'Stephen', 'Garba', 'Typhoid', 25, 'Single', 'Katsina', 'Male', 'B+', 'guardian', 'cleared'),
('HPR1027', 'Linda', 'Eze', 'Hypertension', 53, 'Married', 'Delta', 'Female', 'O+', 'hmo', 'not cleared'),
('HPR1028', 'Andrew', 'Musa', 'Ulcer', 32, 'Single', 'Niger', 'Male', 'A+', 'personal', 'cleared'),
('HPR1029', 'Cynthia', 'Onyeka', 'Malaria', 23, 'Single', 'Rivers', 'Female', 'B+', 'staff', 'cleared');


INSERT INTO payment
(bill, amount_paid, balance, payment_method, payment_package, patient_no)
VALUES
(50000.00, 50000.00, 0.00, 'personal', 'one off', 'HPR1000'),
(75000.00, 50000.00, 25000.00, 'hmo', 'individual plan', 'HPR1001'),
(120000.00, 70000.00, 50000.00, 'personal', 'individual plan', 'HPR1002'),
(45000.00, 45000.00, 0.00, 'staff', 'one off', 'HPR1003'),
(150000.00, 90000.00, 60000.00, 'hmo', 'individual plan', 'HPR1004'),
(65000.00, 65000.00, 0.00, 'personal', 'one off', 'HPR1005'),
(40000.00, 40000.00, 0.00, 'guardian', 'one off', 'HPR1006'),
(95000.00, 60000.00, 35000.00, 'hmo', 'individual plan', 'HPR1007'),
(55000.00, 55000.00, 0.00, 'personal', 'one off', 'HPR1008'),
(35000.00, 35000.00, 0.00, 'personal', 'one off', 'HPR1009'),
(85000.00, 50000.00, 35000.00, 'staff', 'individual plan', 'HPR1010'),
(45000.00, 45000.00, 0.00, 'guardian', 'one off', 'HPR1011'),
(130000.00, 130000.00, 0.00, 'hmo', 'individual plan', 'HPR1012'),
(60000.00, 40000.00, 20000.00, 'personal', 'one off', 'HPR1013'),
(145000.00, 80000.00, 65000.00, 'hmo', 'individual plan', 'HPR1014'),
(50000.00, 50000.00, 0.00, 'personal', 'one off', 'HPR1015'),
(70000.00, 70000.00, 0.00, 'staff', 'individual plan', 'HPR1016'),
(100000.00, 65000.00, 35000.00, 'hmo', 'individual plan', 'HPR1017'),
(55000.00, 55000.00, 0.00, 'personal', 'one off', 'HPR1018'),
(80000.00, 50000.00, 30000.00, 'guardian', 'one off', 'HPR1019'),
(125000.00, 125000.00, 0.00, 'hmo', 'family plan', 'HPR1020'),
(40000.00, 40000.00, 0.00, 'personal', 'one off', 'HPR1021'),
(110000.00, 70000.00, 40000.00, 'staff', 'individual plan', 'HPR1022'),
(60000.00, 60000.00, 0.00, 'personal', 'one off', 'HPR1023'),
(90000.00, 50000.00, 40000.00, 'hmo', 'individual plan', 'HPR1024'),
(75000.00, 75000.00, 0.00, 'personal', 'one off', 'HPR1025'),
(45000.00, 45000.00, 0.00, 'guardian', 'one off', 'HPR1026'),
(115000.00, 70000.00, 45000.00, 'hmo', 'individual plan', 'HPR1027'),
(65000.00, 65000.00, 0.00, 'personal', 'one off', 'HPR1028'),
(50000.00, 50000.00, 0.00, 'staff', 'one off', 'HPR1029');


INSERT INTO discharge
(patient_relationship, first_name, last_name, age, phone_number, state_of_origin, discharge_fee, payment_method, patient_no)
VALUES
('spouse', 'Michael', 'Okafor', 31, '08031234567', 'Anambra', 5000.00, 'cash', 'HPR1000'),
('spouse', 'David', 'Adeyemi', 37, '08032345678', 'Oyo', 5000.00, 'transfer', 'HPR1001'),
('siblings', 'Peter', 'Eze', 48, '08033456789', 'Enugu', 5000.00, 'cash', 'HPR1002'),
('friend', 'Daniel', 'Okoro', 29, '08034567890', 'Delta', 5000.00, 'transfer', 'HPR1003'),
('spouse', 'Sarah', 'Williams', 42, '08035678901', 'Rivers', 5000.00, 'cash', 'HPR1004'),
('siblings', 'James', 'Afolabi', 35, '08036789012', 'Ogun', 5000.00, 'transfer', 'HPR1005'),
('guardian', 'Joseph', 'Ibrahim', 45, '08037890123', 'Kaduna', 5000.00, 'cash', 'HPR1006'),
('spouse', 'Emeka', 'Nwosu', 50, '08038901234', 'Imo', 5000.00, 'transfer', 'HPR1007'),
('siblings', 'Ibrahim', 'Bello', 40, '08039012345', 'Kano', 5000.00, 'cash', 'HPR1008'),
('friend', 'Paul', 'Joseph', 33, '08040123456', 'Benue', 5000.00, 'transfer', 'HPR1009'),
('spouse', 'Catherine', 'Umeh', 39, '08041234567', 'Anambra', 5000.00, 'cash', 'HPR1010'),
('guardian', 'James', 'Ekanem', 46, '08042345678', 'Akwa Ibom', 5000.00, 'transfer', 'HPR1011'),
('spouse', 'Anthony', 'Obi', 58, '08043456789', 'Enugu', 5000.00, 'cash', 'HPR1012'),
('friend', 'Daniel', 'Ogunleye', 32, '08044567890', 'Osun', 5000.00, 'transfer', 'HPR1013'),
('siblings', 'Francis', 'Eze', 51, '08045678901', 'Abia', 5000.00, 'cash', 'HPR1014'),
('guardian', 'Rose', 'Ibrahim', 44, '08046789012', 'Kwara', 5000.00, 'transfer', 'HPR1015'),
('spouse', 'Grace', 'Adekunle', 36, '08047890123', 'Lagos', 5000.00, 'cash', 'HPR1016'),
('siblings', 'Patrick', 'Okeke', 42, '08048901234', 'Anambra', 5000.00, 'transfer', 'HPR1017'),
('friend', 'Victor', 'Ojo', 34, '08049012345', 'Ondo', 5000.00, 'cash', 'HPR1018'),
('guardian', 'Mary', 'Danladi', 47, '08050123456', 'Plateau', 5000.00, 'transfer', 'HPR1019'),
('spouse', 'Lucy', 'Chukwu', 55, '08051234567', 'Imo', 5000.00, 'cash', 'HPR1020'),
('friend', 'Rebecca', 'Lawal', 28, '08052345678', 'Kogi', 5000.00, 'transfer', 'HPR1021'),
('siblings', 'George', 'Udo', 52, '08053456789', 'Akwa Ibom', 5000.00, 'cash', 'HPR1022'),
('spouse', 'David', 'Balogun', 41, '08054567890', 'Oyo', 5000.00, 'transfer', 'HPR1023'),
('guardian', 'John', 'Nnamani', 49, '08055678901', 'Enugu', 5000.00, 'cash', 'HPR1024'),
('siblings', 'Helen', 'Okafor', 43, '08056789012', 'Abia', 5000.00, 'transfer', 'HPR1025'),
('guardian', 'Stephen', 'Garba', 50, '08057890123', 'Katsina', 5000.00, 'cash', 'HPR1026'),
('spouse', 'Linda', 'Eze', 55, '08058901234', 'Delta', 5000.00, 'transfer', 'HPR1027'),
('friend', 'Andrew', 'Musa', 36, '08059012345', 'Niger', 5000.00, 'cash', 'HPR1028'),
('spouse', 'Cynthia', 'Onyeka', 29, '08060123456', 'Rivers', 5000.00, 'transfer', 'HPR1029');


select patient_no,
gender,
blood_group
from patient;

select sum(balance),
sum(amount_paid)
from payment;

select patient_relationship
from discharge;

select concat( first_name," ", last_name)
from discharge;

select concat( first_name," ", last_name) as full_name
from discharge;

select bill - amount_paid as debt,
balance,
patient_no,
payment_method
from payment;

select bill - 500,
bill
from payment;

-- join 2 tables
select payment.patient_no,
concat(first_name, " ", last_name) as full_name,
diagnosis,
gender,
bill,
balance
from patient
join payment
on patient.patient_no = payment.patient_no;

-- join 3 tables
select payment.patient_no,
patient.first_name,
diagnosis,
gender,
bill,
balance,
discharge.first_name,
phone_number,
patient_relationship,
discharge.payment_method
from patient
join payment
on patient.patient_no = payment.patient_no
join discharge
on patient.patient_no = discharge.patient_no;

--- order by
select *
from hospital.payment
order by payment_method;

select*
from patient 
order by first_name;

-- limti 
select*
from patient 
limit 5;


-- group by
select marital_status,
count(distinct state_of_origin) as distinct_states
from patient
group by marital_status
order by marital_status desc ;


select patient.first_name,
diagnosis,
gender,
bill,
balance,
patient_relationship,
discharge.first_name,
phone_number,
discharge.patient_no
from patient
join payment
on patient.patient_no = payment.patient_no
join discharge
on patient.patient_no = discharge.patient_no;


select bill - amount_paid
from payment;

-- where 

select *
from patient;

select *
from patient
where marital_status = "single";

select first_name,
last_name,
patient_no
from patient
where payment_status = 'cleared';


select patient.patient_no,
first_name,
payment_package
from patient
join payment
on patient.patient_no = payment.patient_no
where payment_package = "individual plan";

select patient.first_name,
diagnosis,
gender,
balance,
phone_number,
patient_relationship,
discharge_fee,
discharge.payment_method
from patient 
join payment
on patient.patient_no = payment.patient_no
join discharge
on patient.patient_no = discharge.patient_no
where discharge.payment_method = "cash";

select *
from patient
where blood_group in ("O-","O+");


select *
from patient
where blood_group in ("A-","A+");


-- ASSIGNMENT
select COUNT(DISTINCT diagnosis) AS number_of_illness_types
FROM patient
WHERE age > 30
AND state_of_origin IN ("Anambra", "Rivers", "Kaduna");

select patient_no, first_name, last_name, age, marital_status, payment_method, payment_status
FROM patient
WHERE age < 40;


SELECT *
from patient
where age >=30;

select *
from patient
where state_of_origin in ("anambra","rivers","kaduna");

select diagnosis,
count(*) as patient_count
from patient
group by diagnosis;

select patient.patient_no,
patient.age,
balance as owing,
discharge.payment_method,
patient_relationship
from patient
join payment
on patient.patient_no = payment.patient_no
join discharge
on patient.patient_no = discharge.patient_no
where patient.age <40
and balance >0
and discharge.payment_method = "transfer"
and patient_relationship = "spouse";

select count(distinct diagnosis)
from patient;

select *
from patient;

 
select *
from patient
where first_name like "%a%";

select min(age) as minimum_age
from patient;

-- if function(case)

select first_name,
age,
case
when age >=60 then "elderly"
when age >=50 then "adult"
when age >=35 then "young adult"
when age >=20  then "youth"
else "adolescent"
end as age_status
from patient;

select first_name,
age,
case
when age >35 then "adult"
when age >=20 then "young adult"
else "youth"
end as age_status
from discharge;

-- subquries

select *
from patient
where age >( select avg(age)
from patient 
where marital_status = "married");

select *
from patient
where diagnosis = (select diagnosis
from patient
where patient_no = "hpr1000");

select *
from patient
where age = (select age
from patient
where patient_no = "hpr1000");


-- sub qurey with 2 table

select *
from patient
where  patient_no in ( select patient_no
from payment 
where balance > 0);

select *
from patient 
where patient_no in ( select patient_no
from payment
where bill > 100000);

-- patient who has ceared their bills ( don't have an understand)

select *
from patient
where payment_status = "cleared";

select *
from patient 
where patient_no = ( select patient_no
from payment 
where bill = ( select max(bill)
from payment));

-- 3 table
   
   select *
   from patient
   where patient_no in( select patient_no
   from payment
   where balance > 0)
   and
   patient_no in( select patient_no
   from discharge);
   
select *
from patient;

-- alter function
alter table patient
add  column genotype varchar (226);

update patient
set genotype = "as"
where patient_no = "hpr1000";

update patient
set genotype = case patient_no
when "hpr1003" then "AA"
when"hpr1004" then "SS"
when "hpr1005" then "AC"
when "hpr1006" then "SC"
END 
where patient_no in ("hpr1003","hpr1004","hpr1005","hpr1006");




select *
from patient
where patient_no in ( select patient_no
from payment
where balance >0)
and 
patient_no in ( select patient_no
from discharge);
  










   









 






































































