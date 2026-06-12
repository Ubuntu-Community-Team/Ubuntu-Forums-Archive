---
title: "System Logs"
date: 2005-08-01
forum: Server Platforms
---

### Post by theQmaster on 2005-08-01
How/Where do I see the system logs.

I have this particular problem when I have a process that runs just fine as a low priviledge user but it doesn't complete as root.

Very interesting. To me looks like it's an access problem but how do I figure it out?
Is there any place/file that tells me how/when a process hanged or fired an error ?

Thanks,
theQmaster

---

### Post by dave9191 on 2005-08-01
You can find all sorts of logs in the /var/logs dir. And there are some programs that will refuse to run as root as it can be a security problem. 

Dave

---

### Post by theQmaster on 2005-08-01
The program I'm meant to run was JSVC that is making Tomcat run on 8080 as daemon. Intersting is that the socket on 8080 is created but the server is support to create another socket at 8009 and that is not created.

Anyone experienced something like that ?
Q

---

### Post by dave9191 on 2005-08-01
You should not run a web server as root. There is a  dedicated user for running that. And if running that works from your account then leave it at that. 

Dave

---

### Post by LordHunter317 on 2005-08-02
[QUOTE=theQmaster]The program I'm meant to run was JSVC that is making Tomcat run on 8080 as daemon. Intersting is that the socket on 8080 is created but the server is support to create another socket at 8009 and that is not created.[/quote]Check your tomcat configuration.  You may have the AJP connector disabled.

---

