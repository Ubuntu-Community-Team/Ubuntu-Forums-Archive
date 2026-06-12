---
title: "Netbook OS?"
date: 2008-12-01
forum: The Cafe
---

### Post by kevin11951 on 2008-12-01
I need a new operating system for my dell mini 9, the one it came with (ubuntu) was old (8.04.1) so i formatted with 8.10, but that takes up all but 100mb of the ssd, so...

what is a good OS for netbooks, i need something that will fit on 4gb, and will support the hardware of the dell mini 9.

also, hopefully something with a nice interface, like the ubuntu netbook remix.

---

### Post by cardinals_fan on 2008-12-01
SliTaz is awesome.

---

### Post by jdong on 2008-12-01
8.04 old? What's wrong with 8.04? It's still a fully supported, widely-used version of Ubuntu.

---

### Post by zmjjmz on 2008-12-01
> **kevin11951 said:**
> like the ubuntu netbook remix.

You just answered your own question.

---

### Post by snowpine on 2008-12-01
Hi Kevin, a few comments:

1) Ubuntu Hardy Heron is only 8 months old. It is a stable, functional, long-term-support version of Ubuntu. I am curious, in what way does it not meet your needs?
2) SliTaz is an awesome distro, but unfortunately lacks some important features to make it netbook-friendly (easily-configured wireless and 1024x600 resolution, for example).
3) CrunchBang Linux is my current favorite Ubuntu derivative for netbooks. It should fit easily on your 4gb drive. However, I am running it on an Asus eee, so I can't guarantee it will work on your Dell Mini 9. Curious if you try it to hear your opinion. :)

---

### Post by kevin11951 on 2008-12-01
> **zmjjmz said:**
> You just answered your own question.

the ubuntu netbook remix isnt a distro though, its a full size ubuntu install with a few changes, ie. to big for the tiny 4gb ssd.

---

### Post by zmjjmz on 2008-12-02
Well then I would recommend building an ubuntu minimal system from the ground up.
Just make sure you get the lpia build, for obvious reasons. The Mini's wifi chip is a bcm4310, and you shouldn't have any trouble installing that driver (in the b43-fwcutter package).
And if worst comes to worst, just use Dell's restore CD. Hardy is perfectly fine.

---

### Post by snowpine on 2008-12-02
I can't believe I forgot to mention Xubuntu! :) It will fit onto a 4gb drive no problem.

---

### Post by cardinals_fan on 2008-12-02
> **snowpine said:**
> 
2) SliTaz is an awesome distro, but unfortunately lacks some important features to make it netbook-friendly (easily-configured wireless and 1024x600 resolution, for example).

Wireless is obviously hit-or-miss on a case-by-case basis, but the three packages **linux-crypto**, **linux-wireless**, and **wireless_tools** should handle most cards.

