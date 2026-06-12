---
title: "Problem with mysql remote access on ubuntu"
date: 2008-12-07
forum: Server Platforms
---

### Post by abhinav90 on 2008-12-07
i am trying to remotely connect to my mysql server on my ubuntu hardy machine using java jdbc for a widget that i have developed. After long hours i was successfully able to make the mysql server remotely accessible over the default 3306 port. telnet myserverIP 3306 connects successfully, However, when i run my java widget to connect the widget shows running in netbeans but nothing at all opens up. I left it for 20 minutes but nothing happened. The GUI also did not open up in the screen so i am unable to even track the error. it just keeps coming as running. I have tried the jdbc with another managed host and have successfully remotely connected to the US from India. but with my own server it is not working. i have not setup any firewalls nor iptables and even added a user with all priveleges to the mysql table. Dont know what to do?

Any Help would be really appreciated. Thanks in Advance

---

### Post by koenn on 2008-12-07
that could be anything between a configuration error on your server, any sort of network problems, a database privileges issue,  or a problem with your jdbc connection settings, such as a charset mismatch between the mysql databases and the client program.

You could blindly try to diagnose and fix any of those, or you could learn to trap errors and display them on screen, and possibly add some debug output to your program. 
I'm not a programmer, but for the latter option, probably people at the programming forum can help.

---

### Post by cariboo on 2008-12-07
Can you connect to mysql remotely from the terminal?

```
mysql -h <server> -u <user> -p
```

If you can connect remotely via the terminal, then it isn't a configuration problem with mysql.

Jim

---

### Post by abhinav90 on 2008-12-08
the thing is that when i try to connect to mysql that way it prompts me for the password then it just keeps waiting, i waited for 20 minutes and all that could be seen was the blinking cursor. I think the same sort of stall is happening to the java app when it is trying to connect to mysql. What could be the possible solution to this??

---

### Post by cariboo on 2008-12-08
It sounds like you have a misconfiguration. I have attached a copy of my /etc/mysql/my.cnf.

Compare it with yours and see if there are any differences.

Jim

---

### Post by fatbastard spice on 2008-12-08
Getting the same behaviour myself (hangs without response after entering password if i try to connect remotely). Login works fine for no host specified.

I know this was working last night as i just enabled remote connections to mysql to start setting up a mythtv frontend on another machine.

I did notice that the updates i applied recently had a bunch of bind & other dns related changes. Wonder if they're involved?

Also looked at your config file cariboo907 - main difference for me is that i've commented out the bind address to allow remote connections from other machines.

I've also got another config file in /etc/mysql/conf.d/ that changes a few things, though that mainly looks like performance based stuff for mythtv (table_cache, sort_buffer_size, net_buffer_length, query_cache_type, query_cache_size & binlog_ignore_db).

---

### Post by abhinav90 on 2008-12-09
i checked the files they are almost identical. Only difference is that i have made my bind address equal to my external ip of my server to allow remote connection. Any other solutions in mind ???

---

### Post by cariboo on 2008-12-09
Have you got your user setup to allow remote logins?

```
 show grants;
+--------------------------------------------------------------------------------------------------------------------------------+
| Grants for jim@%                                                                                                              |
+--------------------------------------------------------------------------------------------------------------------------------+
| GRANT ALL PRIVILEGES ON *.* TO 'jim'@'%' IDENTIFIED BY PASSWORD '*1B4D0819C228ECCDD08697E118FA4B80437A7D6D' WITH GRANT OPTION | 
+--------------------------------------------------------------------------------------------------------------------------------+
1 row in set (0.00 sec)
```

If privileges are not set up correctly, you may not be able to connect remotely

Jim

---

### Post by koenn on 2008-12-09
> **abhinav90 said:**
> i checked the files they are almost identical. Only difference is that i have made my bind address equal to my external ip of my server to allow remote connection. 

Is this server behind a NAT router so that its IP address when seen from the LAN is different( private) from the one seen from the WAN (public) ?

If so, if you try to connect by hostname, you may be connecting to an address that your mysqld is not listening on (depends on how you handle DNS on the LAN)


Even if you connect to the correct address, i.e. the public address, your NAT router might refuse or be unable to handle connections to its WAN interface that are in fact coming from the LAN. 

You can narrow this down by having mysqld bind to the private address (+ connect by IP address or fix DNS accordingly)  and see if that works.

---

### Post by abhinav90 on 2008-12-11
i found a reason why mysql-server on ubuntu stalls my connection. When i try to remotely try to connect to my server using mysql -u on my desktop after requesting password it keeps waiting forever,

When i checked out my server and typed netstat -tap | grep mysql  i first get:

(No info could be read for "-p": geteuid()=1000 but you should be root.)
tcp        0      0 173-45-231-96.sli:mysql *:*                     LISTEN      -               
tcp        0      0 173-45-231-96.sli:mysql 59.183.1.24:50296       ESTABLISHED

but then it becomes

(No info could be read for "-p": geteuid()=1000 but you should be root.)
tcp        0      0 173-45-231-96.sli:mysql *:*                     LISTEN      -               
tcp        0     66 173-45-231-96.sli:mysql 59.183.1.24:50046       FIN_WAIT1   -               

i think the FIN_WAIT1 is the problem but dont know how to fix this socket problem. What should i do? ? Any input would be appreciated.

---

### Post by abhinav90 on 2008-12-29
bump

---

