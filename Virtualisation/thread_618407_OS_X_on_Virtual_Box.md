---
title: "OS X on Virtual Box?"
date: 2007-11-20
forum: Virtualisation
---

### Post by Toy Machine on 2007-11-20
Is it possible to install Mac's OS X on a virtual machine such as Virtual Box?

---

### Post by flaggh on 2007-11-20
I've seen OSX VMware images on some torrent search engines, so if it's possible to install it on VMware, I don't see why VirtualBox would be any different.  There are also many people that have put together their own OSX based "Hackintosh" computers using non-Apple hardware, so again if they can install it onto any x86 based machine I don't see why you wouldn't be able to install it on VirtualBox.

---

### Post by maybeway36 on 2007-11-20
Not legally :P

---

### Post by cenwesi on 2007-11-20
I too want to know... i did d/l a torrent couple weeks ago but i could load it up. It loads up half way and reports some sort of error.

---

### Post by MrSpiffdifilous on 2007-12-08
I'd like to know if this would be possible with the installation disk. I'm not sure which version I have but my wifes G4 Powerbook has kicked the bucket and now she has to use my computer however she doesnt like ubuntu that much and windows frustrates the hell out of her(cant say I blame her). I know that Virtualbox has options for different mac os's but the list is as follows: OS/2 Warp 3 ,OS/2 Warp 4, OS/2 Warp 4.5. Which one would I use? Like I said its a G4 from about 4 years ago I think.

also as a side note, why would synaptic tell me I cant run VMware because my computer is i386?

---

### Post by zekopeko on 2007-12-09
those OS/2 Warp 3,4,4.5 are NOT Mac OS X. They are a different OS all together.

---

### Post by MrSpiffdifilous on 2007-12-11
> **zekopeko said:**
> those OS/2 Warp 3,4,4.5 are NOT Mac OS X. They are a different OS all together.

aww craptacular. any way to make it happen in virtualbox? I checked out Qemu but instantly felt I was in over my head

---

### Post by flaggh on 2007-12-11
I don't think it will be possible to use any currently available virtualization software to get it to run "natively" like it does on Apple hardware.

---

### Post by mat_london on 2007-12-13
Apparently it does .....

[URL="http://db.xbench.com/merge.xhtml?doc2=256720"]
http://db.xbench.com/merge.xhtml?doc2=256720[/URL]

---

### Post by MrSpiffdifilous on 2007-12-13
if I read that right it said he installed it as a FreeBSD in virtualbox....I'll give this a try today and post results

---

### Post by flaggh on 2007-12-13
As I mentioned in one of my previous posts, you can get it to run, but it won't be easy and it won't run out of the box.  For instance, I'm almost certain you won't be able to use the software updates feature.  Installing OS X on non-Apple hardware is against their terms of use so they don't make it easy.

---

### Post by khurrum1990 on 2007-12-13
It is possible on various torrent sites, I won't say which cause it might be against torrent rules, u can download patched versions of tiger and leopard to run on vmware, virtualbox, and x86.

---

### Post by MrSpiffdifilous on 2007-12-16
I tried the way I posted before....no luck at all. Someone has emailed me...a document that may or may not be expicit instruction on how to get this to work. If anyone here would like this document I may or may not be able to send it to you. if you catch my drift. :)

---

### Post by mat_london on 2007-12-18
It appears its possible to get a native vdi version running.

These results are not bad for a virtualised version of OSX, even if these tests don't include the graphics.

[http://db.xbench.com/merge.xhtml?doc2=258888](http://db.xbench.com/merge.xhtml?doc2=258888)

---

### Post by rickycodie on 2007-12-18
sweet i've been wanting to so this for so long.

---

### Post by airtonix on 2007-12-18
the only reason why apple os software runs n intel stuff is because hte new intel stuff has more cpu instructions that support the requirements of OSX.

Even when putting together real hardware, you have to really be sure that every part of your motherboard, cpu and ram are all going to support waht ever OSX requires.

Close friend of mine bought new components with the intention of creating a hackintosh.

turns out he sata controller on the board gave him no end of problems when setting up ubuntu , whereas OSx didnt care. driver issues with ubuntu it turns out. kernel level.

---

### Post by LostBear on 2008-05-31
You will get a performance hit with using Virtual Box or vmware or any other virtualisation software. As someone who has got osx (tiger and leopard) running on a Striker Extreme Nvidia 680i board (very tricky but not impossible) and on a little Asus Pundit computer (very very easy!!) i would suggest if you really want to run it on a pc, get an Asus Pundit. Its very close interms of spec to mac mini, even down to the onboard graphics. a doddle. a pundit is about £100/$200 - stick in a 80GB hard drive (you will run into trouble with bigger) and a dvd drive (IDE is best). Use kalyway. Once installed, it will boot to the osx desktop in 5 seconds.

---

### Post by p_quarles on 2008-05-31
> **maybeway36 said:**
> Not legally :P
+1. Thread closed.

---

