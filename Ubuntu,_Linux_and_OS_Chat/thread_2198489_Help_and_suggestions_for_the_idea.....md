---
title: "Help and suggestions for the idea...."
date: 2014-01-09
forum: Ubuntu, Linux and OS Chat
---

### Post by sadia21xx on 2014-01-09
Hi,
I am new here and getting to know the environment slowly.

I have a question, im doing a project in college about providing open source network solution for a school. I will using Ubuntu Server, So in this project im doing e-learning system that will be the moodle server but i want to have something as active Directory we have in windows..which will be make me able to integrate the moodle by using the credentials from active directory. I searched on internet it says of OpenLDAP, does this act as AD of Ubuntu? Im new to whole of this pls i need your suggestions. or is there something else we can have as the LDAP thru whch we can connect our moodle server to that domain for authenticating.

And the next thing is i need to provide open source solutions for the school, suggestions what will be suitable for a school and it open-source. LibreOffice i ave chosed for document application...what else application can be for a school open source that can be provided... The open-source is being used because of the licensing fees other OS requires and as  its a school they dont have huge budgets

More to this pls if u have suggestions and ideas do give.
Thanks alot
Regards

---

### Post by mastablasta on 2014-01-09
OpenLDAP is like AD and i think even compatible with AD.

inkscape and maybe gimp or lighter pci editor in case they need to create or edit a picture.

then it all depends on what they plan to or want to do on computers. is it computer science classes or what? i mena there are mathematics learning programmes, physics, then oyu have program langauges such as scratch, python etc.

---

### Post by lykwydchykyn on 2014-01-09
OpenLDAP is not equivalent to AD.
OpenLDAP is an LDAP server, which is basically a directory server in which you can store users, computers, etc.  
AD is a whole ecosystem of services built around LDAP.  It's got tools for pushing out printers, software, system policies, updates, etc.

OpenLDAP isn't going to have any of that by default.  You may find software that works with OpenLDAP to do some of these things, but it's not an all-in-one solution like AD.

If all you want is centralized authentication, then OpenLDAP can do this.  If you want centralized systems management, you want to look at something like Puppet.  If you want a "group policies" solution, that'll be desktop-environment-dependent.

EDIT:  I wrote a series of articles a while back on setting up a Linux desktop for a child; you may find some useful information in it.  Start here:

[http://www.alandmoore.com/blog/2013/01/07/building-a-linux-system-for-a-child-part-1-what-and-why/](http://www.alandmoore.com/blog/2013/01/07/building-a-linux-system-for-a-child-part-1-what-and-why/)

---

### Post by sadia21xx on 2014-01-10
thanks.

please more suggestions regarding open source softwares

---

### Post by sadia21xx on 2014-01-10
lykydchykyn, so if i have openLDAP can i integrate moodle with it and gets details for logging from this openLDAP....

---

