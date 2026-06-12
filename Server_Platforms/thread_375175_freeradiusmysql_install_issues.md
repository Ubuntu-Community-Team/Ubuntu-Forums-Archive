---
title: "freeradius/mysql install issues"
date: 2007-03-03
forum: Server Platforms
---

### Post by silverstriip on 2007-03-03
I have been trying to configure my 6.10 server for several days now with a few different versions of instructions on the web to get freeradius installed on my server.  Ultimately I want freeradius to talk to freeside to administer my mikrotik servers.  At this point I have some mysql issues.  I have installed the freeradius-mysql package on the server but keep running into a couple snags.  I'm not sure what all to post information wise, please let me know what else I can put in this thread to help out.  I'm currently receiving the following after importing my SQL file into the database and starting up the freeradius server:

 freeradius -x
Starting - reading configuration files ...
Using deprecated naslist file.  Support for this will go away soon.
Module: Loaded PAP
Module: Instantiated pap (pap)
Module: Loaded CHAP
Module: Instantiated chap (chap)
Module: Loaded MS-CHAP
Module: Instantiated mschap (mschap)
Module: Loaded SQL
rlm_sql (sql): Driver rlm_sql_mysql (module rlm_sql_mysql) loaded and linked
rlm_sql (sql): Attempting to connect to radius@10.0.1.247:/radius
rlm_sql (sql): starting 0
rlm_sql (sql): Attempting to connect rlm_sql_mysql #0
rlm_sql_mysql: Starting connect to MySQL server for #0
rlm_sql_mysql: Couldn't connect socket to MySQL server radius@10.0.1.247:radius
rlm_sql_mysql: Mysql error 'Can't connect to MySQL server on '10.0.1.247' (111)'
rlm_sql (sql): Failed to connect DB handle #0
rlm_sql (sql): starting 1
rlm_sql (sql): starting 2
rlm_sql (sql): starting 3
rlm_sql (sql): starting 4
rlm_sql (sql): Failed to connect to any SQL server.
Module: Instantiated sql (sql)
Module: Loaded Acct-Unique-Session-Id
rlm_acct_unique: Cannot find attribute 'User-Name' in dictionary
radiusd.conf[81]: acct_unique: Module instantiation failed.
radiusd.conf[128] Unknown module "acct_unique".
radiusd.conf[127] Failed to parse preacct section.


thanks for any assistance.

---

### Post by eric_stewart on 2007-03-03
> **silverstriip said:**
> I have been trying to configure my 6.10 server for several days now with a few different versions of instructions on the web to get freeradius installed on my server.  Ultimately I want freeradius to talk to freeside to administer my mikrotik servers.  At this point I have some mysql issues.  I have installed the freeradius-mysql package on the server but keep running into a couple snags.  I'm not sure what all to post information wise, please let me know what else I can put in this thread to help out.  I'm currently receiving the following after importing my SQL file into the database and starting up the freeradius server:

 freeradius -x
Starting - reading configuration files ...
Using deprecated naslist file.  Support for this will go away soon.
Module: Loaded PAP
Module: Instantiated pap (pap)
Module: Loaded CHAP
Module: Instantiated chap (chap)
Module: Loaded MS-CHAP
Module: Instantiated mschap (mschap)
Module: Loaded SQL
rlm_sql (sql): Driver rlm_sql_mysql (module rlm_sql_mysql) loaded and linked
rlm_sql (sql): Attempting to connect to radius@10.0.1.247:/radius
rlm_sql (sql): starting 0
rlm_sql (sql): Attempting to connect rlm_sql_mysql #0
rlm_sql_mysql: Starting connect to MySQL server for #0
rlm_sql_mysql: Couldn't connect socket to MySQL server radius@10.0.1.247:radius
rlm_sql_mysql: Mysql error 'Can't connect to MySQL server on '10.0.1.247' (111)'
rlm_sql (sql): Failed to connect DB handle #0
rlm_sql (sql): starting 1
rlm_sql (sql): starting 2
rlm_sql (sql): starting 3
rlm_sql (sql): starting 4
rlm_sql (sql): Failed to connect to any SQL server.
Module: Instantiated sql (sql)
Module: Loaded Acct-Unique-Session-Id
rlm_acct_unique: Cannot find attribute 'User-Name' in dictionary
radiusd.conf[81]: acct_unique: Module instantiation failed.
radiusd.conf[128] Unknown module "acct_unique".
radiusd.conf[127] Failed to parse preacct section.


thanks for any assistance.

Your MySQL implementation does not answer network queries except from local host by default.  If your radius server is not co-hosted on the same machine, you need to configure MySQL to listen on its standard network port (3309 ?).  I ran into a similar issue when setting up a Snort sensor to write to a remote MySQL database.  This should get you pointed in the right direction....I'm certainly not a MySQL expert.  

