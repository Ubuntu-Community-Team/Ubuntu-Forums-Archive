---
title: "Home/Family server suggestion"
date: 2007-05-18
forum: Server Platforms
---

### Post by Ventajou on 2007-05-18
I'm trying to define a list of apps to fulfill my home server needs. I was wondering what you guys use. Is there a better app for a particular job? Anything else I could add to the list?

The goal is to manage several XP clients belonging to my family members and offer them various web based services and apps. I'm aiming for single sign on as well.

Here we go:

Samba:
 - Domain Controller (user authentication)
 - File Server
 - Print Server

OCS Inventory
 - Inventory
 - Package deployment (I'm hoping to be able to push local policies through that)

Subversion with TortoiseSVN as client
 - Document management
 - Source control for my development projects

Zimbra or Horde Groupware
 - Email (incl. spamassassin and antivirus)
 - Calendar
 - Address Book
 - Todo lists

Gallery
 - Photo galleries

?
 - Book Library

?
 - Music Library (might just end up in a samba shared folder)

Of course I'd have Apache, MySQL and PHP at the very least for some web development.

Thanks!

---

### Post by kvonb on 2007-05-18
For "groupware", have a look at "egroupware".

It is available from the repos (simple synaptic installation) and it also has a stock control/accounting module as well!

More info here: [http://www.egroupware.org](http://www.egroupware.org)

I installed it yesterday, it was reasonably easy to get running as long as you know how to get a mail server up and running!

---

### Post by Macchi on 2007-06-12
> **kvonb said:**
> 
I installed it yesterday, it was reasonably easy to get running as long as you know how to get a mail server up and running!

Kvonb,
Have you tried to synchronize contacts, calendar, memo and tasks with Evolution? 

Ventajou,
Regarding the Small Office and Home Office server I have deployed a few solutions with SuSE and Ubuntu. My recommendation is to keep it simple so that the server remains reliable. Too many features will most probably compromise stability and will increase exponentially the administrative burden, I dare to say.
 
Another approach that I have adopted is to spread the functionality in different virtual machines in the same physical server. This provides has an substantial overhead but keeps the dependability at good levels.
 
I have experimented with a few open source groupware solutions but many of them have been either unstable or demanded too much time to deploy and maintain. Unfortunately I haven't had the time to work in this area but hope to see some good synergy happening between Ubuntu and groupware solutions.

---

