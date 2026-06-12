---
title: "Upgrading 12.04 to 14.04"
date: 2014-09-27
forum: Server Platforms
---

### Post by michael_stern2 on 2014-09-27
I am seriously appalled how poorly release upgrades are handled in Ubuntu. I compiled Xen on Ubuntu 12.04.1 LTS, works without problems. 
Now that 14.04.1 is out, Ubuntu is continuously prompting to update to 14.04.1 - after all, it'll no longer be supported in 2017.

Alas, upgrading that server is a surefire way to brick it. I am somewhat careful, and have a VM with the exact same configuration as my public facing servers, so of course I try the updates there first. First release upgrade, I document every key I press, and upon the end of the upgrade, I suddenly see a slew of errors in grub, and of course the whole thing is fubar after the reboot. 

Okay, sure, maybe I missed something. Since it's a VM, I can just revert to the snapshot before the update. Run the whole thing again, this time a bit more careful than before, trying to spot anything that could result in an unbootable system, installing a lot of the manufacture provided scripts when prompted. Nothing. The slew of grub errors is there again. This time I try and see if I can fix grub - but no dice. Apparently the whole thing changed completely. Reinstalling grub as suggested all over the place does nothing. Reboot the system, fubar again. That's a great way of introducing 14.04, because you can be absolutely sure I am not going to do that on any production server. 

Speaking of production server: Since a while ago, I also get this lovely panic-inducing message:
```
Your current Hardware Enablement Stack (HWE) is no longer supported since 2014-08-07. Security updates for critical parts (kernel and graphcis stack) of your system are no
longer available. For more information, please see: http://wiki.ubuntu.com/1204_HWE_EOL
```

It then goes on to tell you to do a release upgrade (I already know how that'll go), or to

```
* Install a newer HWE version by running:
sudo apt-get install linux-generic-lts-trusty linux-image-generic-lts-trusty

and reboot your system.
```

I think you should put that in a cookbook form, because it works just as well as doing a release upgrade. Like so:

**Upgrade your HWE version the Ubuntu way[SUP]TM[/SUP]**

[LIST=1]
[*]Make sure you're up to date: ```
sudo apt-get update ; sudo apt-get upgrade
```
[*]Install a newer HWE version: ```
sudo apt-get install linux-generic-lts-trusty linux-image-generic-lts-trusty
```
[*]Reboot: ```
sudo reboot
```
[*]Reinstall your system because you just bricked it.
[/LIST]


So I guess with Ubuntu, I have to reinstall my servers every few years. Great.

---

### Post by Bucky Ball on 2014-09-27
> **michael_stern2 said:**
> 
Now that 14.04.1 is out, Ubuntu is continuously prompting to update to 14.04.1 - after all, it'll no longer be supported in 2017.



Welcome. Unsure what you mean by this. 14.04 LTS is supported until April 2019 ... it will get to 14.04.5 and possibly beyond. ;)

12.04 LTS, also a long-term support release, is supported until 2017. 

(Incidentally, I am a big music fan, and Mike Stern is a legendary jazz/fusion guitarist!)

---

