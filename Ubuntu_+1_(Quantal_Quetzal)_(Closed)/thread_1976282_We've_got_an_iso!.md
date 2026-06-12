---
title: "We've got an iso!"
date: 2012-05-08
forum: Ubuntu +1 (Quantal Quetzal) (Closed)
---

### Post by Mathor on 2012-05-08
Hope everyone has been enjoying their UDS thus far. As my first, it's pretty amazing.

I'm surprised this is up this early, but:

[http://cdimage.ubuntu.com/daily-live/current](http://cdimage.ubuntu.com/daily-live/current)

Get testing!

---

### Post by jerrylamos on 2012-05-08
Lubuntu quetzal daily build doesn't have i386 yet.  I run lubuntu quetzal on this notebook since it's a better fit.

I'll fire up my bigger notebook which does run unity (I prefer -2D) to give a go at the unity i386.  It'll do 64 bit but I don't bother.

Thanks for the tip, I'd been looking on occasion but didn't see it yet.

Jerry

---

### Post by Mathor on 2012-05-08
I just did a clean install of a daily build, and install went perfectly!

---

### Post by jerrylamos on 2012-05-08
Just for giggles I copied precise-i386 to quantal-i386 and did a zsync which started at 67% so if successful this will have relieved the server of 2/3 of the transfer.

Jerry

---

### Post by arpanaut on 2012-05-08
In my best Gomer Pyle voice:
SURPRISE SUR-PRISE!

I really wasn't expecting isos this early, I guess they ARE committed to making things work and to being able to test from the get-go. 8-)

---

### Post by nm_geo on 2012-05-08
Deleted the obvious

---

### Post by Mathor on 2012-05-08
> **nm_geo said:**
> I believe some of those dates are the last day of testing PP 12.04.. So they may be getting ready to spins some new ones but not all are QQ I bet.

All of the ones that are posted today and say "quantal" are QQ. Also, in my template on the fresh install it says "alpha1" 

 I think they are trying to be a little bit early, and have a good amount of bugs worked out by the first alpha, so they can get a lot more done this release.  In Precise, the majority of users couldn't even boot until about alpha 2.

---

### Post by ventrical on 2012-05-08
Thanks ! 

Works  great!!

 Install to hdd now on old Celleron 750Mhz/512sdram:)

---

### Post by ventrical on 2012-05-08
It's just amazing how these pre-alphas always works so seamlessly.

ventrical@ventrical-Dell-DV051:~$ lsb_release -a
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu quantal (development branch)
Release:    12.10
Codename:    quantal
ventrical@ventrical-Dell-DV051:~$ uname -a
Linux ventrical-Dell-DV051 3.4.0-1-generic-pae #3-Ubuntu SMP Wed May 2 17:52:29 UTC 2012 i686 i686 i686 GNU/Linux
ventrical@ventrical-Dell-DV051:~$ 


The 650mhz Celeron took too long .. I think I'll try Lubuntu on that.

---

### Post by ventrical on 2012-05-08
Looks like a lot of bugs fixed with the installer. Synaptic now downloads with the file dialog-box version which it did not in previous version  installs.. No need to update.

---

### Post by ronacc on 2012-05-08
amazing , startup-disk-creator actually made a bootable usb stick for me , that hasn't happened for awhile . trying an install on a spare drive .

---

### Post by rtalcott on 2012-05-08
Did a Virtual Box install and that worked...3d...everything...
rt

---

### Post by jerrylamos on 2012-05-08
I've got a hard drive, a usb hard drive, and a usb flash drive.  Booting .iso off the flash drive didn't work.  quantal iso gets all screwed up on which is /dev/sda or /dev/sdb or /dev/sdc.  Gets part way up, suddently can't find anything.  Acts like it switched what dev was which part way up.

Hmmm.

Jerry

---

### Post by rtalcott on 2012-05-08
I had no problem booting the iso off flash...AMD/Gigabyte board...although I did get lazy and did a VBOX install on another machine....

rt

---

### Post by grahammechanical on 2012-05-08
I am running the live session right now.

1) Sound is not muted. It was muted by default previously which was an issue for accessibility.

2) We can change the launcher icon size and there are no proprietary drivers installed. I did not think that we could change icon size in 2D. So, is this 2D? Not sure how to tell.

running the code

```
metacity
```

brings up the Already got Window Manager message.

So may be this is 3D

3) It has the 3.4.0-1 kernel.

4) It has the keyboard overlay and the HUD

It is looking good.

Regards.

---

### Post by wilee-nilee on 2012-05-08
Thanks OP, downloaded and installed using unetbootin, and running great with all my regular tweaks, time to clone it for a backup you never know. :)

---

### Post by nm_geo on 2012-05-08
Lubuntu amd64 quantal 12.10 went well on my end. Created a persistent USB with startup disk creator ran it awhile installed my b43 firmware got wifi working then decided I would go for a hardware install on my old trusty Dell D620.  Slick and clean..
hmmm.. qa-tracker not recording 12.10 testing yet.. 

As usual the first pre-Alpha seems to be pretty good for me. All I noticed was 12.04 in the ubiquity slide show that is pretty normal in Alpha too.

Out

---

### Post by sammiev on 2012-05-08
Need the weekend to play. :) Maybe a fresh build by then! :popcorn:

---

### Post by Miykel on 2012-05-09
G'Day guys, after many dramas I finally got QQ installed off the disc I burned from the iso, had a lot of problems with grub, could not find the install, had to use boot repair.iso to repair grub then I couldn't load the nVidia drivers, ended up up gradeing Xorg server and relevant nVidia drivers, took most of the afternoon but all seems good now.
 I'm amazed at how much you guys have taught me, many thanks
Regards Miykel

---

### Post by philinux on 2012-05-10
> **Mathor said:**
> Hope everyone has been enjoying their UDS thus far. As my first, it's pretty amazing.

I'm surprised this is up this early, 

Get testing!

Indeed. MS and some devs made this point at UDS.

[http://iloveubuntu.net/ubuntu-1210-daily-builds-available-download](http://iloveubuntu.net/ubuntu-1210-daily-builds-available-download)

---

### Post by pressureman on 2012-05-11
Daily alternate ([http://cdimage.ubuntulinux.org/daily/current/](http://cdimage.ubuntulinux.org/daily/current/)) are still precise images.

---

