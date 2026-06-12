---
title: "Looking to become a Linux Admin"
date: 2008-06-03
forum: The Cafe
---

### Post by Mauler5858 on 2008-06-03
For my background, ive been a computer enthusiast all my life.  I have an Associate's Degree in computer technology, have been in IT support/Help Desk/Jr. Admin position(s) with roughly 3 years of experience.  About a year ago i took the interest in linux(using only ubuntu).  Ever since then ive been in head first trying to learn the OS.  I am now windows free at home on my desktop and my wife's laptop, and have a server that i have been steady trying to learn on(CLI+webmin only).  I want MORE.  If anybody has any reccomendations for activities, reading, learning i am all ears.  I want to transform my newfound passion for linux and IT experience into making me a feasable Linux Admin and making it into a career.  Any help would be so kindly appreciated.

---

### Post by ukripper on 2008-06-03
if you interested in becoming linux certified admin. 
i would recommend you start from LINUX+ (it is pretty basic level exam) [http://certification.comptia.org/linux/default.aspx](http://certification.comptia.org/linux/default.aspx)

and for advance levels - you have RHCE
[http://www.redhat.com/certification/rhce/](http://www.redhat.com/certification/rhce/)

in professional world these certificates value alot.


By the way I am Linux+ certified but I am a database application developer.

Linux+ gives you enough grounds up in linux essentials.

Goodluck

---

### Post by Mauler5858 on 2008-06-03
I have been thinking of that route.  I definately think i will look more into it.

Thanks.

---

### Post by Sef on 2008-06-03
Moved to Community Cafe.

---

### Post by macogw on 2008-06-03
Ditch webmin.  Learn proper.  Real SA's don't use webmin, they^W we use SSH.

EDIT:  I get to say "we" now, since it's now my job :)

---

### Post by FuturePilot on 2008-06-03
> **macogw said:**
> Ditch webmin.  Learn proper.  Real SA's don't use webmin, they use SSH.

SSH FTW. I've been putting a server together lately and I tried Webmin but I didn't like it. Now it's just SSH for me. It's quite fun using SSH to admin a system. :D

---

### Post by wdaniels on 2008-06-03
Take a look at the [Linux Professional Institute]("http://www.lpi.org/eng/certification") certifications - they also have a Ubuntu Certified Professional specifically.

---

### Post by toupeiro on 2008-06-04
SSH is most definately the common connection method for Linux/UNIX server admins. Trusted Hosts, netgroups, sendmail,NFS, NIS, NIS+, OpenLDAP, Active Directory Authentication for Linux, Samba/CIFS etc..  These are the things you must deal with in most corporate linux presences.

---

### Post by ukripper on 2008-06-04
I have to agree SSH is the best admin tool for me. i have tried Webmin but just don't seem to like it!
Got port forwarding setup and i use SSH for my home server from work. Works flawless!!

---

### Post by Mauler5858 on 2008-06-04
I actually use webmin very little.  I have only really used it to edit config files in a browser window rather than vi, but ive gotten better at vi so i am using it less.

---

### Post by Luke has no name on 2008-06-04
LINUX SUX GO BUY SERVER 2003

only your soul + tax

<_<

I had to get the 10 year old out of me. Now that that's over with, I'd suggest everything above this post! SSH is important, and a good certification will be useful, too. I've been chatting up the server team at my place of employment (40,000+ employee global company), here's what they've told me:

---Learn virtualization! They use VMWare ESX and Redhat for host machines, with Windows guests. There is a free version of VMWare out there though, and Xen is pretty full featured as well. "Running Xen: A Hands-On guide to the Art of Virutalization" is a good book (from reading the first chapter). Look into it.

Anyway, virtualization is the future of enterprise computing. If it isn't commonplace now, it will be soon, just like OOP is for programming. It's just 'there'. Know it.

---From there, there are of course different areas to focus on, depening on how specific you think your job will be. there are people who work ONLY with Storage Area Networks (SANs), and people who ONLY work on networks. Then there are admins for specific software, like Exchange(MS shop) or any other software your company needs.

General skills needed for being a Linux admin will be SSH admin, virtualization, and knowing how to run a secure system.

---

