---
title: "Simple Q multiple apache users and remote administration"
date: 2011-02-07
forum: Server Platforms
---

### Post by Griff De La Griff on 2011-02-07
The questions is mainly about how one professionaly would solve the  security and administration for the multiple webadmins, but firstly I  give some general information.
I spent 2 days searching and there are alot of good guides but I dont see my specific questions answered, not so I can understand them atleast.

I have Ubuntu 10.10 64bit server edition installed.

I am educating myself and am new to linux but use vmware and have  installed Gentoo multiple times and a copy of Ubuntu server. This server  is going to be setup on the 64-bit 10.10 Ubuntu virtual machine.

What I want:
Simulate a server in a hosting company for 5 websites from different clients.

I understand I need to install the LAMP pack. I understand how I create users and virtual sites. My problems is:

1. Where is the best/securest place for the webfolders. I was thinking  home/site1 home/site2 etc because of the automatic right permissions on  theese folders but am unsure if its unwise or unprofessional in some way  to use the homedirectories.

2. solved. (how to upload files remotely) - I use ftp and give users access to only their directorys.

3. solved. (how to administer the databases for each client) - I use PHPMyAdmin.

4. Will PHP automatically work for all the virtual hosts, or do I need to configure some file for this.


Furthermore I wonder how 1 server would work in a real life scenario for  5 sites. Is it overkill, or isnt it good enough, i really dont know.  Should I place the SQL on a different server. The hardware should not  really be a problem since its cheap nowdays.

---

### Post by Griff De La Griff on 2011-02-08
Really, no one?

What about just question 1

---

### Post by wormyblackburny on 2011-02-08
Document root should always be /var/www if you are going for "professional" (in prod environment it should probably be mounted via NFS to a SAN). The other problem you have with using home folders is collaboration. If you want all of your "Admins" to have access to read/wirte/execute in the various web folders, create a group and add them all to the group then give that group access to /var/www. If you use their home folders you either have to give others access to the each others home directories (which wouldn't make me particularly happy) or you have no collaboration at all....

---

### Post by Griff De La Griff on 2011-02-09
The problem is that they are supposed to be 5 different admins for 5 different companies with each their own website. The server is is going to be offering webhosting for anyone interested so the different admins should not be able to see each others files and this is very important. This is why I thought homedirectories would be suitable.

---

