---
title: "Lookinf for a DB add."
date: 2008-05-08
forum: The Cafe
---

### Post by jethro10 on 2008-05-08
Hi,
[EDIT : I meant a DB App. but can't edit the title!]
I have built a NAS / server for home and it's fine.
I want to put on a, preferably, php web based database front end, eg a VERY simple Microsoft Access type client I guess to make and store my own databases in probably a MySQL backend?
Now theres lots of CMS type packages that you drop into your web server, connect upto MySQL and your away (I use Joomla)
But can't find a generic Web based database GUI, or at a push a home/hobby "Collections" type database may do where folk record, lets say stamp collections, or coins, or movies they have seen.

Any ideas?
Jeff

---

### Post by jethro10 on 2008-07-02
Well apart from can't spell app!, I've finally found one or two solutions 
[http://www.tonymarston.co.uk/php-mysql/sample-application.html](http://www.tonymarston.co.uk/php-mysql/sample-application.html) (Click on online demo)

and
[http://www.radicore.org/](http://www.radicore.org/)

would both be ok, I might invest a little time on this.
Unless someone knows of something a little simpler?

---

### Post by rickyjones on 2008-07-02
I'm a little confused - are you looking for an application to help manage the SQL back end or are you looking for a simple application to store items in a DB - I could probably help you with both.

1. For managing SQL I highly recommend PHPMyAdmin.
2. If you are looking for a simple PHP/SQL site like "Enter information about your item and hit submit" then I (and many others) would be able to write something for you.

If you are looking for say, a tutorial, try searching for "PHP News Tutorial" - I used most of those results to teach myself basic PHP/SQL code.

I hope this helps!

Sincerely,
Richard

---

### Post by jethro10 on 2008-07-02
> **rickyjones said:**
> I'm a little confused - are you looking for an application to help manage the SQL back end or are you looking for a simple application to store items in a DB - I could probably help you with both.

1. For managing SQL I highly recommend PHPMyAdmin.
2. If you are looking for a simple PHP/SQL site like "Enter information about your item and hit submit" then I (and many others) would be able to write something for you.

If you are looking for say, a tutorial, try searching for "PHP News Tutorial" - I used most of those results to teach myself basic PHP/SQL code.

I hope this helps!

Sincerely,
Richard

Background. I program for a living in microsoft.net, using asp.net and use SQL server for the backend. So :-

1. already use it to backup my Joomla site etc, find it's great.
2. Nearly, not a site, I want a web based basic database editor for example to store and edit a wine collection and tasting notes etc. Would rather it was generic, cos I may then decide to store other types of data in it. or create a new set of table to store the other stuff in.

As far as PHP/Myslq goes, yes, i've decided to try an learn it as well, that's why I would like 2. above to be simple so I can use that to follow what it does and lear from it.
But basically my re-designed point 2 is what i'm after.
Can you follow these ramblings? It's always difficult to explain properly.....
Thanks
Jeff

---

### Post by rickyjones on 2008-07-02
> **jethro10 said:**
> Background. I program for a living in microsoft.net, using asp.net and use SQL server for the backend. So :-

1. already use it to backup my Joomla site etc, find it's great.
2. Nearly, not a site, I want a web based basic database editor for example to store and edit a wine collection and tasting notes etc. Would rather it was generic, cos I may then decide to store other types of data in it. or create a new set of table to store the other stuff in.

As far as PHP goes, yes, i've decided to try an learn it as well, that's why I would like 2. above to be simple so I can use that to follow what it does and lear from it.
But basically my re-designed point 2 is what i'm after.
Can you follow these ramblings? It's always difficult to explain properly.....
Thanks
Jeff

Kind of sounds like you want a very basic PHP site with an SQL backend with three fields: ID, Title, Text. ID is automatic for pulling records. Title is a short description of what you are storing (Wine Recipe: Blah Blah Blah). Text is the full text of what you are storing.

Am I getting closer here?

Thanks,
Richard

---

### Post by jethro10 on 2008-07-02
> **rickyjones said:**
> Kind of sounds like you want a very basic PHP site with an SQL backend with three fields: ID, Title, Text. ID is automatic for pulling records. Title is a short description of what you are storing (Wine Recipe: Blah Blah Blah). Text is the full text of what you are storing.

Am I getting closer here?

Thanks,
Richard
Basically, thats it.

I've just found this site [http://www.hotscripts.com](http://www.hotscripts.com) and it has loads of samples including this :- [http://www.dadabik.org/](http://www.dadabik.org/)
Which is more than enough, just installed it on my PC.
Why I never found something like it 2 months ago on my initial search I dunno.

Jeff

---

### Post by rickyjones on 2008-07-02
> **jethro10 said:**
> Basically, thats it.

I've just found this site [http://www.hotscripts.com](http://www.hotscripts.com) and it has loads of samples including this :- [http://www.dadabik.org/](http://www.dadabik.org/)
Which is more than enough, just installed it on my PC.
Why I never found something like it 2 months ago on my initial search I dunno.

Jeff

Excellent! I'm glad you found something. :)

---

