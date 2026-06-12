---
title: "Which Mail Server"
date: 2007-09-30
forum: Server Platforms
---

### Post by tbrothers on 2007-09-30
I'm sure this question will get a lot of varying answers ... but what woild be a good mail server to install on a Ubuntu server?  I want a nice web interface with calendar and contacts.

I am a home user with a small business currently running aroung 15 mailboxes on an Exchange server ... Which I am replacing with a Ubuntu server, version 7.04.

Thanks,
Terry

---

### Post by jleiss on 2007-09-30
I would take a look at Zimbra ([www.zimbra.com](www.zimbra.com)) has a nice web interface like outlook really easy to manage, and does a real good job of filtering spam.

---

### Post by IcemanV9 on 2007-09-30
This is a [[COLOR="Orange"]good place[/COLOR]]("https://help.ubuntu.com/community/Servers?action=show&redirect=WebAndMailServers") to start with.

---

### Post by HermanAB on 2007-09-30
Nevermind the features, the only one that is easy to install and works with zero maintenance is Citadel: [http://www.citadel.org](http://www.citadel.org)

Installing Citadel takes about 20 minutes, while any other system typically takes about a week (unless you have done it many times before).

Cheers,

H.

---

### Post by gfowler on 2007-10-01
Salix provides and easy transistion for Exchange/Outlook users (it's the closest I have found).  Somewhere buried in the discussion forums (Scalix) is a bash script that will install and configure the basic Scalix system.   I have used it to install Scalix 11.1 on EE, it will require some minor modification to do so.  There is a Outlook connector that will let you using Outlook with Scalix that will give your users near the same look & feel of Outlook/Exchange.  DON'T use the fast synch or whatever they call it, alarms in the Cal won't work.

Scalix has just released a new version that may eliminate the problem, can't speak to that.  

You may find other recommendations found here of more utility for your situation.  If you elect to try the scalix and can not find the script, I can upload it here.

Jerry

---

