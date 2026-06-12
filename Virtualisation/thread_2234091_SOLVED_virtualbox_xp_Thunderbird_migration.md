---
title: "SOLVED virtualbox xp Thunderbird migration"
date: 2014-07-12
forum: Virtualisation
---

### Post by Paul_Matejcek on 2014-07-12
[SIZE=3]SOLVED

I'm an utter 'babe in the woods,'* migrating half a dozen or so systems from XP to Ubuntu -- including my home desktop.  This post is about my home desktop.  

I have three systems: Ubuntu 14.04 and Virtual XP on a 1TB drive, and XP on a 500MB drive.  I will probably  use Thunderbird for email on Ubuntu.  My Outlook Express email in the  virtuall XP was the most current, so I installed Thunderbird there, and had it import my mail and accounts form Outlook  Express.  Some of my virtualization parameters may be sub-optimal; it took 14-15 hours to do the import (2.66 GHz, 2 GB).  I have a lot of mail -- but not THAT much.  VirtualXP claimed using most (90%) of its CPU time on kernel.  But I digress.  

So, I have Thunderbird running in Virtual XP.   I will install it on Ubuntu.   I'm assuming/hoping that I can export it all in Thundrebird on 'VXP' and move it via shared folders to Ubuntu, and  import it to Thunderbird there.  Can I?  Are there any special pitfalls that you can warn me about in migrating Thunderbird from 'VXP' to Ubuntu?  I'm old, and I don't have time to make ALL of the possible mistakes myself.  

Thanks in advance, 

Paul in Wisconsin

(*except for years working with CLI-only systems including KOSMIC, RSX-11, VAX/VMS, and a bit of Unix and Ultrix in the '60s, '70s, and '80s[/SIZE].)

---

### Post by Paul_Matejcek on 2014-07-12
SOLVED.  

An  issue is that I thought I had installed Guest Additions, and had not.  I installed it on the systems at work...  Getting Guest Additions in and working made the shared folders work, and, for whatgever reason, seems to have really improved performance on the VXP system.  So, T-Bird is running on Ubuntu, and most of my old environment is moved over.  


Wish me luck!

Paul

---

### Post by TheFu on 2014-07-14
a) If solved, please mark the thread as **SOLVED**.

b) I've never hear of "VXP" - is that a term you made up?  There isn't anything special about a VM for 99.999999% of questions related to end-user applications, so I'm confused by the new term.

c) To my knowledge, thunderbird profiles are cross platform unless you installed binary addons/plugins.  I've moved the ~/.thunderbird/ directories across at least 5 different systems and they just worked when placed in the correct location on the next system. No need to import/export anything. It also worked with the lightning (calendar settings).

d) For tuning virtualbox - [http://blog.jdpfu.com/slowVbox](http://blog.jdpfu.com/slowVbox) has the settings.

---

### Post by Paul_Matejcek on 2014-07-16
If solved, please mark the thread as **SOLVED**.
[COLOR=#0000ff]Done.  It took me a while to figure out how to edit the title.  
[/COLOR]
b) I've never hear of "VXP" - is that a term you made up?  There isn't anything special about a VM for 99.999999% of questions related to end-user applications, so I'm confused by the new term.
[COLOR=#0000ff]Sorry -- yes, I made it up -- antecedent just before: Virtual XP.  [/COLOR]

c) To my knowledge, thunderbird profiles are cross platform unless you installed binary addons/plugins.  I've moved the ~/.thunderbird/ directories across at least 5 different systems and they just worked when placed in the correct location on the next system. No need to import/export anything. It also worked with the lightning (calendar settings).
[COLOR=#0000ff]Translation and migration seems to be complete, Thunderbird seems to be performing 'as advertised.'[/COLOR]

d) For tuning virtualbox - [http://blog.jdpfu.com/slowVbox](http://blog.jdpfu.com/slowVbox) has the settings.
[COLOR=#0000ff]Thanks for the tip![/COLOR]

[I]
Is there a way to tell this forum to send me an email when there's a response to a post?  I just assumed it would do that...  

Paul in WI

[/I]

---

