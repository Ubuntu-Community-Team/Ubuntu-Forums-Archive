---
title: "relatime in fstab"
date: 2012-03-15
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by novafluxx on 2012-03-15
I checked my fstab and don't see relatime in there. Is this something I should add or is it set elsewhere?

Been away from the game for a while now so I'm not sure if fstab even matters much anymore!

---

### Post by screaminj3sus on 2012-03-15
I am fairly sure ubuntu already uses relatime as default.

---

### Post by ajgreeny on 2012-03-15
> **screaminj3sus said:**
> I am fairly sure ubuntu already uses relatime as default.
Yes, it has done so for quite a while.

---

### Post by Bucky Ball on 2012-03-15
The realtime kernel you mean? Not used by default as far as I know (the rt kernel it is called and that is in the kernel name to signify that).

It is generally used for audio/video work (editing/creation, not just watching movies and listening to music) and not really necessary for a regular/day-to-day install. Mostly used in Ubuntu Studio which is designed for AV edit/creation.

Any reason you are wanting to use it? If not, don't bother adding. If you are intending to do serious AV work, then dig around in here for more info:

[http://www.google.com.au/#hl=en&sclient=psy-ab&q=installing+rt+kernel+ubuntu&oq=installing+rt+kernel+ubuntu&aq=f&aqi=g-v1&aql=&gs_sm=3&gs_upl=96618l96900l1l97603l2l1l1l0l0l0l228l228l2-1l2l0&gs_l=hp.3..0i15.96618l96900l1l97603l2l1l1l0l0l0l228l228l2-1l2l0.&pbx=1&bav=on.2,or.r_gc.r_pw.r_qf.,cf.osb&fp=4887cfbcfb0a79dc&biw=1024&bih=597](http://www.google.com.au/#hl=en&sclient=psy-ab&q=installing+rt+kernel+ubuntu&oq=installing+rt+kernel+ubuntu&aq=f&aqi=g-v1&aql=&gs_sm=3&gs_upl=96618l96900l1l97603l2l1l1l0l0l0l228l228l2-1l2l0&gs_l=hp.3..0i15.96618l96900l1l97603l2l1l1l0l0l0l228l228l2-1l2l0.&pbx=1&bav=on.2,or.r_gc.r_pw.r_qf.,cf.osb&fp=4887cfbcfb0a79dc&biw=1024&bih=597)

Again, really not necessary for a regular install ...


* Just read ajgreeny's post. Seems he/she knows something I don't. Or do they??? In this page:

[https://help.ubuntu.com/community/UbuntuStudioPreparation](https://help.ubuntu.com/community/UbuntuStudioPreparation)

... under Realtime Kernel, it doesn't appear it is the default in 12.04 LTS, and this:

> Ubuntu 12.04 will come with a low  latency kernel available in the repositories.  This kernel will be  maintained by the Ubuntu Studio devs.... from here:

[http://www.mixxx.org/forums/viewtopic.php?f=1&t=2996](http://www.mixxx.org/forums/viewtopic.php?f=1&t=2996)

If this is true I guess that would save you installing the ppa or UStudio repo manually, but used as default kernel? Appears not ... can't see why it would be as uses more resources (your machine needs some grunt), could have disastrous effects for some machines and configurations (has problems with some proprietary drivers and may render low-spec machines sluggish) and is really not necessary for everyday tasks. ;)

Using the rt kernel as the default for 12.04 LTS would be a *very* bad move.

---

### Post by dino99 on 2012-03-15
> **Bucky Ball said:**
> The realtime kernel you mean?

no :  relatime, way different of realtime or timereal or ...

---

### Post by toobuntu on 2012-03-15
Well, you could always check what mount options are in use by

```
$ mount
```

If using an SSD, the mount options [FONT="Courier New"]noatime,nodiratime[/FONT] are useful for prolonging its useful life.

[FONT="Courier New"]relatime[/FONT] is really most useful on mail spool directories, and is probably unnecessary otherwise. Personally, I use [FONT="Courier New"]noatime[/FONT] instead of [FONT="Courier New"]relatime[/FONT].

---

### Post by Bucky Ball on 2012-03-15
> **dino99 said:**
> no :  relatime, way different of realtime or timereal or ...

Oh, ha! As you were ...

Getting late here; I better go to bed! Enjoy ... ;)

---

### Post by novafluxx on 2012-03-15
Thanks guys. I was referring to the relatime option for mounting ext files systems.

When I run mount I get the following

```
/dev/sda1 on / type ext4 (rw,errors=remount-ro)

```

Along with other stuff

Since there's nothing set regarding access time, does this mean it defaults to relatime or noatime?

By the way, thank you Bucky Ball for the very good reply. It may not have been what I was looking for, but your reply was spot on and if it had been what I was looking for you'd have pointed me in the right direction! Thanks!

---

### Post by dino99 on 2012-03-15
some related readings:

[https://lwn.net/Articles/244829/](https://lwn.net/Articles/244829/)
[https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)

---

### Post by toobuntu on 2012-03-15
Short answer: the default behavior is [FONT="Courier New"]relatime[/FONT].

Longer answer, from [FONT="Courier New"]man mount[/FONT]:
> 
       relatime
[INDENT]      * * *
              Since Linux 2.6.30, the kernel defaults to the behavior provided
              by this option (unless noatime was  specified), and the stricta&#8208;
              time  option  is  required  to  obtain traditional semantics.[/INDENT]

---

### Post by novafluxx on 2012-03-16
> **toobuntu said:**
> Short answer: the default behavior is [FONT="Courier New"]relatime[/FONT].

Longer answer, from [FONT="Courier New"]man mount[/FONT]:

Thanks!

---

