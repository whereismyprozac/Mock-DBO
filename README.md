# Mock-DBO
Create database [AssistDatabase]--Create a database and the following tables and implement relationships in your database. stellaparker

create table Clients
(
ClientID int primary key  not null,
FirstName varchar(25) not null,
MiddleName varchar(25) null,
LastName varchar(25) not null,
Nickname varchar(25) null,
PhoneNumber varchar(10) null,
MessagePhone varchar(10) null,
StreetAddress varchar(50) null,
City varchar(50) null,
[State] varchar(2) null,
Zipcode varchar(5) null,
ACESNumber varchar(5) null,
Birthdate smalldatetime null,
SSN varchar(9) null,					
MedicareNumber varchar(9) null,
EmergencyContact varchar(200) null,  
GP varchar(25) null,
GP_PhoneNumber varchar(10) null,
Income money null,
[ValueOfAssets] money null
);
 create table Specialists
  (
 SpecialistID int primary key  not null,
 FirstName varchar(25) not null,
 LastName varchar(25) not null,
 Title varchar(25) not null
 )
create table Assists
(
AssistID int primary key  not null,
ClientID int FOREIGN KEY REFERENCES Clients(ClientID),
DateOpened smalldatetime not null,
DateClosed smalldatetime null,
SpecialistID int FOREIGN KEY REFERENCES Specialists(SpecialistID),
TypeOfAssistance varchar(250) null,
RefferalSource varchar(50) null,
RefPhone varchar(10) null,
Confidential varchar(3) null,
);

create table Tasks
(
TaskId int primary key  not null,
AssistID int FOREIGN KEY REFERENCES Assists(AssistID),
TaskDate smalldatetime not null,
FollowUpNeeded varchar(3) null,
Activity varchar(25) not null,
[Status] varchar(25) null
)

create table Outreach
(
OutreachID int primary key  not null,
OutreachDate smalldatetime not null,
[Location] varchar(50) not null,
Attendees int null,
Notes varchar(250) null
) 
insert into Clients(ClientID, FirstName, MiddleName, LastName, Nickname, PhoneNumber, MessagePhone,
StreetAddress, City, [State], Zipcode, ACESNumber, Birthdate, SSN, MedicareNumber, EmergencyContact, GP, GP_PhoneNumber,
Income, [ValueOfAssets])
values (1,'Terry', null, 'Bradshaw', null, '3603333333','3603333333','303 4th','Olympia','WA', '98501', 
null, null, null, null, null, null, null, null, null); 

insert into Clients(ClientID, FirstName, MiddleName, LastName, Nickname, PhoneNumber, MessagePhone,
StreetAddress, City, [State], Zipcode, ACESNumber, Birthdate, SSN, MedicareNumber, EmergencyContact, GP, GP_PhoneNumber,
Income, [ValueOfAssets])
values (2,'Sam', null, 'Jones', null,'3605545555', NULL, '1525 Pacific', 'Olympia', 'WA', '98501',
null, null, null, null, null, null, null, null, null );

insert into Clients(ClientID, FirstName, MiddleName, LastName, Nickname, PhoneNumber, MessagePhone,
StreetAddress, City, [State], Zipcode, ACESNumber, Birthdate, SSN, MedicareNumber, EmergencyContact, GP, GP_PhoneNumber,
Income, [ValueOfAssets])
values (3, 'Ginger', null, 'Baker', null, '3608787878', '3608787877', null, null, 
null, null, null, null, null, null, null, null, null, null, null);

insert into Clients(ClientID, FirstName, MiddleName, LastName, Nickname, PhoneNumber, MessagePhone,
StreetAddress, City, [State], Zipcode, ACESNumber, Birthdate, SSN, MedicareNumber, EmergencyContact, GP, GP_PhoneNumber,
Income, [ValueOfAssets])
values (4, 'Sarah', null, 'Hughes ', null, '3604443333', null, '8702 54th', 'Lacey', 'WA', null, 
null, null, null, null, null, null, null, null, null);

insert into Clients(ClientID, FirstName, MiddleName, LastName, Nickname, PhoneNumber, MessagePhone,
StreetAddress, City, [State], Zipcode, ACESNumber, Birthdate, SSN, MedicareNumber, EmergencyContact, GP, GP_PhoneNumber,
Income, [ValueOfAssets])
values (5, 'Lovey', null, 'Howell', null, '3607777777', '3607777755', '4226 X St.', 'Tumwater', 'WA', '98501',
null, null, null, null, null, null, null, null, null );

UPDATE Clients
SET FirstName = 'Alfred'
where MessagePhone =3603333333;

DELETE FROM Clients WHERE LastName='Terry';

insert into Specialists(SpecialistID, FirstName, LastName, Title) values(1,'BB', 'King', 'Specialist II');

insert into Specialists(SpecialistID, FirstName, LastName, Title) values(2, 'Ann', 'Wilson', 'Specialist I');

update Specialists
set FirstName = 'Tim'
where FirstName = 'BB'

delete from Specialists where FirstName = 'BB'

--select * from Clients

insert into Assists(AssistID, ClientID, DateOpened, DateClosed, SpecialistID, TypeOfAssistance, 
 RefferalSource, RefPhone, Confidential)
values(1, 3, '10/2/04', '12/12/04', 1, 'Councelling', 'Dr. Jones', 'Yes', NULL);

insert into Assists(AssistID, ClientID, DateOpened, DateClosed, SpecialistID, TypeOfAssistance, 
 RefferalSource, RefPhone, Confidential)
values(2, 3, '10/5/04', '10/5/04', 1, 'Referral', 'Dr. Barnes','No', null);

