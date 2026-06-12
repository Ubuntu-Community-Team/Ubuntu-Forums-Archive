---
title: "Ubuntu panel - project"
date: 2011-07-12
forum: Server Platforms
---

### Post by capt.primetime on 2011-07-12
Hello everyone,
recently we decided to make our own panel (like Plesk or cPanel) but for Ubuntu and it will be licenced under GPL (like any other professional sofware). We need your help because we want to make a panel not only that fits our needs but also the needs of other system administrators and domain owners. We researched other panels and found out that non of them has security/look/ease of use in one package. Bad codig is another problem found in other panels.
I made a short overwiev of what I think we have to have in the beginning.  

I Security :
1. Completely chroot enviornoment where every single service is in chroot mode (bind, mysql, postfix, .... )
2. Easily managed IPtables trough web-based interface. 
3. Coding rules has to be strict.  

II Software selection :
1. MTA - Postfix
2. POP - dovecot
3. SQL - MysQL and PostgreSQL
4. DNS - BIND
5. WebServer - Apache
6. FTP - pureftp
7. PHP - 5


* Keep in mind that we will make panel software scalable, so we can easily add aditional funcionalities like supoprt for Sendmail, djbnds, lighttpd, proftpd, etc. This is just the selection of services we plan to implement first. 

III Ticketing system -- from scratch
IV  Hosting ordering system -- domain search and domain + hosting purchase
V   UI (admin/reseller/domain owner) should be organized in such way anyone can manage him/her - self.
VI  Documentation - is very important for any project. We want to document every single thing we did to make this panel work. This means that system admins will always know what is changed and where when they hit apply button in the panel. Same thing goes for resellers and domain owners. Also, we will document coding in the panel so anyone can jump in and add new feature. 
Im perfectly aware of the fact that every person is different and that there will be always some new feature to add. Also, I have never done any open source project before so I would need tips on that too. We hope to get feedback from forum members about what and how things should be handled, so if you talk about mail system , one should provide the info about what she/he misses in other panels, and what features are a must. 
This is going to be a big project and we will need all the help we can get to make this one right. Thank you in advance.

---

### Post by Lars Noodén on 2011-07-12
Rather than chroot, look at AppArmor. That can be used to lock down which files and directories a program is allowed to access.

---

### Post by capt.primetime on 2011-07-12
Can you please elaborate on why is it better to use AppArmor? Thanks in advance.

---

### Post by Lars Noodén on 2011-07-12
> **capt.primetime said:**
> Can you please elaborate on why is it better to use AppArmor? Thanks in advance.

For chroot, it is all or nothing access and it is necessary to create a duplicate of a subset of the system which may waste space and does require extra work to maintain.  

For [AppArmor](https://wiki.ubuntu.com/AppArmor), different applications have their own profiles and the profile states whether a file or directory is read, read-write or no access for that application.  The profiles can also make use of simple (globbing) pattern matching.  In some ways it is a little more complex to set up, but on the plus side, there is a lot more flexibility.  Supposedly for Oneiric, network ports will be among the options that can be restricted.  I don't yet find AppArmor as easy to work with as Systrace, but it is what Ubuntu has and so that's that.

---

### Post by Lars Noodén on 2011-07-12
You can use a ready-made ticketing system.  The choices include [Trac](http://trac.edgewall.org/), [RequestTracker](http://bestpractical.com/rt/) and [OTRS](http://otrs.org/).  There are more.

---

### Post by capt.primetime on 2011-07-12
Thank you for your reply Lars. When I did a research about hardening the system I was concerned about two things : 
1. If its going to be enough
2. If its going to be "simple" to implement and maintain
If you have only one domain on a server, you dont really need extra  panel to make it work, but if you plan to host many sites on the same  machine, then its crucial not to go too much into customization (or at  least not to make base system with too much radical changes). Chroot do  that, but many are very familiar how it works and many had alot of  experience maintaining such environments. 
AppArmor is something worth investigating, and if it fits the profile then I don't see the reason not to use it.

---

### Post by Lars Noodén on 2011-07-12
I'd recommend IMAPS over POP as it is mostly deprecated. IMAP(S) is a better protocol and also allows the users the choice of downloading the messages or leaving them on the server.

---

### Post by capt.primetime on 2011-07-12
> **Lars Noodén said:**
> You can use a ready-made ticketing system.  The choices include [Trac]("http://trac.edgewall.org/"), [RequestTracker]("http://bestpractical.com/rt/") and [OTRS]("http://otrs.org/").  There are more.

OTRS looks like a good project. I will have to set it up on a test server and see what it can do. Also I will have to tell our programmer to take a look at the code. One big drawback could be the fact it needs little bit more resources :( 
From OTRS website :
 > We recommend using a machine with at least a 2 GHz Xeon or comparable CPU, 2 GB RAM and a 160 GB hard drive. 


		> I'd recommend IMAPS over POP as it is mostly deprecated. IMAP(S) is a  better protocol and also allows the users the choice of downloading the  messages or leaving them on the server. 	
Yes, IMAP will have to be supported by default.

---

