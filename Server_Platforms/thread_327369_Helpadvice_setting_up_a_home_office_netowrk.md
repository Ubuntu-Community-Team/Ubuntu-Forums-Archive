---
title: "Help/advice setting up a home office netowrk"
date: 2006-12-29
forum: Server Platforms
---

### Post by darclaird on 2006-12-29
Greetings,

Im in the middle of a running upgrade of my home office network (which also incorporates other machines I use about the house) and was after some advice/help on how to set things up most efficiently

Basically I have two desktop machines and a laptop all of which use  Edgy or Dapper as the main desktop and an xboxone of the desktops dual boots XP as I need it for some propitary software I use for work when wine just doesn't cut the mustard.

the centerpiece of the new setup is an old Hp Vectra I acquired of a family member, which I intend to push into use as a central fileserver hopefully running ubuntu server. what I would like is for this to be the machine which holds the /home directory for each of the users and a number of commonly used directories, which can be served to each machine irrespective of Windows or *nix based platform.

so far I have worked out I will need to use Samba for windows file sharing, NFS for Linux filesharing, where I hit a snag is, what I would like to occur is anytime I need to enter a new user on group all I need to do is add them to the server and this will propogate to the rest of the network... and what is the best way of going about this

All help/suggestions appreceated

Cheers

Justin (aka darclaird)

---

### Post by kidders on 2006-12-29
Hi there,

Since you need Windows compatibility, I think the best thing to do is set up a Samba domain, perhaps with LDAP. The downside is that it's also the most complicated thing to do. :-(

You would wind up with:

[LIST]
[*]A Windoze domain controller that works like something out of a corporate office.
[*]A centralised user/authentication database, exposed using LDAP, which is compatible with virtually everything (including address book apps, etc.).
[*]Centralised user profiles.
[/LIST]

The first time I did this with Linux, it took me several hours to get it right, but it's very cool. Hehe.

---

### Post by darclaird on 2006-12-29
Yeah, from the reading I have been doing that was where my thoughts were heading, though I can't seem to find any good howtos on LDAP out there (that explain how the setup/working of user authentication works alongside the filesharing)

Also, is NFS not neccesary if I am using LDAP?

Cheers

Justin

---

### Post by kidders on 2006-12-30
Hi there,

Yeah, I know what you mean about LDAP HOWTOs... there are lots and lots of them around, but they're all a little different, and never quite get you where you want to be!

> Also, is NFS not neccesary if I am using LDAP?NFS is a filesharing protocol ... LDAP is not.

Imo the best thing to do is run authentication for everything (Windows & Linux) off LDAP. The theory is...

[LIST=1]
[*]Set up an LDAP server on the machine that is to become your samba PDC.
[*]Test it out with something silly, like an email client ... see if it can connect, authenticate, and pull your users' contact addresses off it.
[*]Switch a Linux box to LDAP-based authentication & try to log in as a test user that exists only in the LDAP database.
[*]Duplicate all Linux boxes' user and group lists into LDAP.
[*]Reconfigure samba to use LDAP.
[*]Try to log into your new domain from Windows.
[/LIST]

A few extra things need a little tweaking, once you get this far, like centralising Linux's user profiles, but one thing at a time, eh? Hehe.

Try googling for something like "samba linux pdc howto" and see what happens. If you can't find what you need, I'd be happy to walk you through it.

---

### Post by DNeoMatrix on 2006-12-30
Hi, I have a Win 2k3 r2 server running as my domain controller, and i have about 5 windows xp clients...but i would really like to switch the clients to ubuntu rather than xp (run faster on the slower machines, more security from a end user perspective, less problems), but i want to keep my 2k3 machine as the central controller (need exchange server to sync with my phone). Should this be "plug-n-play"? I mean will it just work if I point the ubuntu machine to my server as the LDAP server?

---

### Post by jonathan.lees on 2006-12-30
Yes, it does work. I'm currently doing it with Fedora workstations by using samba and winbind with a couple of setting changes to the Server 2003 default domain policy. With Fedora it's fairly easy to achieve as it can be done with Fedora's network authentication tools.

Here's a [link]("http://www.fedoraforum.org/forum/showthread.php?t=92804&page=1&pp=15") to setting it up in Fedora, I know it's not Ubuntu but it should give you some idea. If someone has a good howto for Ubuntu, I'd appreciate it too.

thanks

---

### Post by DNeoMatrix on 2006-12-31
Thanks for the quick reply, but i was hoping for something a little more ubuntu specific - I'm still 50% newb to ubuntu and don't know my way around enough to translate from fedora. I'll be trying, but any help would be greatly appreciated.

If anyone has knows of any thin client linux distro - i.e. a distro which supports windows domains, internet, instant messaging and hardly anything else - i'd appreciate it. I'm looking for an easy way for the family to be able to log onto their windows accounts without the hassle of dealing with windows.

---

### Post by darclaird on 2007-01-03
*sheepish grin*

Turns out, just after posting my last reply, I tripped over my own feet running between my desktop and server, and broke a few bones in my right foot, which has knocked me out of working for a few weeks, so I have plenty of time to work on this and I will get back to you with howtos shortly

Cheers

--dl

---

### Post by enopepsoo on 2007-01-03
> **darclaird said:**
> *sheepish grin*

Turns out, just after posting my last reply, I tripped over my own feet running between my desktop and server, and broke a few bones in my right foot, which has knocked me out of working for a few weeks, so I have plenty of time to work on this and I will get back to you with howtos shortly

Cheers

--dl

are you totally serious? ](*,)

---

### Post by darclaird on 2007-01-06
Yes, Yes I am

However for those interested further scans yesterday revealed no actual fractures, just a lot of ligament/tendon bruising, so I am still off work for a while

---

### Post by Soarer on 2007-01-06
Glad to hear it :)

---