insert into Assists(AssistID, ClientID, DateOpened, DateClosed, SpecialistID, TypeOfAssistance, 
 RefferalSource, RefPhone, Confidential)
values(3, 4, '11/21/04', '1/6/05', 1, 'Forms assistance', null, null, null);

insert into Assists(AssistID, ClientID, DateOpened, DateClosed, SpecialistID, TypeOfAssistance, 
 RefferalSource, RefPhone, Confidential)
values(4, 4, '11/10/04 ', '12/7/04', 1, 'Counseling', null, null, null);

insert into Assists(AssistID, ClientID, DateOpened, DateClosed, SpecialistID, TypeOfAssistance, 
 RefferalSource, RefPhone, Confidential)
values(5, 3, '12/1/04', '12/1/04', 2, 'Referral', null, null, null);

insert into Assists(AssistID, ClientID, DateOpened, DateClosed, SpecialistID, TypeOfAssistance, 
 RefferalSource, RefPhone, Confidential)
values(6, 3, '12/18/04', null, 2, 'Dr. Eligibility', null, null, null);

insert into Assists(AssistID, ClientID, DateOpened, DateClosed, SpecialistID, TypeOfAssistance, 
 RefferalSource, RefPhone, Confidential)
values(7, 4, '12/8/04', '1/10/05', 2, 'Forms Assistance', 'Dr. Jason', '3605555555', null);

insert into Assists(AssistID, ClientID, DateOpened, DateClosed, SpecialistID, TypeOfAssistance, 
 RefferalSource, RefPhone, Confidential)
values(8, 3, '12/15/04', '12/18/04', 2, 'Counseling', null, null, null);

insert into Assists(AssistID, ClientID, DateOpened, DateClosed, SpecialistID, TypeOfAssistance, 
 RefferalSource, RefPhone, Confidential)
values(9, 1, '12/12/04', null, 1, 'Referral ', 'DSHS', null, 'No');

insert into Assists(AssistID, ClientID, DateOpened, DateClosed, SpecialistID, TypeOfAssistance, 
 RefferalSource, RefPhone, Confidential)
values(10, 1, '12/29/04', '1/29/05', 1, 'Advocacy', null, null, null);

insert into Assists(AssistID, ClientID, DateOpened, DateClosed, SpecialistID, TypeOfAssistance, 
 RefferalSource, RefPhone, Confidential)
values(11, 2, '12/27/04', '1/15/05', 1, 'Dr. Eligibility', null, null, null);
--update and delete from Assists
update Assists
set Confidential = 'No'
where DateOpened = '12/27/04'
delete from Assists where RefPhone = 'Yes'

--insert into Tasks
insert into Tasks(TaskId, AssistID, TaskDate, FollowUpNeeded, Activity, [Status]) 
values(1, 2, '10/05/04', null, 'Phone Call', 'Complete');

insert into Tasks(TaskId, AssistID, TaskDate, FollowUpNeeded, Activity, [Status]) 
values(2, 3, '12/15/04', null, 'Phone Call', 'Complete');

insert into Tasks(TaskId, AssistID, TaskDate, FollowUpNeeded, Activity, [Status]) 
values(3, 4, '12/01/04', 'Yes', 'Phone Call', null);

insert into Tasks(TaskId, AssistID, TaskDate, FollowUpNeeded, Activity, [Status]) 
values(4,6, '12/01/04', null, 'Letter', 'Complete');

insert into Tasks(TaskId, AssistID, TaskDate, FollowUpNeeded, Activity, [Status]) 
values(5, 6, '12/06/04', null, 'Phone Call', 'Complete');

insert into Tasks(TaskId, AssistID, TaskDate, FollowUpNeeded, Activity, [Status]) 
values(6, 7, '1/5/05 ', 'Yes', 'Letter', null);

insert into Tasks(TaskId, AssistID, TaskDate, FollowUpNeeded, Activity, [Status]) 
values(7, 10, '1/4/05 ', 'Yes', 'Letter', null);

update Tasks
set FollowUpNeeded = 'No'
where TaskDate = '10/05/04'

delete from Tasks where TaskDate = '10/05/04'

insert into Outreach(OutreachID, OutreachDate, [Location], Attendees, Notes)
values(1, '10/03/04', '415 4th Ave Olympia WA 98502', '4', null)

update Outreach
set Notes = 'It was snowing.'
where Notes = null
delete from Outreach where OutreachID = '1'

SELECT CONCAT(FirstName,' ',LastName) AS ClientName, A.DateOpened AS DateOpened, TypeOfAssistance
FROM Clients C, Assists A
WHERE C.ClientID = A.ClientID;


SELECT A. *, CONCAT(FirstName,' ',LastName) AS SpecialistName
FROM Assists A, Specialists S
WHERE A.SpecialistID = S.SpecialistID;

SELECT distinct CONCAT(FirstName,' ',LastName) AS ClientName
FROM Assists A, Clients C, Tasks T
WHERE A.ClientID = C.ClientID AND A.AssistID = T.AssistID AND FollowUpNeeded = 'Yes';


SELECT CONCAT(C.FirstName,' ',C.LastName) AS ClientName, CONCAT(S.FirstName,' ',S.LastName) AS SpecialistName
FROM Clients C, Assists A, Specialists S
WHERE C.ClientID = A.ClientID AND A.SpecialistID = S.SpecialistID AND DateOpened between '01/01/03' and '12/31/03';


SELECT CONCAT(C.FirstName,' ',C.LastName) AS ClientName, A.DateOpened AS AssistDate, A.TypeOfAssistance
AS TypeOfAssistance, CONCAT(S.FirstName,' ',S.LastName) AS SpecialistName
FROM Clients C, Assists A, Specialists S
WHERE C.ClientID = A.ClientID AND A.SpecialistID = S.SpecialistID AND A.DateClosed IS NULL;

