---
title: "vsftpd does not start"
date: 2016-07-22
forum: Server Platforms
---

### Post by edwinx on 2016-07-22
Hi,

I installed vsftpd and I cannot get it to start.  

```
udo service vsftpd start
vsftpd start/pre-start, process 19909
```

seems to work but when I run nmap, it is not showing up as listening on any ports
Also,  when I take a look at 

```
/var/log/vsftpd.log
```

I don't see any entries of errors and such. only failed connection requests from earlier attempts.  so I guess it has started at 1 point.  

Any tips how I can troubleshoot this further?  I just want FTP for internal use and I (admin) will be the one using it.

Thanks,
edwinx

---

### Post by thomaschr on 2016-07-25
You can use 'netstat -tulpen' to check if vsftpd is Listening, no need for nmap :-)
I had the same problems because of an error in the config file.

Just try to start vsftpd manually (by typing 'vsftpd') and see ih it refuses to start. It will tell you why!

Thomas

---

### Post by edwinx on 2016-07-27
> **thomaschr said:**
> You can use 'netstat -tulpen' to check if vsftpd is Listening, no need for nmap :-)
I had the same problems because of an error in the config file.

Just try to start vsftpd manually (by typing 'vsftpd') and see ih it refuses to start. It will tell you why!

Thomas


Thomas, thanks!
what work, there was an error in my userList_deny, so I just commented it out

Would you know how would I check which users are able to log in? I currently log into the console/ssh as "admin".  I want to be able to use the same login as well. 

Thanks,
 [CENTER][COLOR=#FFFFFF][FONT=Helvetica Neue]**Save**[/FONT][/COLOR][COLOR=#FFFFFF][FONT=Helvetica Neue]**Save**[/FONT][/COLOR][/CENTER]

---

### Post by thomaschr on 2016-07-29
With a standard installation everyone which has a passwort (in /etc/shadow) and a Shell (in /etc/passwd) is able to log in.
vsftpd checks a few more things (is his home directory writeable...) but those are the main ones!

Thomas

---

