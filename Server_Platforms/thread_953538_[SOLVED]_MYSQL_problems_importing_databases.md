---
title: "[SOLVED] MYSQL problems importing databases"
date: 2008-10-20
forum: Server Platforms
---

### Post by bronkeydain on 2008-10-20
Hello People,

I have a HUGE problem. I am using this webbased php/mysql CRM system called vTiger CRM 5.0.4. My server runs Ubuntu Gutsy Server 7.10
My server HD crashed the other day. I made daily tar backups of the entire / partition and mysqldump backups of my databases, all to an external drive every night. 

I have rebuild my server, for some reason my tar archives seem corrupted on the external drive (EEK!), it gives me I/O error when I try to access. The mysqldumps are readable. However I have problems importing them.

- First I drop & then create database vtigercrm504 to get an empty database.
- Then I type: mysql -u root -p vtigercrm504 < vtigercrm504.09.10.2008.sqlbackup 
> When I enter the SQL password, then I get this error: 
ERROR 1136 (21S01) at line 1323: Column count doesn't match value count at row 9 

The thing is that I get the same kind of error for my eGroupware MYSQL database. I have already posted this on vTigers forums, but they are rather slow there and sometimes don't answer at all. I have already wasted a lot of time trying to fix this and it is getting really critical. 

I was using vTiger for managing my entire business and now my client data, billing info, debtors list, helpdesk trouble tickets.... everything gone! I thought I was safe with my daily backups and now I am in a terrible mess here. It nearly makes you consider buying an old G4 mac and slap leopard server on with time machine....

Help? Anyone?

---

### Post by bronkeydain on 2008-10-20
This is my MYSQL server version:

Server version: 5.0.45-Debian_1ubuntu3.3-log Debian etch distribution

---

### Post by indytim on 2008-10-20
> 
ERROR 1136 (21S01) at line 1323: Column count doesn't match value count at row 9 


What this error message is telling you is that at line 1136 of your load file, you have a mismatch between either:

the declared fields and the values 

or

the load file contains more fields than the structure of the table.  Looks like it passed through the previous 1322 records ok.  Suggest you open the load file and go to line 1323 to check specifics.  If it's just this one record, you might be able to make some repairs and continue the load.  If it's more prevelant, then you're probably faced with either writting a patcher to fix the .sql load file of manually editing the load files (not a lot of fun).

Hope this provides a glimmer of assistance.

Good Luck,

IndyTim

---

### Post by bronkeydain on 2008-10-20
Thanks indytim.

I will try your suggestions, who knows. But I wonder if there is no way then to force mysql to ignore these mismatches.

Also I wonder if my current mysql server has a different version from the one I was using before. I was reading about people having similar problems with version 5.0.45. Some people have fixed this error by deleting all databases and reinstalling mysql. I have tried this but no joy.

---

### Post by bronkeydain on 2008-10-20
I have tried what you said, I opened the dumpfile in a text editor & jumped to line 1323.
Line 1323 tries to insert contact information into the database. It is the last line in the file. I have removed this line and the database imported without errors. However my application won't run complaining about missing tables etc. 

I get the impression that the sqldump has been cut off half way. Looking at the tables in the database the table names all start with a, b or c. 
 ](*,)

---

### Post by indytim on 2008-10-20
Are you getting any code dumps on which tables are missing?  From what you say, it seems to make sense.  If you can tie down the specific table that is missing, you might be able to do a partial restore from a previous backup.

I seriously doubt that you are experiencing these type of problems as a function of a version advancement in MySQL (I reserve the right to be wrong however... :) ).

IndyTim

---

### Post by bronkeydain on 2008-10-23
Sorry for the late reply, been real busy.

I have fixed my problem from a different angle. 
The crashed server HD actually had a corrupted file table, and after having fixed that using testdisk  and fsck I can now read my original data again, my backup is still screwed :)

Thanks for your help

---