CREATE VIEW [View1]
AS
SELECT CONCAT(C.FirstName,' ',C.LastName) AS ClientName, CONCAT(S.FirstName,' ',S.LastName) AS SpecialistName,
A.DateOpened, T.TaskDate, A.TypeOfAssistance
FROM Clients C, Assists A, Tasks T, Specialists S
where T. FollowUpNeeded = 1;

CREATE VIEW View2
WITH SCHEMABINDING AS
SELECT CONCAT(C.FirstName,' ',C.LastName) AS ClientName, CONCAT(S.FirstName,' ',S.LastName) AS SpecialistName,
A.DateOpened, T.TaskDate, A.TypeOfAssistance
FROM Clients C, Specialists S, Assists A, Tasks T
WHERE T.FollowUpNeeded = 'YES' 
AND A.DateClosed > DATEADD(month, 1, A.DateOpened)
create unique clustered index idx_TaskDate on dbo.View2 (TaskDate); --Needs to be fixed, not working in current state on view 
CREATE VIEW View3
AS
SELECT CONCAT(C.FirstName,' ',C.LastName) AS ClientName, CONCAT(S.FirstName,' ',S.LastName) AS SpecialistName,
A.DateOpened, T.TaskDate, A.TypeOfAssistance
FROM Clients C, Specialists S, Assists A, Tasks T
WHERE YEAR(A.DateOpened)=2005;

CREATE VIEW View4
AS
SELECT CONCAT(C.FirstName,' ',C.LastName) AS ClientName, CONCAT(S.FirstName,' ',S.LastName) AS SpecialistName,
A.DateOpened, T.TaskDate, A.TypeOfAssistance
FROM Clients C, Specialists S, Assists A, Tasks T
WHERE MONTH(A.DateOpened) between 12/01/04 and 12/31/04 
AND YEAR(A.DateOpened)= 2004;
select * from View4

CREATE VIEW View5
AS
SELECT CONCAT(Clients.FirstName,' ',Clients.LastName) AS ClientName, Clients.PhoneNumber
FROM Clients
--ORDER BY ClientName, C.PhoneNumber
create unique clustered index idx_ClientName on dbo.View5 (ClientName);

CREATE VIEW View6
AS
SELECT Specialist.SpecialistName, Activity.Date
FROM Specialist
JOIN Activity ON Specialist.SpecialistID=Activity.SpecialistID
WHERE MONTH(Activity.Date)=MONTH(GETDATE()) 
AND YEAR(Activity.Date)=YEAR(GETDATE());
--message_team_project.txt

Create database [assistDatabase]--Create a database and the following tables and implement relationships in your database. stellaparker

create table Clients
(
ClientID int primary key  not null,
FirstName varchar(25) not null,
MiddleName varchar(25) null,
LastName varchar(25) not null,
Nickname varchar(25) null,
PhoneNumber varchar(10) null,
MessagePhone varchar(10) null,
StreetAddress varchar(50) null,
City varchar(50) null,
[State] varchar(2) null,
Zipcode varchar(5) null,
ACESNumber varchar(5) null,
Birthdate smalldatetime null,
SSN varchar(9) null,					
MedicareNumber varchar(9) null,
EmergencyContact varchar(200) null,  
GP varchar(25) null,
GP_PhoneNumber varchar(10) null,
Income money null,
[ValueOfassets] money null
);
 create table Specialists
  (
 SpecialistID int primary key  not null,
 FirstName varchar(25) not null,
 LastName varchar(25) not null,
 Title varchar(25) not null
 )
create table assists
(
assistID int primary key  not null,
ClientID int FOREIGN KEY REFERENCES Clients(ClientID),
DateOpened smalldatetime not null,
DateClosed smalldatetime null,
SpecialistID int FOREIGN KEY REFERENCES Specialists(SpecialistID),
TypeOfassistance varchar(250) null,
RefferalSource varchar(50) null,
RefPhone varchar(10) null,
Confidential varchar(3) null,
);

create table Tasks
(
TaskId int primary key  not null,
assistID int FOREIGN KEY REFERENCES assists(assistID),
TaskDate smalldatetime not null,
FollowUpNeeded varchar(3) null,
Activity varchar(25) not null,
[Status] varchar(25) null
)

create table Outreach
(
OutreachID int primary key  not null,
OutreachDate smalldatetime not null,
[Location] varchar(50) not null,
Attendees int null,
Notes varchar(250) null
) 
-- Write SQL statements to insert, update, and delete a record in each of the Clients, assist, 
--Task, Outreach, and Specialist tables. 3 points stellaparker
insert into Clients(ClientID, FirstName, MiddleName, LastName, Nickname, PhoneNumber, MessagePhone,
StreetAddress, City, [State], Zipcode, ACESNumber, Birthdate, SSN, MedicareNumber, EmergencyContact, GP, GP_PhoneNumber,
Income, [ValueOfassets])
values (1,'Terry', null, 'Bradshaw', null, '3603333333','3603333333','303 4th','Olympia','WA', '98501', 
null, null, null, null, null, null, null, null, null); 

insert into Clients(ClientID, FirstName, MiddleName, LastName, Nickname, PhoneNumber, MessagePhone,
StreetAddress, City, [State], Zipcode, ACESNumber, Birthdate, SSN, MedicareNumber, EmergencyContact, GP, GP_PhoneNumber,
Income, [ValueOfassets])
values (2,'Sam', null, 'Jones', null,'3605545555', NULL, '1525 Pacific', 'Olympia', 'WA', '98501',
null, null, null, null, null, null, null, null, null );

