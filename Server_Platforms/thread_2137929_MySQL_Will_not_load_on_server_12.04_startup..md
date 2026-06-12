---
title: "MySQL Will not load on server 12.04 startup."
date: 2013-04-22
forum: Server Platforms
---

### Post by smOBudda on 2013-04-22
Edit: I am running 12.10 sorry for the typo in the title.

Good morning, I wanted to take some time to see if I could get some advice as to why I'm having the problem I'm currently having pertaining to mysql not loading on the startup. A little background regarding the situation: I was installing freeswitch to my crashbox and I was able to get it installed with no issues, from that point I was trying to load the interface for FushionPBX during the install process for the FushionPBX it had asked me what type of database I would like to use for the install process. During that time I had opt for the default option according to the wiki I was using witch was just going to make a whole separate database for the system to run off. During that time it finished the install process, I went to access the user interface through the web browser and I was unable to access it though I showed the browser tab picture for FushionPBX. 

After I had tried to access my website to make sure that nothing was broken and noticed that I was unable to load any of the information attached to my website or /var/www/ dir. I then restarted my server thinking that I may just be a random issue that a reboot could fix. While running the system check before the load process was finished I noticed that mySQL failed to load. Since I've had this issue I have been unable to login to SSH or my FTP though I am able to access my server in safe mode and can confirm that all files attached to the directory's are still there thought none of the processes such as my ventrilo server, freeswitch, etc don't start. I had tried to view the log files found in /log/ dir but when trying to view them with nano in safe mode nothing shows. Any help or direction that you could provide me in terms of resolving this issue would mean the world to me. Thanks again ahead of time.

---

### Post by tgalati4 on 2013-04-22
Mysql log files are normally dumped to /var/log/mysql.  I would look through those and post anything useful.

I don't understand what "safe" mode is.  Is this a virtual machine running under Windows?  Or are you logging into "Recovery" mode which is just a root terminal with minimal services loaded?

If you are having other system issues, then you need to investigate /var/log/syslog and see what else is going on.

If apache fails to load (because it is independent of mysql) then there are other issues.  

Many times when installing a service (such as Fus(h)ionPBX) that requires a database (for example, mysql) you have to configure the database with an admin account and password as well as populate the fields of the database--initial schema or template.  If this was not done or done incorrectly, then your service won't run.

I'm guessing there is a simple typo during the install.

---

### Post by smOBudda on 2013-04-22
> **tgalati4 said:**
> Mysql log files are normally dumped to /var/log/mysql. I would look through those and post anything useful.

I don't understand what "safe" mode is. Is this a virtual machine running under Windows? Or are you logging into "Recovery" mode which is just a root terminal with minimal services loaded?

If you are having other system issues, then you need to investigate /var/log/syslog and see what else is going on.

If apache fails to load (because it is independent of mysql) then there are other issues. 

Many times when installing a service (such as Fus(h)ionPBX) that requires a database (for example, mysql) you have to configure the database with an admin account and password as well as populate the fields of the database--initial schema or template. If this was not done or done incorrectly, then your service won't run.

I'm guessing there is a simple typo during the install.


[B]I don't understand what "safe" mode is. Is this a virtual machine running under Windows? Or are you logging into "Recovery" mode which is just a root terminal with minimal services loaded?

[/B]-That is correct I am running the machine using the Recovery option on startup.

I will take the advice that you gave me when I get a chance to get out of my 9-5 for the day and view the logs listed in the dir's that you gave me in terms of locating a issue. Every service during the startup system check loads fine and shows as [*OK*] the only problem that I run into is with the MySQL with "FAILED" in red. I also wanted to ask would the issue that im having with my database have anything to do with not being able to logging in using SSH? Every time I tried to boot my server without recovery it was asking me for the username and password. The user has always been "root" and the password the one that I use. It will let me use root for the first login though any login there after will tell me that root is not a correct user. 

I think at this point it might be best to get out of work and view the direction you gave me thus far. What I really would like to know is if the mysql issue would be causing problems with my other services runing as well as not being able to connect to FTP or SSH. I would imagine not?

---

### Post by tgalati4 on 2013-04-22
I cannot think of a connection between failure of ssh and mysql not starting.  Ssh issues get logged to auth.log so check that first.  The default Ubuntu install does not have a root account, only *sudo* for running administrative actions.  I'm not familiar with your environment (freeswitch, fusionPBX) to know if that lack of a root account would be an issue.

The fact that it costs $1000 for a 3-day course on fusionPBX implies that it is not a trivial installation.

---

