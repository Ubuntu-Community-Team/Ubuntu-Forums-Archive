---
title: "Submit your xorg.conf online :)"
date: 2007-04-10
forum: The Cafe
---

### Post by chakkaradeep on 2007-04-10
Hi All,

Submit your xorg.conf online [here]("http://www.xorg-conf.org/")

This really helps many people to get the right xorg.conf for their vide card. Kewl :)

---

### Post by PetePete on 2007-04-10
thats a great idea

but theres no search facility (that i could find?)

if you've got lots and lots of xorg.conf files there MUST be a way to quickly search them
like specify a monitor / vid card and list all the xorgs relating to them

top idea though

---

### Post by chakkaradeep on 2007-04-10
> **PetePete said:**
> but theres no search facility (that i could find?)

Yea, me too want the search function. Hope they would add it soon.

---

### Post by max7 on 2008-08-07
I am looking for such a site but this one is not working any more.
Is there alternative?

---

### Post by smartboyathome on 2008-08-07
Old post, so don't expect it to. I don't think there is anything similar, and besides, Ubuntu doesn't use Xorg now for graphics drivers unless you have NVidia proprietary. :(

---

### Post by Swarms on 2008-08-07
> **smartboyathome said:**
> Old post, so don't expect it to. I don't think there is anything similar, and besides, Ubuntu doesn't use Xorg now for graphics drivers unless you have NVidia proprietary. :(

Oh what does it use then? :o

---

### Post by BLTicklemonster on 2008-08-07
By proprietary, you mean restricted drivers, no? And if so, then what settings would one use for an Nvidia card to bleed the most out of one's card, eh?

---

### Post by FuturePilot on 2008-08-07
> **Swarms said:**
> Oh what does it use then? :o

The goal is to eventually eliminate xorg.conf all together and write the configuration dynamically with all the autodetection goodness. As of right now *most* of the configuration is written dynamically, however there is still a minimal xorg.conf which will eventually disappear.

---

### Post by BLTicklemonster on 2008-08-07
In my opinion, autodetect, and let the detected settings be placed in some file like, oh, I don't know, xorg.conf where a person can look, and say "no, no, no, I want more", and edit it to their liking. Honestly, what I want may not be what another person wants/needs. So the Ubuntu overlords are going to force us to use the driver configuration that they deem is best for us? I personally want something I can edit if I so desire. Let it autodetect all it wants, but let me tweak it once it's done.

---

### Post by FuturePilot on 2008-08-07
I believe it will still read the settings if a xorg.conf is present. So when they do get rid of it, if you create that file and put settings in it, it should read from that. You'll almost always need a device specified if you use the Nvidia binary driver because X [will not default to that driver if it is installed]("http://www.phoronix.com/scan.php?page=news_item&px=NjYwMw")

---

### Post by max7 on 2008-08-08
I can't configure xorg.conf with nvidia dual screen with one 1650x1050 lcd and internal one. 
If someone know how to do that please post it here
[http://ubuntuforums.org/showthread.php?t=883114](http://ubuntuforums.org/showthread.php?t=883114)

---