insert into Clients(ClientID, FirstName, MiddleName, LastName, Nickname, PhoneNumber, MessagePhone,
StreetAddress, City, [State], Zipcode, ACESNumber, Birthdate, SSN, MedicareNumber, EmergencyContact, GP, GP_PhoneNumber,
Income, [ValueOfassets])
values (3, 'Ginger', null, 'Baker', null, '3608787878', '3608787877', null, null, 
null, null, null, null, null, null, null, null, null, null, null);

insert into Clients(ClientID, FirstName, MiddleName, LastName, Nickname, PhoneNumber, MessagePhone,
StreetAddress, City, [State], Zipcode, ACESNumber, Birthdate, SSN, MedicareNumber, EmergencyContact, GP, GP_PhoneNumber,
Income, [ValueOfassets])
values (4, 'Sarah', null, 'Hughes ', null, '3604443333', null, '8702 54th', 'Lacey', 'WA', null, 
null, null, null, null, null, null, null, null, null);

insert into Clients(ClientID, FirstName, MiddleName, LastName, Nickname, PhoneNumber, MessagePhone,
StreetAddress, City, [State], Zipcode, ACESNumber, Birthdate, SSN, MedicareNumber, EmergencyContact, GP, GP_PhoneNumber,
Income, [ValueOfassets])
values (5, 'Lovey', null, 'Howell', null, '3607777777', '3607777755', '4226 X St.', 'Tumwater', 'WA', '98501',
null, null, null, null, null, null, null, null, null );

UPDATE Clients
SET FirstName = 'Alfred'
where MessagePhone =3603333333;

DELETE from Clients where LastName='Terry';

insert into Specialists(SpecialistID, FirstName, LastName, Title) values(1,'BB', 'King', 'Specialist II');

insert into Specialists(SpecialistID, FirstName, LastName, Title) values(2, 'Ann', 'Wilson', 'Specialist I');

update Specialists
set FirstName = 'Tim'
where FirstName = 'BB'

delete from Specialists where FirstName = 'BB'

--select * from Clients

insert into assists(assistID, ClientID, DateOpened, DateClosed, SpecialistID, TypeOfassistance, 
 RefferalSource, RefPhone, Confidential)
values(1, 3, '10/2/04', '12/12/04', 1, 'Councelling', 'Dr. Jones', 'Yes', NULL);

insert into assists(assistID, ClientID, DateOpened, DateClosed, SpecialistID, TypeOfassistance, 
 RefferalSource, RefPhone, Confidential)
values(2, 3, '10/5/04', '10/5/04', 1, 'Referral', 'Dr. Barnes','No', null);

insert into assists(assistID, ClientID, DateOpened, DateClosed, SpecialistID, TypeOfassistance, 
 RefferalSource, RefPhone, Confidential)
values(3, 4, '11/21/04', '1/6/05', 1, 'Forms assistance', null, null, null);

insert into assists(assistID, ClientID, DateOpened, DateClosed, SpecialistID, TypeOfassistance, 
 RefferalSource, RefPhone, Confidential)
values(4, 4, '11/10/04 ', '12/7/04', 1, 'Counseling', null, null, null);

insert into assists(assistID, ClientID, DateOpened, DateClosed, SpecialistID, TypeOfassistance, 
 RefferalSource, RefPhone, Confidential)
values(5, 3, '12/1/04', '12/1/04', 2, 'Referral', null, null, null);

insert into assists(assistID, ClientID, DateOpened, DateClosed, SpecialistID, TypeOfassistance, 
 RefferalSource, RefPhone, Confidential)
values(6, 3, '12/18/04', null, 2, 'Dr. Eligibility', null, null, null);

insert into assists(assistID, ClientID, DateOpened, DateClosed, SpecialistID, TypeOfassistance, 
 RefferalSource, RefPhone, Confidential)
values(7, 4, '12/8/04', '1/10/05', 2, 'Forms assistance', 'Dr. Jason', '3605555555', null);

insert into assists(assistID, ClientID, DateOpened, DateClosed, SpecialistID, TypeOfassistance, 
 RefferalSource, RefPhone, Confidential)
values(8, 3, '12/15/04', '12/18/04', 2, 'Counseling', null, null, null);

insert into assists(assistID, ClientID, DateOpened, DateClosed, SpecialistID, TypeOfassistance, 
 RefferalSource, RefPhone, Confidential)
values(9, 1, '12/12/04', null, 1, 'Referral ', 'DSHS', null, 'No');

insert into assists(assistID, ClientID, DateOpened, DateClosed, SpecialistID, TypeOfassistance, 
 RefferalSource, RefPhone, Confidential)
values(10, 1, '12/29/04', '1/29/05', 1, 'Advocacy', null, null, null);

insert into assists(assistID, ClientID, DateOpened, DateClosed, SpecialistID, TypeOfassistance, 
 RefferalSource, RefPhone, Confidential)
values(11, 2, '12/27/04', '1/15/05', 1, 'Dr. Eligibility', null, null, null);
--update and delete from assists
update assists
set Confidential = 'No'
where DateOpened = '12/27/04'
delete from assists where RefPhone = 'Yes'

--insert into Tasks
insert into Tasks(TaskId, assistID, TaskDate, FollowUpNeeded, Activity, [Status]) 
values(1, 2, '10/05/04', null, 'Phone Call', 'Complete');

insert into Tasks(TaskId, assistID, TaskDate, FollowUpNeeded, Activity, [Status]) 
values(2, 3, '12/15/04', null, 'Phone Call', 'Complete');

insert into Tasks(TaskId, assistID, TaskDate, FollowUpNeeded, Activity, [Status]) 
values(3, 4, '12/01/04', 'Yes', 'Phone Call', null);

