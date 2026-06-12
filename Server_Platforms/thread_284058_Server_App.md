---
title: "Server App"
date: 2006-10-25
forum: Server Platforms
---

### Post by Drezard on 2006-10-25
Hello, I have a mac O/S 10 computer, 2 Windows Xp computers, A Ubuntu Linux server and 2 other Ubuntu computers.

Im looking for a program that can run on my Linux server (I think its called LAMP maybe) That can hold user accounts for all of these computers on the one server. Meaning, that i can login to my mac with the username Drezard and then log off and then login on the Pc with the same username and password.

If there isnt one for all three of those O/S's then is there a program for Mac & Ubuntu for this and is there one for Windows & Ubuntu. 

- Cheers, Daniel

---

### Post by kidders on 2006-10-25
Hi there,

You're looking for LDAP-based authentication, I'd say. (LAMP is an acronym for Linux/Apache/MySQL/PHP.)

Most operating systems don't really care how they authenticate users ... Windoze is the fussy one, so it's the OS whose whims you'll have to bend to. My advice is to set up a Samba PDC to emulate a Microsoft domain, and join all your computers to it. That way, all your computers can authenticate against the same source. It's not the easiest thing in the world to do though!

---

### Post by wayne_za on 2006-10-25
Well see [opensourcecms]("http://www.opensourcecms.com") for a great link to some server apps. I run a few myself on my home server.

or take a look at the [freashmeat]("http://freshmeat.net/browse/183/")  site they have a PHP applications section.

Cheers,
Wayne
[mysite]("http://myparadigm,sytes.net/Joomla")

---

### Post by kidders on 2006-10-26
PHP apps won't be much help authenticating network users, I'm afraid :-(

---

