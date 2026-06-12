---
title: "PHP form creator"
date: 2010-04-22
forum: The Cafe
---

### Post by hambone79 on 2010-04-22
I need help finding a piece of software. I'm looking for something (preferably web based) that will help me create custom forms to enter data into a MySQL database. I know a little bit of PHP and Perl, but I'm really pressed for time and don't have the time to write something from scratch.

Here are the basics of what I need (I'm setting up a problem reporting system for manufacturing):

1. Ability to login to the system and setup permissions for different users.
2. Ability to create custom forms with a simple interface and define how things will go into a database.
3. Some forms will require basic calculations to be performed.
4. Some forms will need the ability to attach pictures.
5. Need the ability to create simple reports.

---

### Post by ugm6hr on 2010-04-22
I have spent quite a lot of time looking for just such a piece of software.

I'm not sure it exists...

However, I have found VFront - which can:
1. Authenticate users / set permissions by 3 groups.
2. Create forms with a simple interface.
3. Attach files / images to DB entries.
4. Create simple reports (I think - although I haven't installed the reporting addon)

If you find something that does custom forms and custom links to other joined tables - let me know in my thread:
[http://ubuntuforums.org/showthread.php?t=1459531](http://ubuntuforums.org/showthread.php?t=1459531)

---

### Post by madjr on 2010-04-22
> **hambone79 said:**
> I need help finding a piece of software. I'm looking for something (preferably web based) that will help me create custom forms to enter data into a MySQL database. I know a little bit of PHP and Perl, but I'm really pressed for time and don't have the time to write something from scratch.

Here are the basics of what I need (I'm setting up a problem reporting system for manufacturing):

1. Ability to login to the system and setup permissions for different users.
2. Ability to create custom forms with a simple interface and define how things will go into a database.
3. Some forms will require basic calculations to be performed.
4. Some forms will need the ability to attach pictures.
5. Need the ability to create simple reports.

you can probably setup a cms like drupal to do all this.

it has enough plugins to do virtually anything

it's quick too

---

### Post by colaho on 2010-04-23
You need something like Bugzilla~~

---

### Post by hambone79 on 2010-04-23
> **colaho said:**
> You need something like Bugzilla~~

Actually I already thought of that. In fact, I have been using a modified version of Bugzilla for a problem reporting system for a few years and even wrote a howto about it [here]("http://www.hacksawlabs.com/index.php?option=com_content&view=article&id=56:using-bugzilla-for-manufacturing&catid=36:system-administration&Itemid=53"). Unfortunately, it has alot of limitations that can only be addressed by using a custom database.

I have also tried vFront, but it is still missing a few key features to be useful.

What I did find was a piece of software called [Glom]("http://www.glom.org/wiki/index.php?title=Glom"). It is sort of like Filemaker Pro with a MySQL database backend which is pretty much what I'm looking for.

---

### Post by ugm6hr on 2010-04-23
I've tried Glom before - I thought it was Postgres only.

It's not web-based either.

I'd be interested to hear how you find it fits your bill.

---

