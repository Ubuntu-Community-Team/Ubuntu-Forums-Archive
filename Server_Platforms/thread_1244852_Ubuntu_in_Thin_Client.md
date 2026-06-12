---
title: "Ubuntu in Thin Client"
date: 2009-08-19
forum: Server Platforms
---

### Post by carlos_sun on 2009-08-19
Dear All;:lolflag:
    
    I'm trying to understand if I would install Ubuntu OS in my thin Client.
    
    I have and HP-Neoware C50 thin client based on X86, however, HP would close this line, and I would not have more support. so I'm thinking add Ubuntu inside.

    The spec of C50 is
       RAM 256MB
       Flash 256MB
    So I have too many restriction, please someone who know how could I add in, please advice.

---

### Post by lykwydchykyn on 2009-08-19
> **carlos_sun said:**
> Dear All;:lolflag:
    
    I'm trying to understand if I would install Ubuntu OS in my thin Client.
    
    I have and HP-Neoware C50 thin client based on X86, however, HP would close this line, and I would not have more support. so I'm thinking add Ubuntu inside.

    The spec of C50 is
       RAM 256MB
       Flash 256MB
    So I have too many restriction, please someone who know how could I add in, please advice.

Are you wanting to netboot (PXE) the thin client to an ubuntu server, a la LTSP, or actually put Linux on the thin client's flash drive?

I have on old compaq thin client at work with similar specs (256 RAM/Flash), and all I've ever gotten to work on it was damnsmalllinux, and that only with some major finagling.

Even a minimal install of Debian required about 600 MB.  Ubuntu is unlikely to get smaller than that, even at its most minimal.

---

### Post by scorp123 on 2009-08-20
> **carlos_sun said:**
>  I have and HP-Neoware C50 thin client Take it apart and take a look inside. Does it have an IDE connector?

Read here why I am asking (just ignore the rest that is irrelevant to you):
[http://ubuntuforums.org/showpost.php?p=7622202&postcount=17](http://ubuntuforums.org/showpost.php?p=7622202&postcount=17)

So yes, I converted a thin-client that originally had Windows CE on it into an Ubuntu system, thanks to that IDE-Flash drive below.

[IMG]http://www.transcendusa.com/Products/images/IFD/DOM_IDE//DOM40V-S_530x400-8G.jpg[/IMG]

So that's why I suggest you take your thin-client apart. Slowly. With lots and lots of caution ... If you're lucky your current thin-client OS (Windows CE?) is also stored on such a IDE-Flash drive and it should therefore be possible to replace it with something else, e.g. above 8 GB drive.

---

