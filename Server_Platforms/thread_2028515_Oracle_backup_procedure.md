---
title: "Oracle backup procedure"
date: 2012-07-18
forum: Server Platforms
---

### Post by druca on 2012-07-18
Hello,

I was wondering if it was possible to have a stored Oracle procedure that was triggered by time? I want to write one that would data pump a schema to a DR schema nightly. 

Is this possible? 


Thank you,

Drew Morrissey

---

### Post by druca on 2012-07-18
Also I don't mean a database trigger specifically. 

I mean more of a cron job sort of thing. I did not know if this was possible using stored procedures. It doens't look like it at the moment. I will post on this forum if I come across a solution.

---

### Post by LHammonds on 2012-07-19
I don't use Oracle on Linux so I don't know the specifics.
 
I would use the command-line utility called "sqlplus" that would allow a batch/script process to execute an SQL statement.  I would use that utility to execute a basic SQL command to execute the stored procedure.  Once I got it working, I would then schedule it via cron to run as often as you like.
 
[Running oracle commands directly from the command-line]("http://www.unix.com/unix-linux-applications/136095-running-oracle-commands-directly-command-line.html")
 
LHammonds

---

### Post by druca on 2012-07-20
Thank you LHammonds I appreciate your input. Does this script look ok? Of course I have removed any sensitive info with placeholders. 

I'm a little new to this so excuse any really dumb syntax errors or anything. I'm essentially trying to back up one schema to another using impdp and expdp across a database link. Not sure if this is possible but its what I dug up and hacked together yesterday. I will try it on a test server today. 

```

//Oracle Script export nightly on regular database

CREATE OR REPLACE DIRECTORY backdir AS /opt/Backup/ ;

GRANT READ, WRITE ON DIRECTORY backdir TO schema_user ; 

expdp  schema_user DIRECTORY=backdir DUMPFILE=schema_user.dmp SCHEMAS=schema_user ;

```
-------------------------------------------------------------------------------------------------------------------------------
```


//Oracle Script Import Script nightly on Disaster recovery dbase: 

create public database link mylink connect to schema_user identified by password using 'CONNECTIONSTRING' ;

impdp schema_user/password SCHEMAS=schema_user REMAP_SCHEMA=schema_user:DR_schema_user DIRECTORY=backdir 
NETWORK_LINK=mylink DUMPFILE=schema_user.dmp  EXCLUDE=CONSTRAINT, REF_CONSTRAINT, INDEX TABLE_EXISTS_ACTION=REPLACE ;

Drop datebase link mylink ;


```

---

### Post by LHammonds on 2012-07-20
I'm not that familiar with Oracle coding but those would be the commands you add to an SQL file and use a redirector to pump that command file into sqlplus.  Don't forget to define what "backdir" is in the import command file.

The setup would require knowing what user ID/group will be executing these commands and making sure the /opt/backup folder has the appropriate permissions to allow the creation of the export file.

You would then need to make sure the remote server has access (user rights / sharing rights) to the file/folder where the schema file was exported (or have a process copy/move the file to the remote server)

The remote server would then run the sqlplus command using the SQL command file to import the schema.

Check my sig for some of the bash scripts I wrote for MySQL which might be helpful in creating your scripts as well as scheduling them.

LHammonds

---

