---
title: "Random lockups with Lubuntu 13.10 beta1 64 bit"
date: 2013-09-17
forum: Ubuntu Development Version
---

### Post by santosh83 on 2013-09-17
Hello all,

Recently I installed the amd64 version of Lubuntu 13.10 beta1 alongside my still existing installation of 10.10.

There were a few minor bugs for which I submitted bug reports and generally the system runs well except for one big problem.

At apparently random times it'll completely freeze. No keys will work, not even CTRL+ALT+DEL of the SysRq key combinations, and no disk activity as well. The only solution when this happens is to cold reboot via the reset button. :-(

During my three years of running 10.10 on the same CPU (and one year on the same motherboard), this NEVER happened. Even now when I boot into 10.10 there are no lockups. This leads me to think if this is possibly a problem with the newer kernel and drivers (v3.11 vs v2.6.35 in 10.10) not playing well with my old hardware?

Processor is Intel Pentium Dual Core E2140 1.6 GHz and mainboard is MSI G41M-P33 combo (Intel G41 chipset) for what it's worth.

The freeze-up particularly seems to happen when I close or open OpenGL apps like Flightgear or Firefox. I tested the RAM with Memtest86 and it is fine. I'm thinking it is a combination of flaky mainboard hardware and the new kernel...

Would downgrading to Precise help? Everything is fine except for this issue...

---

### Post by mörgæs on 2013-09-17
> **santosh83 said:**
> 
Would downgrading to Precise help? Everything is fine except for this issue...

It's likely, but noone can answer for sure. I would go for Raring, though. Please try and let us know the results.

---

### Post by santosh83 on 2013-09-18
Thanks!

Just to test if it is something solely specific to the newer version I've installed a heavy OpenGL app (flightgear) on both 10.10 and 13.10, and will test them both to the limit. I already know lockups often occur in 13.10, and if 10.10 manages to run fgfs *without* any lockup, then this would indicate that something to do with newer kernel/graphics code is not tolerated by my hardware.

Not that I can do much in any case... I can hardly stick with 10.10 anymore! I guess I'll have to bear with the irritation of these freeze-ups until I can get a new mainboard and CPU. :-(

---

### Post by mörgæs on 2013-09-18
I don't see any indications that hardware is failing. Sounds more like the classical problems with a beta version.

If you want to isolate and report the bugs, which will be appreciated, it's better to compare 13.10 with 13.04 than 10.10.

---

### Post by sudodus on 2013-09-19
We think that the current problem that Lubuntu Saucy will freeze is caused by a regression that recent kernels do not cooperate well with zRAM. See this bug report

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1227202](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1227202)

It is very reproducible with the installer and low RAM, but it can happen at other instances too, during the installation or after the installation in the installed system.

---

### Post by santosh83 on 2013-09-19
> **sudodus said:**
> We think that the current problem that Lubuntu Saucy will freeze is caused by a regression that recent kernels do not cooperate well with zRAM. See this bug report

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1227202](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1227202)

It is very reproducible with the installer and low RAM, but it can happen at other instances too, during the installation or after the installation in the installed system.

This must be it. I remember that the install crashed at the very last stage too! Hopefully an update will soon patch this up. Except for this annoying problem I'm generally happy with 13.10... Thanks for the heads up. :-)

---

### Post by amjjawad on 2013-09-20
Two things I'd like to highlight, just to make sure the OP understands it clearly :)

1- Ubuntu 10.10 has reached its EOL already - [http://fridge.ubuntu.com/2012/04/10/ubuntu-10-10-maverick-meerkat-end-of-life-reached-on-april-10-2012/](http://fridge.ubuntu.com/2012/04/10/ubuntu-10-10-maverick-meerkat-end-of-life-reached-on-april-10-2012/)

2- Ubuntu Developmental releases are NOT for day-to-day usage:
[http://fridge.ubuntu.com/2013/09/06/13-10-saucy-salamander-beta-1-released/](http://fridge.ubuntu.com/2013/09/06/13-10-saucy-salamander-beta-1-released/)

Thank you :)

@OP
Please click on "affect me" on that bug ;)

---

### Post by santosh83 on 2013-09-20
> **amjjawad said:**
> 
2- Ubuntu Developmental releases are NOT for day-to-day usage:
[http://fridge.ubuntu.com/2013/09/06/13-10-saucy-salamander-beta-1-released/](http://fridge.ubuntu.com/2013/09/06/13-10-saucy-salamander-beta-1-released/)

I see that, but since we're this close to another release I didn't want to install 13.04 and upgrade/reinstall again in just a few weeks!

Lots and lots of little bugs/rough edges but this issue was the only major obstacle here, and now it looks as if there's an easy solution (turn off zram) until things get patched, so I think I'll ride this beta train onto 13.10. :-)

> 
@OP
Please click on "affect me" on that bug ;)

Done!

---

### Post by amjjawad on 2013-09-20
> **santosh83 said:**
> I see that, but since we're this close to another release I didn't want to install 13.04 and upgrade/reinstall again in just a few weeks!

