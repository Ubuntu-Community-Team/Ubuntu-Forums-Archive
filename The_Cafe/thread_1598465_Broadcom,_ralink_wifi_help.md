---
title: "Broadcom, ralink wifi help"
date: 2010-10-16
forum: The Cafe
---

### Post by Hippytaff on 2010-10-16
After about two months of joining this forum there was a wave of help requests in the beginner forum about the difficulties connecting to the interweb with  ralink and broadcom chipsets - I tried to help and learned a lot about ndiswrapper and blacklisting in the process...and there were many others with much more knowledge than me that helped...must have worked because I haven't seen a post about this for a few weeks now :-D

---

### Post by Hippytaff on 2010-10-16
Bad post - how do you delete posts :-)

---

### Post by EarthMind on 2010-10-16
You just post "Abracadabra", with the capital letter.

---

### Post by inobe on 2010-10-16
no need to delete the post.

was this one of the cards affected ?

```
01:05.0 Network controller: RaLink RT2800 802.11n PCI
```

---

### Post by Hippytaff on 2010-10-16
> **inobe said:**
> no need to delete the post.

was this one of the cards affected ?

```
01:05.0 Network controller: RaLink RT2800 802.11n PCI
```

As far as I remember and all the rt28xxx....something to do with not releasing the drivers for open source use (or something)....

broadcom have decided to let their drivers be use open source from now on though...so the next Linux releases will be better supported by ex capitalists :-)

---

### Post by inobe on 2010-10-16
they made a good choice in doing so, these drivers can't be limited to a single platform, it would be absurd and their loss of sales.

releasing the code also benefits the vendor and relieves them of countless hours of work as it becomes community maintained.

look at nouveau, a video driver, it's better than ever, it's great to fresh install linux and be greeted with a 3d desktop.

---

### Post by Hippytaff on 2010-10-16
your right....shame the older nvidia stuff still causes problems

---

### Post by inobe on 2010-10-16
> **Hippytaff said:**
> your right....shame the older nvidia stuff still causes problems

the older nvidia stuff was just older, older ati cards were just older, my point is not as much went into these opensource drives some years back, they managed to build a community and improve them.

heck look at ati's proprietary driver, the opensource driver destroys it, it's a shame when the proprietary driver sucks.

many i know had issues with ati drivers then and now, the issues start because they feel they need to activate that buggy driver expecting better results.

some wireless devices drop connections as i've noticed in some threads, it's bad kernel modules that usually get fixed and folks need to get the modules in order to do that, sometimes it requires ndiswrapper.

if we study how far we have come within the last five years, it's astonishing.

back when i first began using opensuse 9.2 "everything" needed configuring, search for modules, edit config files, even xorg.conf.

now you install and almost nothing needs done "nothing" unless you want some proprietary stuff and a few apps.

so we are heading in that direction, hardware vender's jump on the bandwagon.

hardware was probably what held us back so long.

---

### Post by Khakilang on 2010-10-17
I had not problem with my USB wifi adapter. But some of the Distro like Debian doesn't work. It could be in the kernel I guess.

---

### Post by inobe on 2010-10-17
> **Khakilang said:**
> I had not problem with my USB wifi adapter. But some of the Distro like Debian doesn't work. It could be in the kernel I guess.

true, as these kernels improve these modules become included hence the term monolithic kernel.

---

