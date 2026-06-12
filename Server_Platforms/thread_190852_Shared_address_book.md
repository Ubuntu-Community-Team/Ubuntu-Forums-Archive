---
title: "Shared address book"
date: 2006-06-06
forum: Server Platforms
---

### Post by fizgig on 2006-06-06
So I've been looking all over for a tutorial to set up a simple ldap server to host a shared address book.  My boss is threatening to buy MS exchange just so he can get that functionality but I keep telling him to give me more time to try out openldap.  (I'm not an IT guy, I'm a mechanical engineer but I've managed to solve all IT problems so far with Ubuntu)

I've got breezy server installed and it's doing well as an vpn, file and print server.  They all installed easily and there's plenty of documentation to work with.

With Ldap, it's different.  I've tried a few different tutorials I've found on the web.  Most get me some of the way there but fail for reasons I don't understand.  Even the [Ubuntu wiki]("https://wiki.ubuntu.com/OpenLDAPServer?highlight=%28ldap%29") fails for me at the point where I should be able to enter the ldif file (can't parse line 5).  The rest of the ubuntu wiki's deal with logins which I don't care about.

The basic point here is that, for some reason, all the tutorials that I find don't seem to work with Breezy.

Has anybody made a shared address book with Ubuntu server?  If so, would you be up for making a tutorial for the rest of us that is customized for ubuntu?  Sure would be nice.

---

### Post by shreko on 2006-06-06
Sorry, I can't help you with LDAP address book, I just wanna add myself to the list of people interested in this solution. I am just like you, mechanical engineer who enjoys dealing with computers in business. My boss is not threatening with MS Exchange yet, but some sales guys mentioned shared address book, so it would be nice if I surprise them and make OSS solution. 
Hopefully, someone in this excellent Ubuntu community will help.

---

### Post by cyracks on 2006-06-08
Same here, just want to be informed if there will be any interesting solutions. Did any of you tried to manage ldap with gosa ?

---

### Post by A1ex on 2006-06-08
There's also phpLDAPadmin.

Failing that, there are other exchange-like programs in the pipeline for linux:

HULA - [http://www.hula-project.org/Hula_Project]("http://www.hula-project.org/Hula_Project")

Open Exchange - [www.open-xchange.org]("http://www.open-xchange.org")

---

### Post by cyracks on 2006-06-21
Today I was browsing the web and came across these links:

Setting address book:
[http://www.onlamp.com/pub/a/onlamp/2003/03/27/ldap_ab.html]("http://www.onlamp.com/pub/a/onlamp/2003/03/27/ldap_ab.html")

An introduction to ldap:
[http://www.onlamp.com/pub/a/onlamp/2001/08/16/ldap.html]("http://www.onlamp.com/pub/a/onlamp/2001/08/16/ldap.html")
[http://www.onlamp.com/pub/a/onlamp/2002/10/17/essentialsysadmin.html]("http://www.onlamp.com/pub/a/onlamp/2002/10/17/essentialsysadmin.html")

Ldap schema:
[http://ldap.akbkhome.com/index.php]("http://ldap.akbkhome.com/index.php")

I think it is easy to understand and could be easily applyed to dapper version of ldap. At the moment I don't have time to actually try to build my own address book since I have a lot of exams but will try in a couple of weeks. So if anybody will try before that let us know.
[LEFT]
[/LEFT]

---

### Post by telecomando on 2006-08-10
I been reading over this guide for Gentoo, I haven't quite got it working yet, but I think I am getting there.
if I ever figure this out, I'll post how i did it.

[http://forums.gentoo.org/viewtopic-t-126278-postdays-0-postorder-asc-start-0.html](http://forums.gentoo.org/viewtopic-t-126278-postdays-0-postorder-asc-start-0.html)

---

### Post by telecomando on 2006-08-10
And this
[http://www.ubuntuforums.org/showthread.php?t=200068&highlight=ldap+address+book](http://www.ubuntuforums.org/showthread.php?t=200068&highlight=ldap+address+book)

---

### Post by sheberlein on 2006-08-10
Look at openldap it may be what you are looking for. It is listed in my package manager(running ubuntu 6.06) some of the tools are installed on my system by default.  Good Luck!

---