That is your call and you are the only one who is responsible if anything might be broken ;)
Better Safe Than Sorry!

But, if you insist, since you are using Saucy, please, make sure to update your system daily:

```
sudo apt-get update && sudo apt-get upgrade
```



> Done!
Thank you!

P.S.
Get rid of your outdated 10.10 unless you have a good valid reason to keep it ;)

---

### Post by santosh83 on 2013-09-20
> **amjjawad said:**
> That is your call and you are the only one who is responsible if anything might be broken ;)
Better Safe Than Sorry!

But, if you insist, since you are using Saucy, please, make sure to update your system daily:

```
sudo apt-get update && sudo apt-get upgrade
```

Thank you!

P.S.
Get rid of your outdated 10.10 unless you have a good valid reason to keep it ;)

I do run the "System tools->Software Updater" 2-3 times a day! :-) But it doesn't do the 'apt-get upgrade' process right? I'll do that from the terminal then... As for 10.10, yes as soon as 13.10 is released and the dust settles.

---

### Post by amjjawad on 2013-09-20
> **santosh83 said:**
> I do run the "System tools->Software Updater" 2-3 times a day! :-) But it doesn't do the 'apt-get upgrade' process right? I'll do that from the terminal then... 

Software Updater should do all kind of updates but for me, I dislike it. I'd like to have more control over my system so I always use the Terminal :)


> As for 10.10, yes as soon as 13.10 is released and the dust settles.
Be careful that if that system has its GRUB installed to your MBR, if you want to remove it, you will need to re-install GRUB to the MBR. I am not sure if you are Dual-Booting 10.10 with 13.10 or not? but just be careful and if you need any help, let me know :)

---

### Post by sudodus on 2013-09-20
> **santosh83 said:**
> I do run the "System tools->Software Updater" 2-3 times a day! :-) But it doesn't do the 'apt-get upgrade' process right? I'll do that from the terminal then... As for 10.10, yes as soon as 13.10 is released and the dust settles.

It is only another user interface doing the same things as

```
 sudo apt-get update
```
and
```
 sudo apt-get dist-upgrade
```

See ```
man apt-get 
``` to find out the differences between upgrade and dist-upgrade.

---

### Post by santosh83 on 2013-09-20
> **amjjawad said:**
> Software Updater should do all kind of updates but for me, I dislike it. I'd like to have more control over my system so I always use the Terminal :)
> **sudodus said:**
> It is only another user interface doing the same things as

```
 sudo apt-get update
```
and
```
 sudo apt-get dist-upgrade
```

See ```
man apt-get 
``` to find out the differences between upgrade and dist-upgrade.

Thanks both. I'll look up the documentation for apt-get then.

> Be careful that if that system has its GRUB installed to your MBR, if you want to remove it, you will need to re-install GRUB to the MBR. I am not sure if you are Dual-Booting 10.10 with 13.10 or not? but just be careful and if you need any help, let me know :)

I did select the MBR for grub when I installed 13.10 beta, so it's now 13.10's grub which controls the show for both versions. :-) I think this will be fine as long as there are no 'update-grub' invoked from within 10.10...?

---

### Post by amjjawad on 2013-09-20
> **santosh83 said:**
> I did select the MBR for grub when I installed 13.10 beta, so it's now 13.10's grub which controls the show for both versions. :-) I think this will be fine as long as there are no 'update-grub' invoked from within 10.10...?

Once you decide to get rid of 10.10, you can just delete its partition using GParted while you are on 13.10 OR even better from a LiveCD or LiveUSB then just run:

```
sudo update-grub
```

From 13.10 ;)

You most welcome :)

---

### Post by sudodus on 2013-09-20
Even if there are 'update-grub' invoked from within 10.10, it will not write to the bootloader, so 13.10 should still be in control. But I don't think there will be much updating of 10.10 because it is way past the end of life.

---

### Post by cariboo on 2013-09-20
> **amjjawad said:**
> Two things I'd like to highlight, just to make sure the OP understands it clearly :)

1- Ubuntu 10.10 has reached its EOL already - [http://fridge.ubuntu.com/2012/04/10/ubuntu-10-10-maverick-meerkat-end-of-life-reached-on-april-10-2012/](http://fridge.ubuntu.com/2012/04/10/ubuntu-10-10-maverick-meerkat-end-of-life-reached-on-april-10-2012/)

2- Ubuntu Developmental releases are NOT for day-to-day usage:
[http://fridge.ubuntu.com/2013/09/06/13-10-saucy-salamander-beta-1-released/](http://fridge.ubuntu.com/2013/09/06/13-10-saucy-salamander-beta-1-released/)

Thank you :)

@OP
Please click on "affect me" on that bug ;)

You're preaching to the choir here. :-)

Most of us have found that Saucy has been pretty stable through the development cycle to the point where it can be used for day to day computing. It's gotten to the point where the cycle has been fairly boring, so many of us are trying different things, including using pre-release kernels, and enabling gnome-shell ppa's just so that we may find some interesting breakage.

---

