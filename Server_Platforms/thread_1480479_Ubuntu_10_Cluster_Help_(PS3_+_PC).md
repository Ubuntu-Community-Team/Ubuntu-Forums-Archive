---
title: "Ubuntu 10 Cluster Help (PS3 + PC)"
date: 2010-05-11
forum: Server Platforms
---

### Post by myrainbow on 2010-05-11
Hi, is it possible to make a cluster with a PC and a linux compatible PS3 by installing Ubuntu 10 on them? There are server and desktop editions but i couldn't know which ones should be installed on PS3 and PC. And i don't know how to setup the cluster after installing Ubuntu. Could you help me? Thank you.

---

### Post by myrainbow on 2010-05-11
Isn't there anyone who have knowledge about clustering PS3 and PC with Ubuntu 10? = \

---

### Post by myrainbow on 2010-05-11
Help...

---

### Post by myrainbow on 2010-05-11
Don't you know? I only want to make a simple CPU cluster. Doesn't Ubuntu support clustering?

---

### Post by myrainbow on 2010-05-11
Nobody is answering me..I want to cluster my PS3 and PC but i don't know how to do. I downloaded both Ubuntu 10 Desktop and Server editions but which ones should i install on the devices? If i must install the server edition, what should i do to setup my cpu cluster? You may also give me somebody's account name if you're sure of that they know about clustering so i can send them pm. Thank you!

---

### Post by myrainbow on 2010-05-12
Help! =\

---

### Post by stevanbt on 2010-05-12
Hi,
Perhaps you may get more answers in the server forum?

Thanks, Steve.

---

### Post by lisati on 2010-05-12
Threads merged and moved to "Server platforms".

---

### Post by myrainbow on 2010-05-12
> **stevanbt said:**
> Hi,
Perhaps you may get more answers in the server forum?

Thanks, Steve.
I hadn't known, i am new here. Thank you.
> **lisati said:**
> Threads merged and moved to "Server  platforms".
Thanks.

---

### Post by TheFuturian on 2010-05-12
Here's a start:-

