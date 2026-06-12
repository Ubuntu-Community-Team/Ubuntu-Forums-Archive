---
title: "How to open server ports"
date: 2007-01-28
forum: Server Platforms
---

### Post by gmanigault on 2007-01-28
Okay here is my problem.  I am confused. 

1.  I loaded Ubuntu server 6.10 and it is up and runnning.  None of the ports are accessible.  I tried to use ssh and connection refused. 

     I did a ssh localhost and it was refused. 

2.  I checked the /etc/services file and none of the ports are commented out.  

3.  I don't know what to do to make the ports funtion.

Please help. Thanks.  

Gary M. 
GWShark

---

### Post by Engnome on 2007-01-28
Do you have open-ssh server installed?

---

### Post by gmanigault on 2007-01-28
I didn't load open-ssh.  When I try to run sudo aptitude install open-ssh .  It gets zero packages. I am still confused.

---

### Post by smdeep on 2007-01-28
Hi

Please install : sudo aptitude install openssh-server

sudo aptitude search openssh
i   openssh-client                              - Secure shell client, an rlogin/rsh/rcp replacement
i   openssh-server                              - Secure shell server, an rshd replacement

---

### Post by gmanigault on 2007-01-28
Thanks for the help.  How do I find out the name of packages as they are known by aptitude to fetch them?  Is there a list it works off of?

Gary

---

### Post by PetePete on 2007-01-29
in /etc/apt/sources.list
uncomment out the required ones...

---

### Post by smdeep on 2007-01-29
> **gmanigault said:**
> Thanks for the help.  How do I find out the name of packages as they are known by aptitude to fetch them?  Is there a list it works off of?

Gary

Hi
If you have a vague idea of the packagename it is easy to search with aptitude.

sudo aptitude search ssh 

should list you all packages which have either ssh in the package name or ssh in the description.

HTH

---