insert into Tasks(TaskId, assistID, TaskDate, FollowUpNeeded, Activity, [Status]) 
values(4,6, '12/01/04', null, 'Letter', 'Complete');

insert into Tasks(TaskId, assistID, TaskDate, FollowUpNeeded, Activity, [Status]) 
values(5, 6, '12/06/04', null, 'Phone Call', 'Complete');

insert into Tasks(TaskId, assistID, TaskDate, FollowUpNeeded, Activity, [Status]) 
values(6, 7, '1/5/05 ', 'Yes', 'Letter', null);

insert into Tasks(TaskId, assistID, TaskDate, FollowUpNeeded, Activity, [Status]) 
values(7, 10, '1/4/05 ', 'Yes', 'Letter', null);

update Tasks
set FollowUpNeeded = 'No'
where TaskDate = '10/05/04'

delete from Tasks where TaskDate = '10/05/04'

insert into Outreach(OutreachID, OutreachDate, [Location], Attendees, Notes)
values(1, '10/03/04', '415 4th Ave Olympia WA 98502', '4', null)

update Outreach
set Notes = 'It was snowing.'
where Notes = null
delete from Outreach where OutreachID = '1'

--/3. Write select statements to organize data from different tables. 4 points each/

--select all clients who have had an assist; include client name, assist date and type./

select ConCAT(FirstName,' ',LastName) as ClientName, A.DateOpened as DateOpened, TypeOfassistance
from Clients C, assists A
where C.ClientID = A.ClientID;

--/•    List all assists including the name of the Specialist./

select A. *, ConCAT(FirstName,' ',LastName) as SpecialistName
from assists A, Specialists S
where A.SpecialistID = S.SpecialistID;

--/•    List client names having tasks needing follow up./

select distinct ConCAT(FirstName,' ',LastName) as ClientName
from assists A, Clients C, Tasks T
where A.ClientID = C.ClientID AND A.assistID = T.assistID AND FollowUpNeeded = 'Yes';

--/•    List all clients having an assist in 2003; 
--include client name and specialist name in the result./

select ConCAT(C.FirstName,' ',C.LastName) as ClientName, ConCAT(S.FirstName,' ',S.LastName) as SpecialistName
from Clients C, assists A, Specialists S
where C.ClientID = A.ClientID AND A.SpecialistID = S.SpecialistID AND DateOpened between '01/01/03' and '12/31/03';

--/•    List all clients having an open assist; include client name, 
--assist date and type, and specialist name in the result.*/

select ConCAT(C.FirstName,' ',C.LastName) as ClientName, A.DateOpened as assistDate, A.TypeOfassistance
as TypeOfassistance, ConCAT(S.FirstName,' ',S.LastName) as SpecialistName
from Clients C, assists A, Specialists S
where C.ClientID = A.ClientID AND A.SpecialistID = S.SpecialistID AND A.DateClosed IS NULL;

CREATE VIEW [View1]
as
select ConCAT(C.FirstName,' ',C.LastName) as ClientName, ConCAT(S.FirstName,' ',S.LastName) as SpecialistName,
A.DateOpened, T.TaskDate, A.TypeOfassistance
from Clients C, assists A, Tasks T, Specialists S
where T. FollowUpNeeded = 1;

CREATE VIEW View2
WITH SCHEMABINDING as
select ConCAT(C.FirstName,' ',C.LastName) as ClientName, ConCAT(S.FirstName,' ',S.LastName) as SpecialistName,
A.DateOpened, T.TaskDate, A.TypeOfassistance
from Clients C, Specialists S, assists A, Tasks T
where T.FollowUpNeeded = 'YES' 
AND A.DateClosed > DATEADD(month, 1, A.DateOpened)
create unique clustered index idx_TaskDate on dbo.View2 (TaskDate); --Needs to be fixed, not working in current state on view 


CREATE VIEW View3
as
select ConCAT(C.FirstName,' ',C.LastName) as ClientName, ConCAT(S.FirstName,' ',S.LastName) as SpecialistName,
A.DateOpened, T.TaskDate, A.TypeOfassistance
from Clients C, Specialists S, assists A, Tasks T
where YEAR(A.DateOpened)=2005;



CREATE VIEW View4
as
select ConCAT(C.FirstName,' ',C.LastName) as ClientName, ConCAT(S.FirstName,' ',S.LastName) as SpecialistName,
A.DateOpened, T.TaskDate, A.TypeOfassistance
from Clients C, Specialists S, assists A, Tasks T
where MonTH(A.DateOpened) between 12/01/04 and 12/31/04 
AND YEAR(A.DateOpened)= 2004;
select * from View4


CREATE VIEW View5
as
select ConCAT(Clients.FirstName,' ',Clients.LastName) as ClientName, Clients.PhoneNumber
from Clients
--ORDER BY ClientName, C.PhoneNumber
create unique clustered index idx_ClientName on dbo.View5 (ClientName);

CREATE VIEW View6
as
select Specialist.SpecialistName, Activity.Date
from Specialist
JOIN Activity on Specialist.SpecialistID=Activity.SpecialistID
where MonTH(Activity.Date)=MonTH(GETDATE()) 
AND YEAR(Activity.Date)=YEAR(GETDATE());
--message_team_project.txt

