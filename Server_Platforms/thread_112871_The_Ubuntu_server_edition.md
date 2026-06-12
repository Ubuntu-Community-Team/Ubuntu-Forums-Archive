---
title: "The Ubuntu server edition"
date: 2006-01-05
forum: Server Platforms
---

### Post by nocturn on 2006-01-05
I haven't seen much discussion about the Ubuntu server edition (here: [http://ubuntuforums.org/showthread.php?t=79093)](http://ubuntuforums.org/showthread.php?t=79093)).

From the page:
* Includes server-oriented kernels with out-of-the-box
automatic support for multiprocessor systems
* Includes a wide variety of popular server applications
such as apache, mysql, postgresql, php, zope, openldap,
bind, samba, all on the single CD, ready for installation
* A slim default installation, occupying just 400 megabytes:
add only the software you need, for a clean, maintainable
configuration.
* Provides no desktop environment (GNOME, KDE, etc.) by default
* Safe and text-oriented boot mode for better clarity and
infinite justice on boot.

Now, I'm wondering if this uses the same repositories as Breezy?  
Can I just upgrade my Hoary server to this new one and pull in the server-kernels?

---

### Post by Titus A Duxass on 2006-01-05
What is the difference between this server and the one that you can install by typing server at the boot prompt during the install?

I am interested because I carried out a server install recently because I needed a Mysql server for my GiantDisc application.

---

### Post by nocturn on 2006-01-05
[QUOTE=Titus A Duxass]What is the difference between this server and the one that you can install by typing server at the boot prompt during the install?

I am interested because I carried out a server install recently because I needed a Mysql server for my GiantDisc application.[/QUOTE]

All of the packages above (apache standard installed) and the modified kernels.

The problem is that I cannot seem to locate those kernels in the standard repo, so I'm wondering how to get them without using the server iso...

---

### Post by nocturn on 2006-01-05
I'm on the ubuntu-server IRC channel right now.

They guys there say that these features will make it in Dapper, but are not in right now.  This contradicts Matt Zimmerman's announcement.

---

