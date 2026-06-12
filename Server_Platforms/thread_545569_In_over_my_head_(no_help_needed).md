---
title: "In over my head (no help needed)"
date: 2007-09-07
forum: Server Platforms
---

### Post by rustybronco on 2007-09-07
I just got 3 proliant 1850r servers and 1 ml350 server given to me, I guess its time to learn how to set up a server don't you think? 
I know nothing about servers! I feel a crash course coming.

---

### Post by gishaust on 2007-09-07
Crash course in anything is fun and exciting
good luck

---

### Post by p_quarles on 2007-09-07
Here's a reasonably good tutorial on using Ubuntu to set up a server with some basic services. 
[http://www.howtoforge.com/perfect_setup_ubuntu704?](http://www.howtoforge.com/perfect_setup_ubuntu704?)

If you're planning on running a Linux-based server, you'll also want to get familiar with the command line. I recommend Scott Granneman's *Linux Phrasebook*. It does a really good job of explaining how commands work.

There are also online guides to the command line, e.g.:
[http://tldp.org/LDP/Bash-Beginners-Guide/html/index.html](http://tldp.org/LDP/Bash-Beginners-Guide/html/index.html)

---

### Post by rustybronco on 2007-09-07
Linux is all that i use now, a matter of principal.
Windows stopped when I kept having to ask uncle gates if I can use my oem copy's of xp after changing a hard drive, motherboard, video cards and the like.
I may try ubuntu on them first but centos probably will be the os of choice for the servers.
Command line is not a worry I started in the days of d.o.s., one of the first things I do when i install linux is to add the terminal to the panel. 
Mr. p_quarles thanks for the links i'm sure to get use of them.

---

### Post by rustybronco on 2007-09-09
Update*** picked up the servers tonight and low and behold the compaq ml350 is like brand new, it was used as a backup server and had less than 8 hours run time in 8 years of service. it has a single p-III 800mhz cpu (waiting for a second cpu to arrive) 512megs ram, 3- 18.2 gig ultra-wide2 scsi drives, and the best part is two of the drives were not ever hooked up! tie straps still holding the cables to the case.
I downloaded smart start 5.5 and centos 5 and burned them to cd when i can find a few minutes on the server they go and the learning begins. (hard drive died on this desktop so it killed the time tonight)

it looks like the start of a great home file/web server to me.

---

### Post by southernman on 2007-09-09
Off-topic-

Want to sell one of those proliants? ;)

---

### Post by rustybronco on 2007-09-09
Sorry no, my son is taking two of the 1850r's and the other 1850r i'm building for my wifes work. BUT my cousin which I had gotten them from says he gets them every 4-6 months, 8 servers in total this time.
He is also a good source of laptops for me (5-6 so far). I'll pm you the next batch.

---

### Post by southernman on 2007-09-09
Sounds good rustybronco. I would appreciate it.

<--- 70-71 half cab bronco going on ebay soon. Project truck

Back on topic. Below is a link you may find useful. Happy Reading.
[http://www.debian.org/doc/manuals/securing-debian-howto/]("http://www.debian.org/doc/manuals/securing-debian-howto/")
Section 1.2 has links to download the manual for off line reading.

---

### Post by BajaMnstr on 2007-09-12
I tell ya it's like a man glutton for punishment that you push yourself to do these things? I really hope it's not some crazy attempt to prove yourself to me. Because you did it a long time ago and i respect you for that. 

Here nor there, good luck on the ubuntu install though. I got server 2003 to work, and it's nice and all but bleh it's just like being at work. but then again so is ubuntu or redhat or SuSe or Debian or Mandriva or Gentoo. I think i'll try solaris. lol that should be good for a laugh, i guess i just like installing every os possible. Well personally i wish i could put Darwin and OSx86 on it. But i'm thinking most of the wierd hardware (wierd to a mac that is) won't be recognized. 

<--windows server 2003 Running DNS Caching, SquidNT (Configured by Kracken) and firewall/proxy.

---

### Post by rustybronco on 2007-09-13
Who let you in here? 
WORLD... meet my son, the one who challenges me, lucky to have him.
baja, haven't had the time to play with the ml350 yet, just have centos5 on it, I downloaded webmin tar.gz maybe if I get the time tonight i'll install it but the cabinets need to be finished first.

do you still  dual boot vista & sabayon, or did you change it to something else?

*** about that no help needed part*** My son is an admin @ a local i.s.p. and my cousin is an i.t. professional for a technologies corporation 
PLUS  these forums who could ask for anything else in the way of help.

---

### Post by BajaMnstr on 2007-09-14
I think they let anyone in here honestly. :lolflag:

But seriously yes i still have the laptop setup that way. And it'll probably stay for a while till i get the time to compile a decent broadcom driver, that or replace the broadcom card in the laptop with something atheros based  (See Ubiquity XR2 or a WLM54AG) Atheros is the best. And is supported at kernel level in new linux builds. Damn broadcom and their crappy chipsets. Someone should just put them out of their misery. Oh well works ok in Vista i guess. But latency and connection drops in linux are horrendus. 

I've got an idea I'll take and make hardware, then write software for it and keep it closed source, then i'll flood the market with them and use my newfound market position to force my crud down peoples throats. And then half-arsed support the largest power-user base in the world. 
oh wait broadcom already does that.

-Wayne

---

### Post by southernman on 2007-09-14
hmmm, I see the resemblence even:

rustybronco > BajaMnstr
> **BajaMnstr said:**
> I've got an idea I'll take and make hardware, then write software for it and keep it closed source, then i'll flood the market with them and use my newfound market position to force my crud down peoples throats. And then half-arsed support the largest power-user base in the world. 
oh wait broadcom already does that.

-WayneI just knew that was going to end with something containing the words Microsoft or Windows! :p

Welcome!

):P

---

### Post by rustybronco on 2007-09-15
server up and running, sftp so far.

---