The resolution should be solved by following this: [http://translate.google.com/translate?hl=en&sl=fr&u=http://forum.slitaz.org/viewtopic.php%3Fpid%3D5339&sa=X&oi=translate&resnum=2&ct=result&prev=/search%3Fq%3Dslitaz%2B1024x600%26hl%3Den%26client%3Dfirefox-a%26rls%3Dslitaz:en-US:official%26hs%3D6x2%26sa%3DG](http://translate.google.com/translate?hl=en&sl=fr&u=http://forum.slitaz.org/viewtopic.php%3Fpid%3D5339&sa=X&oi=translate&resnum=2&ct=result&prev=/search%3Fq%3Dslitaz%2B1024x600%26hl%3Den%26client%3Dfirefox-a%26rls%3Dslitaz:en-US:official%26hs%3D6x2%26sa%3DG)

Sorry for the overt SliTaz fanboyism today, but I just got it set up right on my main box (overwriting Arch) and I'm very excited with it :)

---

### Post by kevin11951 on 2008-12-02
> **zmjjmz said:**
> Well then I would recommend building an ubuntu minimal system from the ground up.
Just make sure you get the lpia build, for obvious reasons. The Mini's wifi chip is a bcm4310, and you shouldn't have any trouble installing that driver (in the b43-fwcutter package).
And if worst comes to worst, just use Dell's restore CD. Hardy is perfectly fine.

where do you get an ubuntu minimal iso?  i tried [http://releases.ubuntu.com](http://releases.ubuntu.com) but i couldn't find it.

---

### Post by jdong on 2008-12-02
A default Ubuntu install also should take less than 50% of the 4GB internal SSD -- are you sure you aren't creating an unnecessary swap partition as the installer naively suggests?

---

### Post by snowpine on 2008-12-02
> **cardinals_fan said:**
> Wireless is obviously hit-or-miss on a case-by-case basis, but the three packages **linux-crypto**, **linux-wireless**, and **wireless_tools** should handle most cards.

The resolution should be solved by following this: [http://translate.google.com/translate?hl=en&sl=fr&u=http://forum.slitaz.org/viewtopic.php%3Fpid%3D5339&sa=X&oi=translate&resnum=2&ct=result&prev=/search%3Fq%3Dslitaz%2B1024x600%26hl%3Den%26client%3Dfirefox-a%26rls%3Dslitaz:en-US:official%26hs%3D6x2%26sa%3DG](http://translate.google.com/translate?hl=en&sl=fr&u=http://forum.slitaz.org/viewtopic.php%3Fpid%3D5339&sa=X&oi=translate&resnum=2&ct=result&prev=/search%3Fq%3Dslitaz%2B1024x600%26hl%3Den%26client%3Dfirefox-a%26rls%3Dslitaz:en-US:official%26hs%3D6x2%26sa%3DG)

Sorry for the overt SliTaz fanboyism today, but I just got it set up right on my main box (overwriting Arch) and I'm very excited with it :)

You know I dig SliTaz too :) but I think it needs something like wicd or nm-applet before I would choose it for my netbook--a quick, graphical tool for scanning available wireless networks. The command line network.sh thing just doesn't cut it for me for a coffeeshop type of device. And the lack of 1024x600 support is a deal breaker.

I happily use SliTaz on my 1024x768 "around the house" laptop however.

---

### Post by kevin11951 on 2008-12-02
> **jdong said:**
> A default Ubuntu install also should take less than 50% of the 4GB internal SSD -- are you sure you aren't creating an unnecessary swap partition as the installer naively suggests?

no, i partition it manually, and i make sure the whole ssd is just one big ext3 partition.

---

### Post by snowpine on 2008-12-02
> **kevin11951 said:**
> where do you get an ubuntu minimal iso?  i tried [http://releases.ubuntu.com](http://releases.ubuntu.com) but i couldn't find it.

Google is your friend, Grasshopper: [https://help.ubuntu.com/community/Installation/MinimalCD](https://help.ubuntu.com/community/Installation/MinimalCD)

---

### Post by cardinals_fan on 2008-12-02
> **snowpine said:**
> You know I dig SliTaz too :) but I think it needs something like wicd or nm-applet before I would choose it for my netbook--a quick, graphical tool for scanning available wireless networks. The command line network.sh thing just doesn't cut it for me for a coffeeshop type of device. And the lack of 1024x600 support is a deal breaker.

I happily use SliTaz on my 1024x768 "around the house" laptop however.
Ah, that would make a difference.  I use SliTaz on my desktop, which doesn't move around a lot :D

I also have ifconfig, iwconfig, and iwlist ingrained rather deeply in my memory.

EDIT: What's wrong with netbox (I haven't used it, so I don't know if it's good or not)?

---

### Post by jdong on 2008-12-02
> **kevin11951 said:**
> no, i partition it manually, and i make sure the whole ssd is just one big ext3 partition.

Whoa, and how much space is it using on the SSD?

---

### Post by kevin11951 on 2008-12-02
> **jdong said:**
> Whoa, and how much space is it using on the SSD?

???

---

### Post by jdong on 2008-12-02
Can you post a sample of what 'df -h' looks like on a freshly installed Ubuntu? If I remember it should be around 2.1-2.4GB of used space, which still should give you plenty of space.

I can suggest some hacks like removing /usr/share/doc and squashfs'ing /usr to get you down near the 700MB arena.

---

