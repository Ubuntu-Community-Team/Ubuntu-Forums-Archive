---
title: "Odd Behaviour, Lan Issues?"
date: 2009-03-29
forum: Server Platforms
---

### Post by SoronZero on 2009-03-29
Ok I have a weird situation that I just cant seem to figure out, maybe the linux gods here can help me out with it. 

Ok some machine backgound specs: 
-I'm running Ubuntu 64 8.04 Server with gnome installed
- AMD 3.4Ghz, 2GB ram, 160GB hard drive to be upgraded to 3-4 drive raid 5 later
-installed MySQL, PHP, Samba and will be primarily be used as a fileserver, possible internet access later.

What Works:
- MySQL, PHP and Samba ALL work on the LOCAL machine just fine
- I can ping the linux machine just fine no issues from my windows PC, and the linux machine can ping itself ok as well.
- My windows PC has no trouble connecting to other resources on my network (i.e. router, voip, etc)
- The linux machine does have internet access.

The Problem:
- From my windows machine I see the Samba machine on the network but I can't access the shares (no Username/PW prompt), I have tried both user and share level access with no go.
- I can't connect to the MySQL part of the machine from the windows machine.
- I have searched most websites and MySQL is configured for network access at ip address 0.0.0.0 instead of 127.0.0.1 and confirmed this with the netstat -apn | grep 3306
- I also confirmed that the Samba shares are listed and able to connect to them on the local side using smbclient.

I tried to disable IPchains/iptables and still no go, what am I missing here?

---

### Post by cariboo on 2009-03-29
> - I can't connect to the MySQL part of the machine from the windows machine.

You have to set up a mysql user that can access the database remotely. I generally create a second user when I setup mysql with the required permissions. Also make sure mysql is listening on port 3306.

This is how I set up my second user open the mysql console:

```
mysql -u root -p
```

then at the prompt type:

```
grant all privileges on *.* to <user>@'localhost'
identified by '<password>' with grant option;
grant all privileges on *.* to <user>@'%'
identified by '<password>' with grant option;
```

You should now be albe to remotely access mysql with the user you just created.

Jim

---

### Post by SoronZero on 2009-03-29
The permissions are set for the mysql users, I set them up for local and network access through mysqladmin, I just keep getting a ERROR 2003: Can't connect to MySQL server (10060) trying to connect from my windows machine and the port for both the server and the client are both set at 3306, I can connect with the local machine and run queries ok.

> 
grant all privileges on *.* to <user>@'localhost'
identified by '<password>' with grant option;
grant all privileges on *.* to <user>@'%'
identified by '<password>' with grant option;


I ran your query above on the linux machine, the windows pc still cant connect with the same error.

---

