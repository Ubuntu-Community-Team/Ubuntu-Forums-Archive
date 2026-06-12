---
title: "Calendar server"
date: 2008-12-02
forum: Server Platforms
---

### Post by aehirst on 2008-12-02
I know this does not have much to do with ubuntu but I thought the smart people of the forums could help.

Im running ubuntu server with webdav to host ical calendars and sunbird as a client.

The problem is that on flakey VPN connections the ICS files seem to get corrupt. Does anyone know of an open source database based calendar server?

Thanks for any help

---

### Post by Masuran on 2008-12-02
Calendars en groupware servers in general are still a lacking feature on Open Source software. Your closest pick is Zimbra I think, a fully featured groupware server.

---

### Post by hyper_ch on 2008-12-02
I use now Horde (with IMP [webmail], Kronolith [calendar], nag [todo]). I can easily sync it all with my old SonyEricsson K800i.

---

### Post by batfastad on 2008-12-02
Take a look at Zimbra... so long as M$ decides to keep its hands off Yahoo!
It's a full groupware solution: calendar, email, tasks/notes, IM between users and a sweet AJAX remote interface.
There's an open-source version which does it all, but only for a single domain.
Then a paid-for version which includes some cool proprietory code for Activesync/Outlook sync, Blackberry, Apple isync, multiple domains and online incremental backups. And a few other gubbins.

I'm planning on migrating our Exchange Small Business Server 2003 over to Zimbra once v6 is released, April 2009 is the estimated date.
There's some big changes/upgrades/new features coming with v6.

HTH, B

---

### Post by quietas on 2008-12-02
Zimbra is a great groupware solution. I set it up at my company this summer using the paid Network Edition on Redhat. Also I run the OSS version on Ubuntu 8.04 as a backup and test server. Most of the functionality of the paid version is usable in the free OSS version, but no paid support and backups. One of the great things on Zimbra is the public sharing of the ICS file if you want to export to other devices. Also there is the Desktop client which saves all data locally on each machine. Outlook connectors are available via paid version, samme with Iphone/Palm/WindowsMobile connections.

Also there is webcal (sucks), or something like PHPGroupWare (also sucks). Clark Connect is another option.

---

### Post by aehirst on 2008-12-03
Thanks for the replys, I will take a look at Zimbra. I might code my own PHP/MYSQL based version however. Depends if I can find the time :p

---

### Post by hyper_ch on 2008-12-03
I strongly suggest to also have a look at Horde :)

---

### Post by aehirst on 2008-12-03
Thanks for the horde suggestion, however it looks a little out of my legue to install it

---

### Post by hyper_ch on 2008-12-03
it's not *that* complicated to install it. I intended to write a howto for a svn install of H3 this weekend...

Btw, here's a demo [https://ssl.lunabox.de/horde/login.php](https://ssl.lunabox.de/horde/login.php) (but it's slow).

I like that fact that it's all "components" and not a "all in one" solution. So by a svn install you would install the individual components (like mailserver, webserver, database server, php, ....) and on top of that you will add the horde things...

the zimbra install, however, is IMHO rather a blackbox into which I don't really see what's going on - that's one of my reasons to chose horde over it.

---

### Post by aehirst on 2008-12-03
I will have to another look at it. I think zimbra is a bit overkill for what I need. I do indeed like the modular components of horde.

---

