---
title: "cannot get slave replication after master crash SQL"
date: 2010-04-24
forum: Server Platforms
---

### Post by skrite on 2010-04-24
Hey all, 
 
we had a hardware failure with our server and the server was re-started. Once up and running, i noticed that the slave was not replicating. 
show slave status gives me this. 
```
mysql> show slave status\G; 
*************************** 1. row *************************** 
               Slave_IO_State: 
                  Master_Host: **.**.**.** 
                  Master_User: muzr 
                  Master_Port: 3306 
                Connect_Retry: 60 
              Master_Log_File: mysql-bin.000283 
          Read_Master_Log_Pos: 106 
               Relay_Log_File: mysqld-relay-bin.000747 
                Relay_Log_Pos: 4 
        Relay_Master_Log_File: mysql-bin.000283 
             Slave_IO_Running: No 
            Slave_SQL_Running: Yes 
              Replicate_Do_DB: main_srvc_db 
          Replicate_Ignore_DB: 
           Replicate_Do_Table: 
       Replicate_Ignore_Table: 
      Replicate_Wild_Do_Table: 
  Replicate_Wild_Ignore_Table: 
                   Last_Errno: 0 
                   Last_Error: 
                 Skip_Counter: 1 
          Exec_Master_Log_Pos: 106 
              Relay_Log_Space: 106 
              Until_Condition: None 
               Until_Log_File: 
                Until_Log_Pos: 0 
           Master_SSL_Allowed: No 
           Master_SSL_CA_File: 
           Master_SSL_CA_Path: 
              Master_SSL_Cert: 
            Master_SSL_Cipher: 
               Master_SSL_Key: 
        Seconds_Behind_Master: NULL 
Master_SSL_Verify_Server_Cert: No 
                Last_IO_Errno: 0 
                Last_IO_Error: 
               Last_SQL_Errno: 0 
               Last_SQL_Error: 
1 row in set (0.00 sec) 
 
```
 
 
i think most weird to me is seconds_behind_master is null. What does that mean? 
Anyway, /var/log/mysql.err is empty 
 
any ideas?  
thanks

---