--Sproc1: To select all assists with an open date falling in a user-defined time period. Include 
--input parameters for start date and end date of the user-defined period. return all fields. 3 
--points
create procedure Sproc1
@startDate date,
@endDate date
as
begin
select * from Assists
where DateOpened BETWEEN @startDate AND @endDate
end
--Sproc2: To return a list of clients and corresponding assists for a specialist identified in an 
--input parameter by specialist ID. Include client name, message phone, assist open and close 
--date, and assist type. 3 points
create procedure Sproc2
@specialistId int
as
begin
select c.FirstName, c.MessagePhone, a.DateOpened, a.DateClosed, a.TypeOfAssistance
from Clients c
JOIN Assists a on c.ClientID = a.ClientID
where a.SpecialistID = @SpecialistId
end
--Sproc3: To return a list of assists and tasks. Include input parameters for whether a task 
--needs follow-up, and the specialist associated with the assist (use specialist ID)
create procedure Sproc3
@needsFollowUp bit,
@specialistId int
as
begin
select a.AssistID, t.TaskId
from Assists a, Tasks t
where t.FollowUpNeeded = @needsFollowUp
AND a.specialistId = @specialistId
end
--Sproc4: To return a list of "new" clients for a year specified in an input parameter (refer to 
--the Application Specifications!). If there are no new clients set a return value of -1. 5 points
create procedure Sproc4
@year int
as
begin
declare @startDate date = cast(@year as varchar(4)) + '-01-01'
declare @endDate date = cast(@year as varchar(4)) + '-12-31'
select COUNT(distinct c.clientId) as 'Number of New Clients'
from Clients c
JOIN Assists a on c.ClientID = a.ClientID
where a.DateOpened BETWEEN @startDate AND @endDate
end
--Sproc5: To return a list of assists for a client. Include input parameters for first and last 
--names, and message phone. If more than one client is associated with the input parameters 
--return -1 without a list of assists
create procedure Sproc5
@firstName varchar(50),
@lastName varchar(50),
@messagePhone varchar(50)
as
begin
	select 
		COUNT(distinct c.ClientID) as 'Number of Clients'
			from Clients c
			JOIN Assists a on c.ClientID = a.ClientID
			where c.FirstName = @firstName
			AND c.LastName = @lastName
			AND c.MessagePhone = @messagePhone
	if @@ROWCOUNT <> 1
		begin
		return -1
		end
	select 
		a.AssistID, 
		a.ClientID,
		t.TaskId, 
		c.ClientID
			from Assists a
			JOIN Clients c on c.ClientId = a.ClientID
			JOIN Tasks t on t.AssistID = a.AssistID
			where c.FirstName = @firstName
			AND c.LastName = @lastName
			AND c.MessagePhone = @messagePhone
end
--Sproc6: To find the ID of a specialist. Use first name and last name to locate a specialist ID, 
--and return the ID as an OUTPUT parameter. If more than one or no specialist is found, set a 
--return value of -1, and set the OUTPUT parameter to 0
create procedure Sproc6
@firstName varchar(50),
@lastName varchar(50),
@specialistId int OUTPUT
as
begin
select COUNT(s.SpecialistID) as 'Number of Specialists'
from Specialists s
where s.FirstName = @firstName
AND s.LastName = @lastName
if @@ROWCOUNT = 0
begin
return -1
end
if @@ROWCOUNT > 1
begin
return -1
end
select s.SpecialistID
--INTO @specialistId
from Specialists s
where s.FirstName = @firstName
AND s.LastName = @lastName
SET @specialistId = @@IDENTITY
end
--spHW61: To add a new client. Include input parameters for all fields except ClientID. For 
--fields that do not require data, set the default value of each parameter to Null. Return the 
--ClientID as an output parameter. If the insert fails, use RaisError to send a message and 
--return -1.
create procedure sphw61
	@FirstName varchar(25) null,
	@MiddleName varchar(25) null,
	@LastName varchar(25) null,
	@Nickname varchar(25) null,
	@PhoneNumber varchar(10) null,
	@MessagePhone varchar(10) null,
	@StreetAddress varchar(50) null,
	@City varchar(50) null,
	@State varchar(2) null,
	@Zipcode varchar(5) null,
	@ACESNumber varchar(5) null,
	@Birthdate smalldatetime null,
	@SSN varchar(9) null,					
	@MedicareNumber varchar(9) null,
	@EmergencyContact varchar(200) null,  
	@GP varchar(25) null,
	@GP_PhoneNumber varchar(10) null,
	@Income money null,
	@ValueOfassets money null
as
begin try
	insert into Clients
	(
		FirstName,
		MiddleName,
		LastName,
		Nickname ,
		PhoneNumber,
		MessagePhone,
		StreetAddress,
		City,
		[State],
		Zipcode,
		ACESNumber,
		Birthdate,
		SSN,					
		MedicareNumber,
		EmergencyContact,  
		GP,
		GP_PhoneNumber,
		Income,
		ValueOfassets
	)
	values (
		@FirstName,
		@MiddleName,
		@LastName,
		@Nickname ,
		@PhoneNumber,
		@MessagePhone,
		@StreetAddress,
		@City,
		@State,
		@Zipcode,
		@ACESNumber,
		@Birthdate,
		@SSN,					
		@MedicareNumber,
		@EmergencyContact,  
		@GP,
		@GP_PhoneNumber,
		@Income,
		@ValueOfassets
	)
end try
begin catch 
	raiserror('insert failed', 16, -1)
end catch
--spHW62: To edit information about a client. Include parameters for all fields; make sure 
--that there is a valid 'where' clause to ensure that the correct record is changed. Evaluate the 
--input parameter values to determine if the new value or current value should be assigned 
--to each field (if the input parameter is null, do not assign to the field). If the client does not 
--exist, use RaisError to send an appropriate message.
create procedure sphw62
	@ClientID int,
	@FirstName varchar(25) null,
	@MiddleName varchar(25) null,
	@LastName varchar(25) null,
	@Nickname varchar(25) null,
	@PhoneNumber varchar(10) null,
	@MessagePhone varchar(10) null,
	@StreetAddress varchar(50) null,
	@City varchar(50) null,
	@State varchar(2) null,
	@Zipcode varchar(5) null,
	@ACESNumber varchar(5) null,
	@Birthdate smalldatetime null,
	@SSN varchar(9) null,					
	@MedicareNumber varchar(9) null,
	@EmergencyContact varchar(200) null,  
	@GP varchar(25) null,
	@GP_PhoneNumber varchar(10) null,
	@Income money null,
	@ValueOfassets money null
