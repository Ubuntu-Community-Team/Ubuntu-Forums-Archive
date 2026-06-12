---
title: "LAMP question:"
date: 2014-09-30
forum: Server Platforms
---

### Post by Priest Apostate on 2014-09-30
(Sorry in advance, but I don't know to which forum to take this question.)

Right now, I am attempting to learn more about setting up LAMP systems. I am currently reading Sams' Teach yourself PHP, MySQL, and Apache. The book mentions that MySQL shouldn't be run as root (which I understand is a security 'no-no'), but I am confused: why do I need to direct the ISP to stop running MySQL as root - how do they (the ISP) figure into me running the program as root? 

Did I overlook something?

---

### Post by Elfy on 2014-10-01
*Thread moved to **Server Platforms**.*

---

### Post by Lars Noodén on 2014-10-01
The short version is that MySQL does not need to be root since its default listening port is 3306.  Above 1024, ports do not need root level access for listening.  So following the principle of least privilege, it gets another user and should be anything other than root.   Though it could have been any user already in use,  following the idea of privilege separation it gets its own user, 'mysql' on Ubuntu.

---

### Post by Vegan on 2014-10-01
out of the box LAMP works fine, no need for any special privileges

the MySQL backup tool does need elevation only because it makes a full copy of the MySQL server

---

### Post by Priest Apostate on 2014-10-01
I forgot to have mentioned: this is off of my own home server (as opposed to a remotely assigned server).

---

### Post by Doug S on 2014-10-01
> **Priest Apostate said:**
> I forgot to have mentioned: this is off of my own home server (as opposed to a remotely assigned server).O.K.> **Priest Apostate said:**
> but I am confused: why do I need to direct the ISP to stop running MySQL  as rootYou don't.> **Priest Apostate said:**
> - how do they (the ISP) figure into me running the program as  root?They don't.

---

### Post by Priest Apostate on 2014-10-01
Gotcha - thanks!

---

