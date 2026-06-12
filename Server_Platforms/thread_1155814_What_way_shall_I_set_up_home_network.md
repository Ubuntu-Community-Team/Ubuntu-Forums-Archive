---
title: "What way shall I set up home network"
date: 2009-05-11
forum: Server Platforms
---

### Post by allyant on 2009-05-11
Hey,
I'm setting up a home server and I have two ways I can go:

1. Ubuntu server, serves as: LAMP, DNS, Proxy(safesquid) and one VMware(running Windows server 2003 for active directory etc) server.

or

2. Ubuntu server only VMware on it running two VM's:
   a) Ubuntu server for DNS, Proxy and LAMP
   b) Windows server for AD, print and NAP.

What one do you think is the best way to go?

Thanks :)

---

### Post by nquinnathome1 on 2009-05-11
Totally up to you; I would probably avoid anything where you add extra overhead though; running two virtual machines is extra work for the CPU, takes more disk space and needs more RAM. So I would suggest (1) as your best option.

---

### Post by justatemptest on 2009-05-11
So why Ubuntu? (can I ask that question here:). If you need active directory, why not just use Windows for everything?

---

### Post by allyant on 2009-05-12
> **justatemptest said:**
> So why Ubuntu? (can I ask that question here:). If you need active directory, why not just use Windows for everything?

I am unaware of any free proxy servers for windows.
And LAMP.

---

### Post by ephmanjmm on 2009-05-12
I would have asked "Why Windows and AD?" but I digress.

Apache MySQL and PHP are all available for windows.

Googled "free proxy servers for windows" and got this.
Proxy servers for windows:
[http://www.google.com/search?hl=en&q=free+proxy+servers+for+windows&btnG=Google+Search&aq=7&oq=](http://www.google.com/search?hl=en&q=free+proxy+servers+for+windows&btnG=Google+Search&aq=7&oq=)

---

### Post by allyant on 2009-05-12
So is your recommendation that I should just install windows?

The reason I am am thinking of using AD is because the amount of windows PC's I have, but if there is any linux alternatives...

---

### Post by ephmanjmm on 2009-05-12
How much experience do you have with AD and how many computers are you talking about for this home network?  AD seems like a lot of trouble for a small setup.  There are LDAP  systems available in the repositories I believe.  OpenLDAP info: [https://help.ubuntu.com/community/OpenLDAPServer](https://help.ubuntu.com/community/OpenLDAPServer)

---

### Post by TwiceOver on 2009-05-12
Just wanted to ask what you think AD is going to get you in a home environment.  I would assume most of your Windows PCs are of the "Home Edition" veriety, so there won't be any domain connections.  Without the domain you can't push updates or group policy.

Now maybe I'm wrong and you have Pro/Business edition Windows PCs.  If that is the case and your 2003 Server is legal and has enough CALs to support your home (man that must have been expensive), then by all means, go only Windows Server!  If I had Windows machines at home and the proper licensing, I would go that route.  WSUS, WSS and GPO make for such a nice environment.

---

### Post by allyant on 2009-05-12
I have 4 computers, 1 Windows XP pro, 2 Vista and 1 linux.
(All not mine obv).

I have spent 2 months as a network admin and set up a few AD networks for learning purposes at home in the past.

Using AD to share; setting, files, user accounts.

Using safesquid to block viruses and filter ads and porn.

---

### Post by bcdudley on 2009-05-12
I have setup both AD and Openldap for my home network in the past. To be honest, I learned more about AD by installing Openldap then I ever could have from running actual AD. I currently am running without any type of ldap at all and I have more computers than you do on my home network. 
 Until you get up around 10 computers, there really is no need for any type of domain authentication.

---

### Post by justatemptest on 2009-05-12
My experience with openldap (in a commercial environment though) tells me you should stay as far away from it as you possible can. It is a black-hole sucking in all IT-admins trying to get it to work. All the time spent on that costs *much* more than a Windows Server, which I personally trust more.

A year later, the main IT-admin-guy re-did it (again), saying the Red-Hat version is much better and all the previous work was terrible...

(For the record I'm a SW eng. This just what I saw around the office...)

---

### Post by allyant on 2009-05-13
Okay, I have decided just to set the server up with Windows Server and have A VM on it running Ubuntu server and have that serve as a proxy server.

---