as
begin try
	IF EXISTS (
		SELECT FirstName, MiddleName, LastName
		FROM Clients
		Where ClientID = @ClientID)
			update Clients
			set FirstName = @FirstName,
				MiddleName = @MiddleName,
				LastName = @LastName,
				Nickname = @Nickname,
				PhoneNumber = @PhoneNumber,
				MessagePhone = @MessagePhone,
				StreetAddress = @StreetAddress,
				City = @City,
				[State] = @State,
				Zipcode = @Zipcode,
				ACESNumber = @ACESNumber,
				Birthdate = @Birthdate,
				SSN = @SSN,
				MedicareNumber = @MedicareNumber,
				EmergencyContact = @EmergencyContact,
				GP = @GP,
				GP_PhoneNumber = @GP_PhoneNumber,
				Income = @Income,
				ValueOfAssets = @ValueOfassets
			where ClientID = @ClientID
end try
begin catch 
	raiserror('update failed', 16, -1)
end catch
--spHW63: To search and update clients, sending in data for all fields through parameters 
--excepting the client id. Determine if a client already exists OR if a new entry is required 
--using first name, last name, and message phone. If the client exists in the database, get the 
--ClientID, and call the stored procedure to edit client information, passing values from the 
--original procedure; if the client does not exist, call the stored procedure to enter a new 
--record and pass in data from the original procedure. Return the ClientID as an output 
--parameter, whether the client record is new or edited.
create procedure sphw63
	@ClientID int OUTPUT,
	@FirstName varchar(25) null,
	@MiddleName varchar(25) null,
	@LastName varchar(25) null,
	@Nickname varchar(25) null,
	@PhoneNumber varchar(10) null,
	@MessagePhone varchar(10) null,
	@StreetAddress varchar(50) null,
	@City varchar(50) null,
	@State varchar(2) null,
	@Zipcode varchar(5) null,
	@ACESNumber varchar(5) null,
	@Birthdate smalldatetime null,
	@SSN varchar(9) null,					
	@MedicareNumber varchar(9) null,
	@EmergencyContact varchar(200) null,  
	@GP varchar(25) null,
	@GP_PhoneNumber varchar(10) null,
	@Income money null,
	@ValueOfassets money null
as
begin try
	IF EXISTS (
		SELECT 1
		FROM Clients
		Where FirstName = @FirstName
		AND LastName = @LastName
		AND MessagePhone = @MessagePhone) 
		SET @ClientID = (SELECT ClientID
			FROM Clients
			Where FirstName = @FirstName
			AND LastName = @LastName
			AND MessagePhone = @MessagePhone)
		exec sphw62 @ClientID, @FirstName, @MiddleName, @LastName, @Nickname, @PhoneNumber, @MessagePhone, @StreetAddress,
		@City,@State,@Zipcode,@ACESNumber,@Birthdate,@SSN,@MedicareNumber,@EmergencyContact,@GP,@GP_PhoneNumber,@Income,@ValueOfassets
		PRINT('Client Edited Successfully')

	exec sphw61 @FirstName, @MiddleName, @LastName, @Nickname, @PhoneNumber, @MessagePhone, @StreetAddress,
	@City,@State,@Zipcode,@ACESNumber,@Birthdate,@SSN,@MedicareNumber,@EmergencyContact,@GP,@GP_PhoneNumber,@Income,@ValueOfassets
	PRINT('Client Inserted Successfully')

end try
begin catch
	raiserror ('insert/eddit client failed', 16, -1)
end catch
--spHW64: To add a new assist. Include a test to ensure that a valid OpenDate and Client ID 
--are passed in: if the date parameter is in the future or the Client ID does not exist, do not 
--insert the record, use RaisError to send an appropriate message, and return a value instead.
create procedure sphw64
@ClientID int null,
@DateOpened smalldatetime null,
@DateClosed smalldatetime null,
@SpecialistID int null,
@TypeOfassistance varchar(250) null,
@RefferalSource varchar(50) null,
@RefPhone varchar(10) null,
@Confidential varchar(3) null
as
begin try
	IF 
	EXISTS (
	select 1 from Assists where ClientID = @ClientID
	) 
	AND (
	GETDATE() > @DateOpened)
		insert into Assists(ClientID, DateOpened, DateClosed, SpecialistID, 
		TypeOfassistance, RefferalSource, RefPhone, Confidential)
		values (@ClientID, @DateOpened,@DateClosed, @SpecialistID, @TypeOfassistance, @RefferalSource,
		@RefPhone, @Confidential)
end try
begin catch 
	raiserror('insert failed', 16, -1)
end catch
--spHW65: To edit an assist. Include parameters for all fields. Structure the stored procedure 
--as a transaction. Test to make sure that only a single record is changed by the update; if 
--more than one record is changed rollback the transaction and use RaisError to send an 
--appropriate message; otherwise commit the transaction.
create procedure sphw65
@AssistID int null,
@ClientID int null,
@DateOpened smalldatetime null,
@DateClosed smalldatetime null,
@SpecialistID int null,
@TypeOfassistance varchar(250) null,
@RefferalSource varchar(50) null,
@RefPhone varchar(10) null,
@Confidential varchar(3) null
as
begin transaction;
	IF 
	EXISTS (
	select 1 from Assists where AssistID = @AssistID
	) 
		update Assists 
		set ClientID = @ClientID,
		DateOpened = @DateOpened,
		DateClosed = @DateClosed,
		SpecialistID = @SpecialistID,
		TypeOfAssistance = @TypeOfassistance,
		RefferalSource = @RefferalSource,
		RefPhone = @RefPhone,
		Confidential = @Confidential
		where AssistID = @AssistID
		if (@@ROWCOUNT>1)
		begin
			raiserror('update failed', 16, -1)
			rollback;
		end
		else
			commit;