[https://help.ubuntu.com/10.04/serverguide/C/clustering.html](https://help.ubuntu.com/10.04/serverguide/C/clustering.html)

Have you already got Ubuntu installed on your PS3?

---

### Post by doas777 on 2010-05-12
well start off at [http://psubuntu.com/](http://psubuntu.com/) for getting the software and getting it installed. if you don't want to use their software, then you are pretty much on your own. not sure if they ahve a lucid version.

---

### Post by myrainbow on 2010-05-12
> **TheFuturian said:**
> Here's a start:-

[https://help.ubuntu.com/10.04/serverguide/C/clustering.html](https://help.ubuntu.com/10.04/serverguide/C/clustering.html)

Have you already got Ubuntu installed on your PS3?
No, not yet. I am thinking of firstly installing Ubuntu 10 Server and secondly installing U10 Desktop to have graphical interface via:
sudo apt-get install ubuntu-desktop
instead of installing it directly from U10 Desktop CD. I wonder if i am doing it right. Thank you for the link..

---

### Post by myrainbow on 2010-05-12
> **doas777 said:**
> well start off at [http://psubuntu.com/](http://psubuntu.com/) for getting the software and getting it installed. if you don't want to use their software, then you are pretty much on your own. not sure if they ahve a lucid version.
thank you, i want to try it with the new version of Ubuntu..

---

### Post by myrainbow on 2010-05-13
Help...

---

### Post by arrrghhh on 2010-05-13
> **myrainbow said:**
> Help...

Don't mean to rain on your parade, but if you updated your PS3 recently you lost the ability to install an "Other OS".  They made it pretty clear when you updated... IF you updated I should say.


If you didn't congrats!  But you're one of the few.  Development of Linux on the PS3 is going to die with that nail pretty much, hardly anyone is going to want to keep their PS3 outdated - it won't let you login to the PSN if you don't keep the system up-to-date!!

Ubuntu does support clustering BTW, it is just much easier to use traditional computers rather than a console like the PS3.  I know, I know, it really *is* just a computer inside, but Sony locks down a lot of the hardware.  Not really much of a computer now.

---

### Post by myrainbow on 2010-05-13
> **arrrghhh said:**
> Don't mean to rain on your parade, but if you updated your PS3 recently you lost the ability to install an "Other OS".  They made it pretty clear when you updated... IF you updated I should say.


If you didn't congrats!  But you're one of the few.  Development of Linux on the PS3 is going to die with that nail pretty much, hardly anyone is going to want to keep their PS3 outdated - it won't let you login to the PSN if you don't keep the system up-to-date!!

Ubuntu does support clustering BTW, it is just much easier to use traditional computers rather than a console like the PS3.  I know, I know, it really *is* just a computer inside, but Sony locks down a lot of the hardware.  Not really much of a computer now.
I did not update my PS3 for this. Could you tell me an easy instruction of settting up a cluster between two PCs if you know? someone gave a link above but could not clearly understand it. what should i do? will it be enough to install ubuntu server on the both devices and to plug in the LAN cable between them? does the U10Server enables PCs (PS3&PC) to detect each other automatically like openmosix does or is there any additional settings needed after OS installing?

---

### Post by arrrghhh on 2010-05-13
I think I need more context as to *why* you are clustering.  What do you want to achieve?  Are you needing redundant services?  Do you just need a server that holds your files with clients connecting to it?  Clustering is not exactly as easy as just plugging in a cable between two computers, unfortunately.  There's a lot of things that need to happen to setup a cluster, and again no offense but it really doesn't sound like you need a cluster...

---

### Post by myrainbow on 2010-05-13
> **arrrghhh said:**
> I think I need more context as to *why* you are clustering.  What do you want to achieve?  Are you needing redundant services?  Do you just need a server that holds your files with clients connecting to it?  Clustering is not exactly as easy as just plugging in a cable between two computers, unfortunately.  There's a lot of things that need to happen to setup a cluster, and again no offense but it really doesn't sound like you need a cluster...
I want to make a CPU cluster to use the power of Cell Processor like this one here:
[http://www.youtube.com/watch?v=oLte5f34ya8](http://www.youtube.com/watch?v=oLte5f34ya8)
for my rendering processes...

---

### Post by arrrghhh on 2010-05-13
I can't watch youtube videos at work, sorry.  I've heard of clusters built using the Cell Processor, but they usually had special access that Sony prevents typical users from accessing.  I could be totally wrong here, but it just seems to me that the PS3 does not make a viable device for clustering/rendering without full access to the hardware.

---

### Post by myrainbow on 2010-05-13
> **arrrghhh said:**
> I can't watch youtube videos at work, sorry.  I've heard of clusters built using the Cell Processor, but they usually had special access that Sony prevents typical users from accessing.  I could be totally wrong here, but it just seems to me that the PS3 does not make a viable device for clustering/rendering without full access to the hardware.
is it possible to contact someone from the Ubuntu team who can have wide knowledge about this?

---

### Post by myrainbow on 2010-05-13
How can i contact the Ubuntu team?

---

### Post by arrrghhh on 2010-05-13
I think you're barking up the wrong tree here...  Just a heads up.

---

### Post by doas777 on 2010-05-14
> **myrainbow said:**
> How can i contact the Ubuntu team?
money talks.
[http://www.ubuntu.com/support/services](http://www.ubuntu.com/support/services)

---

### Post by myrainbow on 2010-05-14
> **doas777 said:**
> money talks.
[http://www.ubuntu.com/support/services](http://www.ubuntu.com/support/services)

thank you for the link, i prefer trying by myself untill it will work O.O

---

### Post by myrainbow on 2010-05-17
nobody knows about cpu clustering lol  = |

---

### Post by BobVila on 2010-05-17
> **myrainbow said:**
> nobody knows about cpu clustering lol  = |

I don't want to be mean, but instead of the constant bumping asking for someone to tell you how to do this, why don't you get your OSes installed and read one of the guides that have been posted? If you have more specific questions, someone will inevitably chime in to help, but you've got to take some initiative here and have a concrete question.

---

### Post by jd65pl on 2010-05-17
Like others have said, this isn't a matter of plug and play. [This guide]("http://www.debianclusters.org/index.php/Main_Page") is comprehensive.

---

