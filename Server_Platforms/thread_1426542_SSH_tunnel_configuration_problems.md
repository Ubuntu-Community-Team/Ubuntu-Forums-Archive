---
title: "SSH tunnel configuration problems"
date: 2010-03-10
forum: Server Platforms
---

### Post by Krijk on 2010-03-10
I'm trying to connect to a remote MySQL server over a SSH tunnel. I want to create a permanent tunnel. I created the tunnel (with key-authentication) using:

```
ssh -f -L 3307:localhost:3306 user@www.myserver.com -N
```

netstat -lpd says it is listening:
```
tcp        0      0 localhost:3307          *:*                     LISTEN      -     
```          

When I try to connect to MySQL (on the remote server) with a Python-script I keep getting connection errors.

```
OperationalError: (OperationalError) (1045, "Access denied for user 'dbuser'@'localhost' (using password: YES)") None None
```


The dbuser has 'dbuser'@'%' rights on the database and I can logon from the remote server. When I try connecting to a local database (on port 3306) the script works fine, so it is obviously an SSH tunnel configuration error. 

I've fiddled with it for some time, but I'm not getting anywhere. Any suggestions?

---

### Post by cdenley on 2010-03-10
That tunnel configuration looks correct. The error indicates the connection to the mysql server was successful. The username/password your script uses must not have permission for the database it is attempting to use.
```

nc -z -v 127.0.0.1 3307
mysql -v -h 127.0.0.1 -u dbuser -p -P 3307

```

---

### Post by Krijk on 2010-03-10
> **cdenley said:**
> That tunnel configuration looks correct. The error indicates the connection to the mysql server was successful. The username/password your script uses must not have permission for the database it is attempting to use.
```

nc -z -v 127.0.0.1 3307
mysql -v -h 127.0.0.1 -u dbuser -p -P 3307

```

No, the user has sufficient rights. I'm a bit further now (not that it helps). After changing localhost to 127.0.0.1 I don't get the permission-error anymore, but the script just freezes. 

I also tried "mysql -v -h 127.0.0.1 -u dbuser -p -P 3307" , but it doesn't respond either. 

:confused:

---

### Post by Krijk on 2010-03-10
> **cdenley said:**
> 
```

nc -z -v 127.0.0.1 3307
mysql -v -h 127.0.0.1 -u dbuser -p -P 3307

```


This did it for me. At least some more information:

```
ERROR 2013 (HY000): Lost connection to MySQL server at 'reading initial communication packet', system error: 0
```

---

### Post by Krijk on 2010-03-10
> **Krijk said:**
> 
```
ERROR 2013 (HY000): Lost connection to MySQL server at 'reading initial communication packet', system error: 0
```

Solved by modifying remote server:

hosts.allow
mysqld: ALL

---