--When a Specialist is deleted, if there are related records in the Outreach or Assists tables, 
--raise an error and cancel the delete; otherwise delete the Specialist.

alter table Assists add SpecialistID int FOREIGN KEY REFERENCES Specialists (SpecialistID);

alter table Outreach add SpecialistID int FOREIGN KEY REFERENCES Specialists(SpecialistID)

CREATE TRIGGER SpecialistDeleteCheck
ON Specialist 
AFTER Delete 
AS 
BEGIN 
    DECLARE @AssistsReferences int
    DECLARE @OutreachReferences int
    DECLARE @DeletedSpecialistID int

    SELECT @DeletedSpecialistID = SpecialistId FROM deleted
    SELECT @AssistsReferences = COUNT(SpecialistID ) FROM Assists A WHERE A.SpecialistID  = @DeletedSpecialistID 
    SELECT @OutreachReferences = COUNT(SpecialistID ) FROM Outreach O WHERE O.SpecialistID = @DeletedSpecialistID 

    if @AssistsReferences > 0 OR @OutreachReferences  > 0
        return RAISERROR ('References to Specialist exist in Outreach or Assists Tables', 16, 10) 
END
--Create archive tables for Clients, Assists, and Tasks. Don't bother with primary keys or 
--constraints; just create tables that duplicate the field data types in the original tables 
--EXCEPT that identity fields should be number/no identity. 5 points

CREATE TABLE ClientsArchive(
ClientID int primary key  not null,
FirstName varchar(25) not null,
MiddleName varchar(25) null,
LastName varchar(25) not null,
Nickname varchar(25) null,
PhoneNumber varchar(10) null,
MessagePhone varchar(10) null,
StreetAddress varchar(50) null,
City varchar(50) null,
[State] varchar(2) null,
Zipcode varchar(5) null,
ACESNumber varchar(5) null,
Birthdate smalldatetime null,
SSN varchar(9) null,                    
MedicareNumber varchar(9) null,
EmergencyContact varchar(200) null,  
GP varchar(25) null,
GP_PhoneNumber varchar(10) null,
Income money null,
[ValueOfAssets] money null
);


create table AssistsArchive
(
AssistID int primary key  not null,
ClientID int FOREIGN KEY REFERENCES Clients(ClientID),
DateOpened smalldatetime not null,
DateClosed smalldatetime null,
SpecialistID int FOREIGN KEY REFERENCES Specialists(SpecialistID),
TypeOfAssistance varchar(250) null,
RefferalSource varchar(50) null,
RefPhone varchar(10) null,
Confidential varchar(3) null,
);


create table TasksArchive
(
TaskId int primary key  not null,
AssistID int FOREIGN KEY REFERENCES Assists(AssistID),
TaskDate smalldatetime not null,
FollowUpNeeded varchar(3) null,
Activity varchar(25) not null,
[Status] varchar(25) null
)
--• When a client is deleted, move the client record, related assists, and related tasks to the 
--archive tables; the original records should be deleted from the original Client, Assist, and 
--Task tables. 15 points

CREATE TRIGGER TRG_TASKS_Archive_Deletes 
on Tasks
after delete
as
begin
    INSERT INTO TasksArchive
        (TaskId, AssistID , TaskDate, FollowUpNeeded, Activity, [Status])
           SELECT deleted.TaskId, deleted.AssistID, deleted.TaskDate, deleted.FollowUpNeeded, deleted.Activity, deleted.[Status] FROM deleted
end
        
CREATE TRIGGER TRG_Assists_Archive_Deletes
on Assists
after delete 
as
begin 
    INSERT INTO AssistsArchive
        (AssistID, ClientID, DateOpened, DateClosed, SpecialistID, 
         TypeOfAssistance, RefferalSource, RefPhone, Confidential)
           SELECT deleted.AssistID, deleted.ClientID, deleted.DateOpened, 
        deleted.DateClosed, deleted.SpecialistID, deleted.TypeOfAssistance, deleted.RefferalSource, 
        deleted.RefPhone, deleted.Confidential
       FROM deleted
End
CREATE TRIGGER TRG_Clients_Archive_Deletes
on Clients
after delete
as
begin
    INSERT INTO ClientsArchive
        (ClientID, FirstName, MiddleName, LastName, Nickname, PhoneNumber, MessagePhone, StreetAddress,
          City, [State], Zipcode, ACESNumber, Birthdate, SSN,    MedicareNumber, EmergencyContact, GP,
           GP_PhoneNumber, Income, [ValueOfAssets])
           SELECT
           deleted.ClientID, deleted.FirstName, deleted.MiddleName, deleted.LastName, deleted.Nickname, 
           deleted.PhoneNumber, deleted.MessagePhone, deleted.StreetAddress,
          deleted.City, deleted.[State], deleted.Zipcode, deleted.ACESNumber, deleted.Birthdate, 
          deleted.SSN,    deleted.MedicareNumber, deleted.EmergencyContact, deleted.GP,
          deleted.GP_PhoneNumber, deleted.Income, deleted.[ValueOfAssets]
       FROM deleted 
end

