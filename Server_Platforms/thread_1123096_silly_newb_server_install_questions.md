---
title: "silly newb server install questions"
date: 2009-04-11
forum: Server Platforms
---

### Post by mudguts on 2009-04-11
On the plus side, I didn't find any similar threads.
on the downside, I'm a complete idiot and have some stupid questions.

So my client has decommisioned about 25 Dell Poweredge servers - ranging from 1550's to 2860's to powervaults.

they have RedHat installed but they want the drives cleaned and formatted, my suggestion was installing ubuntu server but not configuring it.

So obviously, I need the 64 bit server edition, correct?
From there, when a machine has multiple drives in RAID formation, do i only install it on one drive and the RAID will put it on the other drives?

As well, I have some IBM blade servers, do I have to install it on each blade seperatly?

lastly, I'll be selling these when I'm done on eBay or Kijiji - if you want a good deal, let me know.  I've been selling 1850's with 2 x 3.6 processors and 2x 36GB scsi drives, 2 x power supplies, 4GB ram, remote access controller and rails for $400 USD or $500 CDN   
Shipping is not cheap though..

I appreciate your answers, thanks.

---

### Post by albinootje on 2009-04-11
> **mudguts said:**
>  they have RedHat installed but they want the drives cleaned and formatted, my suggestion was installing ubuntu server but not configuring it.

Why not just use this to clean them : [http://www.dban.org/](http://www.dban.org/)
After that you can do the formatting with a Gparted live cd.

---

### Post by ugm6hr on 2009-04-12
> **albinootje said:**
> Why not just use this to clean them : [http://www.dban.org/](http://www.dban.org/)
After that you can do the formatting with a Gparted live cd.

Indeed.  Just installing a new OS does not secure your data.  You need enterprise level hard drive formatter / eraser.  DBan is a good choice.

I'm not sure there is a lot of value in installing any OS, since anyone buying a server would likely be able to install their own.

---

### Post by mudguts on 2009-04-12
If I was gay, I'd say FABULOUS!!!
but I'm not so I'll stick with a 'Super Thanks!'

Super Thanks!

I'll give it a try and see what happens!

---

### Post by hyper_ch on 2009-04-12
It is advised to use a descriptive topic title, that means a topic title that gives some clue about the content in the thread itself...

A generic topic title like "noob here" or "need help" does not help at all. As you may have noticed, just about everyone posting in here has some kind of a problem or issue or question ;)

And it is also adviced to use seperate threads for unrelated problems so that you can mark each one individually as solved.

Or in short terms: Help others to help you ;)

See the forums policy, especially section II.2: [http://ubuntuforums.org/index.php?page=policy](http://ubuntuforums.org/index.php?page=policy)

Also, when you are asked to post output from (config) files or from a command, use [noparse]```

```[/noparse] brackets around (each) output. That makes it also easier to read.

---

