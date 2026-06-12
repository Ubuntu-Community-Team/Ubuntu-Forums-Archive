---
title: "Telnet SSL Configuration"
date: 2010-02-17
forum: Server Platforms
---

### Post by Harshvir on 2010-02-17
I am new to ubuntu server. I tried to install telnetd-ssl server on that. The installation process says that its completed successfully. But i am not able to connect on port 992, while i am able to connect on port 23. I think there is some configuration that needs to be done, but i am not able to find what do i need to do for getting this to work.
 
**NOTE**: I have already seen this at many places, so please dont suggest me to use SSH or anything else. My Requirement is for TELNET SSL only.
 
Thanks.

---

### Post by noway2 on 2010-02-17
Step 1: determine if anything is listening on port 992.

```
sudo netstat -tap | grep 992
```
If nothing shows, this probably means you have a configuration error that is preventing it from starting.  Look in your log files, such as syslog or daemon log to see if anything shows.

If it does show that something is listening then you probably have a problem at the firewall end.  It could be a software firewall or a router.  You will need to make sure that port 992 is open to the outside world.

---

### Post by Harshvir on 2010-02-18
Thanks for the reply.
I checked the log files syslog and daemon.log. But i am not able to see any error related to telnet in that.
 
I was just curious about the load error like you mentioned.
When we install telnetd-ssl then it uninstalls the telnetd.
So incase telnetd-ssl is not getting loaded, then i should not be able to connect to port 23. But i am able to connect to Port 23. So i think i am missing something somewhere else.

---

### Post by Harshvir on 2010-02-19
[FONT=Times New Roman][FONT=Times New Roman][FONT=Times New Roman][FONT=Times New Roman][FONT=Times New Roman][FONT=Times New Roman][FONT=Times New Roman]There was some misunderstanding.[/FONT][/FONT][/FONT][/FONT][/FONT][/FONT][/FONT]
[FONT=Times New Roman][FONT=Times New Roman][FONT=Times New Roman][FONT=Times New Roman][FONT=Times New Roman][FONT=Times New Roman][FONT=Times New Roman]I was trying port 992, while it was running on port 23, which is highly unexpected. We need to specify parameters while running telnet, then it runs in ssl mode.[/FONT][/FONT][/FONT][/FONT][/FONT][/FONT][/FONT]
[FONT=Times New Roman][FONT=Times New Roman][FONT=Times New Roman][FONT=Times New Roman][FONT=Times New Roman][FONT=Times New Roman][FONT=Times New Roman]Now its working for me.[/FONT][/FONT][/FONT][/FONT][/FONT][/FONT][/FONT]

---

