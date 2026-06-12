---
title: "Samba 4.4 or newer?"
date: 2017-04-05
forum: Server Platforms
---

### Post by mickier2 on 2017-04-05
I am running Ubuntu 16.04.2 with Samba 4.3.11-Ubuntu version.  I am trying to delete an old dead/offline AD server, and the SAMBA howto states that BEFORE demoting a dead or offline server, make sure to upgrade to Samba 4.4
The latest samba which is supported in Ubuntu LTS seems to be 4.3.11 -  I also noted that according to Samba release schedule, that samba 3.4 is EOL as of March 7, 2017.  
[https://wiki.samba.org/index.php/Samba_Release_Planning](https://wiki.samba.org/index.php/Samba_Release_Planning)

So what's the right advice for my server? I hate to install from source - and then forever - i need to keep updating from source - plus updating my server from apt-get...  

What's the best thing for me to do? can I just ignore the samba wiki instruction and demote the dead server even though i'm on 4.3.11?

---

### Post by wildmanne39 on 2017-04-05
*Thread moved to **Server Platforms**.*

---

### Post by darkod on 2017-04-06
The decision is yours. I also don't like installing from source and then handling any update manually myself, but on the other hand I also don't like that the ubuntu team is so far behind with samba...

One thing to have in mind: removing a dead DC is actually more about clearing up records in AD. By definition of a dead DC, you will not be powering on that server in the network any more, right? All you need to do is to clean up AD to be aware and not look for that DC any more.

I don't know if you use Windows RSAT tools or not, but you can look online for tutorials how to remove dead DC traces from AD and use tutorials both for windows and samba, combine them for your case...

---

### Post by mickier2 on 2017-04-06
Thanks Darko! You are right  - i will not be powering up the dead DC any more so I could just ignore them.

I will also try the windows rsat tools.  I do use windows ad users and groups anyway - I know the point of samba AD is that windows clients "can't tell" it's not a windows server...

---

### Post by darkod on 2017-04-06
Just to make clear, you can't literary ignore a dead DC. That's why I am saying you need to clean up the records from AD. There are many tutorials that show you where to look for, most of them are for windows but the majority will apply because samba AD simulates windows. And some records that exist in windows AD might not exist in samba AD so that will be less things to worry about and clean up.

There are at least two records you need to clean up: the A record and the _msdcs record. If you check here it says how to check if they exist, so if you know how to find them you know how to delete them. But don't forget, there might be more things to delete...
[https://wiki.samba.org/index.php/Verifying_and_Creating_a_DC_DNS_Record](https://wiki.samba.org/index.php/Verifying_and_Creating_a_DC_DNS_Record)

---

