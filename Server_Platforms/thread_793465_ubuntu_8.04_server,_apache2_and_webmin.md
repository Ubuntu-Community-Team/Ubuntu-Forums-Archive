---
title: "ubuntu 8.04 server, apache2 and webmin"
date: 2008-05-13
forum: Server Platforms
---

### Post by badman35 on 2008-05-13
i have setup ubuntu server 8.04 lts last night and i also installed webmin 1.410. the problem is that the apache sever is running and webmin says it is not. when i click the "start apache" link it says that there is an error. so can somone out there tell me just what is going on?????!!!!!

oh when i installed ubuntu server i installed everything when it asked for what i wanted to in stall....

---

### Post by windependence on 2008-05-14
> **badman35 said:**
> i have setup ubuntu server 8.04 lts last night and i also installed webmin 1.410. the problem is that the apache sever is running and webmin says it is not. when i click the "start apache" link it says that there is an error. so can somone out there tell me just what is going on?????!!!!!

oh when i installed ubuntu server i installed everything when it asked for what i wanted to in stall....

Do you think maybe you could post the error? This is not much to go on.

-Tim

---

### Post by d2allgr on 2008-05-14
Had the same problem and fixed it as follows:
in /etc/apache2/apache2.conf I changed
PidFile ${APACHE_PID_FILE} to PidFile /var/run/apache2/apache2.pid ,
User ${APACHE_RUN_USER} to User www-data and
Group ${APACHE_RUN_GROUP} to Group www-data .
After that I set the pid location in the module configuration for apache2 in webmin and did an apache2 restart from shell. Worked fine since then.

---

### Post by badman35 on 2008-05-16
ok here is the error that i get
Module Index
	Error 	
Failed to start apache : Apache does not appear to be running :

httpd (pid 4698) already running

<-  Return to previous page


Ok now can sombody tell me what i need to do to get it to work????

---

### Post by firebottle on 2008-06-02
> **badman35 said:**
> Ok now can sombody tell me what i need to do to get it to work????
1. When you enter the apache module in webmin, click 'module config' at the upper left of the page.

2. Scroll down to the 'System configuration' section, and find the setting for 'Path to Apache PID file.'

3.  Enter '/var/run/apache2.pid' and hit the 'save' button.


If someone else has a better solution, I'm all ears. :evil:

---

### Post by firebottle on 2008-06-02
> **d2allgr said:**
> After that I set the pid location in the module configuration for apache2 in webmin
I'm pretty sure that's all you really needed to do.[-X

---

### Post by motin on 2010-07-11
Thanks a bunch!
One of my servers had this issue and it just got annoying after some time. Adjusting the path to pid file in apache2.conf and setting it in webmin apache module system configuration did it.

---

