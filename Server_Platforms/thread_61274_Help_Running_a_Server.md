---
title: "Help Running a Server"
date: 2005-08-31
forum: Server Platforms
---

### Post by waynejkruse10 on 2005-08-31
Hello. I have been using Ubuntu Hoary for a while now on my secondary computer and i love it. Soon i will be setting up a forum based on Invision Power Board 1.3 on a Ubuntu Based server at school for all the students on the network to use.

I would say i am new to Linux so i may not know all the terms.

I know for what i need to do i need Apache Web Server, Mysql, and PHP. The first time i tried it it did not work. I was told it was because PHP doesnt have MYSQL support or something on the lines of that. I was told i would need to re-compile PHP with MYSQL support.

The second time i used a guide which told me to install specific Apache, several MYSQL and several PHP packages. I could get all of them via the Apt-get except the last one (which was called PHP4-MYSQL) which i got the .DEB file of Debians website. I installed the dependancies and installed it. This didnt fix the problem.

So, i was going to try to recompile PHP but i fould in Synaptic that a few of my packages were broken so i couldnt be bothered fixing it.

What i will do is wipe my screwed up copy of Ubuntu and start fresh. What i need help with is specific package names and versions i need to get so this will work and other information i need.

Remember i am quite new to Linux so you may need to dumb down your lingo  :???: 

Thanks in advance
Wayne

---

### Post by rmrf on 2005-08-31
I just issued this command in my sandbox and it worked fine: 

sudo apt-get install apache2 php4 php4-mysql mysql-server phpmyadmin

Normally it will grab all the dependencies that are needed, and will let me know of any recommended packages. I install phpmyadmin for a graphical interface to mysql through php.

Good luck on the install.

---

### Post by majikstreet on 2005-08-31
*grins*

See the UbuntuGuide ([www.ubuntuguide.org](www.ubuntuguide.org))

Install Apache, PHP, MySQL, then PHPMyAdmin from the guide.

majikstreet

---

