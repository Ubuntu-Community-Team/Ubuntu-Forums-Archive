---
title: "authentication and file server help please ..."
date: 2010-10-30
forum: Server Platforms
---

### Post by joepotter on 2010-10-30
A little help please.

I have a small very poor private school (pre-K to 8th grade) that has computers that are mostly 6+ years old. I have set up a Ubuntu server to handle Dan's Guardian for protection of the children. I need next to set up a centralized file server and some kind of authentication method.

We are dual booting the computers just now since we need to use "Rosetta Stone" language software and they will not release a certain plugin for Linux according to our assigned help person. We also use pure Windows XP in some classrooms for now, and will do so until the school's children gets used to Ubuntu.

So, what is the best authentication method for a mixed environment? Where might I find a Ubuntu "howto" on the method? 

What is the best way to set up a file server? Howto? Can the box running Dan's Guardian also be the authentication box and file server? (it is our newest box, only 2 years old and has a large hard drive)

---

### Post by Boondoklife on 2010-10-30
The authentication would really depend on your login requirements. If I were in your case I would simply have 3 accounts:

[LIST=1]
[*]Guest - For use by children and class room participants. This account should have no password and allow running of applications and minimal write privileges to the hard drive and none on the server.
[*]Faculty - For use by teachers and what not. This account would have a password and minimal write privileges to the hard drive and none on the server (save maybe a shared faculty drive).
[*]Admin - Total control on each system as well as the file server.
[/LIST]
If you are using XP which is just fine, you may want to get steady state which allows you to further lock down the system so changes do no last past a reboot. Now one caveat is rosetta stone and other application that will need to save data to the computer will need to have a writeable partition, thumbdrive, or network share (I would personally opt for the thumb drive). I personally think XP is a great platform for this type of setup as it allows for a easy system lockdown, Ubuntu can be locked down to but it is just easier with windows to be honest.

If you think you need more fine grain control over users, you could setup the file server to be a PDC and create logins for each student, faculty, and administrator. This does have its advantages but also requires more configuration. Samba will handle both your file sharing and PDC service.

As far as protecting the students, Dan's Guardian is just one of many applications that can do this, you could also setup the file server to be your dns using DNSmasq and use block lists from other services such as K9 and advertising killers. This will give you a VERY adaptable way of blocking content on your network.

---

### Post by joepotter on 2010-10-30
Thanks for your thoughts. I have read that Samba might be our best bet in a mixed environment if we want all students to have individual logins. I think that will be required at some point --- the decision made above my station.

If I am understanding this; I'll need to use NFS and Samba in combination to allow a student to log in from any computer with her individual name and password and be "in her environment". Correct?

---

### Post by Boondoklife on 2010-10-30
> **joepotter said:**
> Thanks for your thoughts. I have read that Samba might be our best bet in a mixed environment if we want all students to have individual logins. I think that will be required at some point --- the decision made above my station.

If I am understanding this; I'll need to use NFS and Samba in combination to allow a student to log in from any computer with her individual name and password and be "in her environment". Correct?

I guess that just depends on what you mean by "her environment", if you are just mapping drives to the computer and what not then you can just use samba by itself. It can handle files sharing and authentication all on it's own.

---

### Post by HermanAB on 2010-10-30
Howdy,

Here is a preconfigured VMware virtual machine with LDAP and wizards for it all:
[http://mds.mandriva.org/wiki/Download](http://mds.mandriva.org/wiki/Download)

---