BTW, if your MySQL server *is* the same as your Radius server, I think you still have to set up the MySQL server to listen on the network.  You would have to setup Radius to read/write from IP address 127.0.0.1 but what I said in the 1st paragraph remains true.

Eric
[www.breezy.ca](www.breezy.ca)

---

### Post by silverstriip on 2007-03-09
Eric thank you for the help.  I have now gotten past that error.  I changed the literal IP of the sql server to local (127.0.0.1).  I'm unsure as to how to get sql to recognize my radius ID.  I confirmed that I have the user 'radius' entered into the 'user' table of the 'mysql' database.  Is this looking somewhere else for authentication?  I dont have any relevant tables under the 'radius' database.

freeradius -x
Starting - reading configuration files ...
Using deprecated naslist file.  Support for this will go away soon.
Module: Loaded PAP
Module: Instantiated pap (pap)
Module: Loaded CHAP
Module: Instantiated chap (chap)
Module: Loaded MS-CHAP
Module: Instantiated mschap (mschap)
Module: Loaded SQL
rlm_sql (sql): Driver rlm_sql_mysql (module rlm_sql_mysql) loaded and linked
rlm_sql (sql): Attempting to connect to radius@127.0.0.1:/radius
rlm_sql (sql): starting 0
rlm_sql (sql): Attempting to connect rlm_sql_mysql #0
rlm_sql_mysql: Starting connect to MySQL server for #0
rlm_sql_mysql: Couldn't connect socket to MySQL server radius@127.0.0.1:radius
rlm_sql_mysql: Mysql error 'Access denied for user 'radius'@'localhost' (using password: YES)'
rlm_sql (sql): Failed to connect DB handle #0
rlm_sql (sql): starting 1
rlm_sql (sql): starting 2
rlm_sql (sql): starting 3
rlm_sql (sql): starting 4
rlm_sql (sql): Failed to connect to any SQL server.
Module: Instantiated sql (sql)
Module: Loaded Acct-Unique-Session-Id
rlm_acct_unique: Cannot find attribute 'User-Name' in dictionary
radiusd.conf[81]: acct_unique: Module instantiation failed.
radiusd.conf[128] Unknown module "acct_unique".
radiusd.conf[127] Failed to parse preacct section.




my sql.conf file:
sql {
        driver = "rlm_sql_mysql"

        server = "127.0.0.1"
        login = "radius"
        password = "******"

        radius_db = "radius"

        acct_table1 = "radacct"
        acct_table2 = "radacct"

        postauth_table = "radpostauth"
        authcheck_table = "radcheck"
        authreply_table = "radreply"
        groupcheck_table = "radgroupcheck"
        groupreply_table = "radgroupreply"
        usergroup_table = "usergroup"

        deletestalesessions = yes

        sqltrace = no
        sqltracefile = ${logdir}/sqltrace.sql

        num_sql_socks = 5
        connect_failure_retry_delay = 60

        sql_user_name = "%{User-Name}"

        authorize_check_query = "SELECT id,UserName,Attribute,Value,op FROM ${authcheck_table} $
        authorize_reply_query = "SELECT id,UserName,Attribute,Value,op FROM ${authreply_table} $
        authorize_group_check_query = "SELECT ${groupcheck_table}.id,${groupcheck_table}.GroupN$
        authorize_group_reply_query = "SELECT ${groupreply_table}.id,${groupreply_table}.GroupN$

        accounting_onoff_query = "UPDATE ${acct_table1} SET AcctStopTime='%S', AcctSessionTime=$
        accounting_update_query = "UPDATE ${acct_table1} SET FramedIPAddress = '%{Framed-IP-Add$
        accounting_update_query_alt = "INSERT into ${acct_table1} (AcctSessionId, AcctUniqueId,$
        accounting_start_query = "INSERT into ${acct_table1} (AcctSessionId, AcctUniqueId, User$
        accounting_start_query_alt  = "UPDATE ${acct_table1} SET AcctStartTime = '%S', AcctStar$
        accounting_stop_query = "UPDATE ${acct_table2} SET AcctStopTime = '%S', AcctSessionTime$
        accounting_stop_query_alt = "INSERT into ${acct_table2} (AcctSessionId, AcctUniqueId, U$


        simul_verify_query = "SELECT RadAcctId, AcctSessionId, UserName, NASIPAddress, NASPortI$

        group_membership_query = "SELECT GroupName FROM ${usergroup_table} WHERE UserName='%{SQ$

        postauth_query = "INSERT into ${postauth_table} (id, user, pass, reply, date) values ('$
}

---

