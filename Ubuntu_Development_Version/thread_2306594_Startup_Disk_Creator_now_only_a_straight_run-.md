---
title: "Startup Disk Creator now only a straight run-"
date: 2015-12-17
forum: Ubuntu Development Version
---

### Post by ventrical on 2015-12-17
Upon update/upgrade of xenial ubuntu-mate I noticed a ton of usb-creator-gtk updates so I decided to give it a spin. It has only one option now (that I can see) and that is a straight run live copy of the image to USB. There are no other options ie; for persistence. 

Very streamlined indeed.
  Regards..

---

### Post by sudodus on 2015-12-17
Could be that the version by Marc Deslauriers has reached the daily isos now. The idea is to make a version that is very reliable. I have seen no message or correspondence about it at Launchpad or at the Ubuntu Quality mailing list, so I am only guessing.

I'll get the current Lubuntu daily and try it.

Have you installed some proposed or other special repository or ppa?

---

### Post by flocculant on 2015-12-17
[http://changelogs.ubuntu.com/changelogs/pool/main/u/usb-creator/usb-creator_0.3.0/changelog](http://changelogs.ubuntu.com/changelogs/pool/main/u/usb-creator/usb-creator_0.3.0/changelog)

---

### Post by sudodus on 2015-12-17
Indeed, it's new, the GUI is new, and the version by

```
usb-creator-gtk --version
```

is 0.2.23

```
man usb-creator-gtk
``` page is dated Sept 29 - usb-creator-gtk 0.3.0, so things are not ready yet.

---

### Post by ventrical on 2015-12-17
> **sudodus said:**
> Indeed, it's new, the GUI is new, and the version by

```
usb-creator-gtk --version
```

is 0.2.23

```
man usb-creator-gtk
``` page is dated Sept 29 - usb-creator-gtk 0.3.0, so things are not ready yet.

I have proposed enabled so that may explain it.

---

### Post by sudodus on 2015-12-17
It works in Lubuntu xenial i386, can create a working USB drive from 'itself', and also from an Ubuntu xenial amd64 iso iso file, which it should because it is cloning (like dd and mkusb and gnome-disks).

But it cannot connect to ***mini.iso*** (the interface does not accept mini.iso as an input file).

[Bug #1527086 'new Startup Disk Creator cannot clone mini.iso'](https://bugs.launchpad.net/ubuntu/+source/usb-creator/+bug/1527086)

There is probably some kind of logic, that checks if the source file is the correct kind of file, and this logic should accept also Ubuntu mini.iso.

-o-

Please check if you can clone mini.iso, and if you can, tell me how to do it, otherwise please mark 'affects me too' in the bug report.

---

### Post by sudodus on 2015-12-17
> **ventrical said:**
> I have proposed enabled so that may explain it.

Yes, it explains that you have received more updates about it, but it has also arrived in the 'regular' daily iso files (as I can see in the Lubuntu desktop i386 daily iso). Thanks for the heads up :-)

I hope you have time to check if the problem with mini.iso affects you too.

---

### Post by flocculant on 2015-12-17
confirmed that

---

### Post by sudodus on 2015-12-17
Thanks - I think we are reporting this bug early enough to get it squashed.

Otherwise this version looks good.

---

### Post by ventrical on 2015-12-17
> **flocculant said:**
> confirmed that

Thanks for saving  me extra work:)

btw .. @ sudodus .. what is the mini.iso link please.

thanks.

---

### Post by ventrical on 2015-12-17
> **sudodus said:**
> Thanks - I think we are reporting this bug early enough to get it squashed.

Otherwise this version looks good.

 I like the GUI. It is simple. Lets see if time will tell that it is reliable for testing purposes. I assume they dropped persistence widgets because the resources are needed elsewhere.  If we need Advanced Tool we can use mkusb.

Regards..

---

### Post by sudodus on 2015-12-17
You find the released versions here

[***mini.iso***, minimal install, netboot iso]("http://ubuntuforums.org/showthread.php?t=2230389&p=13211730#post13211730")

It can be confusing to search for the xenial mini.iso files, but I think you find them at the following links

[.../xenial/main/installer-i386/current/images/netboot/](http://archive.ubuntu.com/ubuntu/dists/xenial/main/installer-i386/current/images/netboot/)

[.../xenial/main/installer-amd64/current/images/netboot/](http://archive.ubuntu.com/ubuntu/dists/xenial/main/installer-amd64/current/images/netboot/)

---

### Post by sudodus on 2015-12-17
> **ventrical said:**
> I like the GUI. It is simple. Lets see if time will tell that it is reliable for testing purposes. I assume they dropped persistence widgets because the resources are needed elsewhere.  If we need Advanced Tool we can use mkusb.

Regards..

Yes, it is an easy and reliable way to make the Startup Disk Creator reliable :-)

---

### Post by flocculant on 2015-12-17
> **ventrical said:**
> I like the GUI. It is simple. Lets see if time will tell that it is reliable for testing purposes. I assume they dropped persistence widgets because the resources are needed elsewhere.  If we need Advanced Tool we can use mkusb.

Regards..

Looks the same to me. 

I'd assume they dropped the persistence widgets because the app doesn't do it - nothing to do with resources ;)

---

### Post by sgage on 2015-12-17
Just tried the new-style Startup Disk Creator, with a bog-standard iso, and it actually Created a bootable Startup Disk! SDC hadn't worked for me for a long, long time - maybe never. So whatever they did, good! :KS

---

### Post by ventrical on 2015-12-17
> **flocculant said:**
> Looks the same to me. 

I'd assume they dropped the persistence widgets because the app doesn't do it - nothing to do with resources ;)

I am running it on ubuntu-mate. Some small differences.(edit: Probably because I haven't used it in so long I forgot what it looked like) :)

Yes..but I meant that they do not have the resources (developers and keepers) to maintain and fix those problems . So it looks like a 'keep it simple' approach is the soup de jour:)  That may happen (is happening) to other apps as well.

Regards..

---

### Post by sudodus on 2015-12-17
I think it is a 'both and' situation.

1. Making it simple makes it reliable too - we have the hybrid iso files, that allow us to simply clone the iso files - and it is a good idea to take advantage of it.

2. Maybe 95% or 99% of the usage needs no persistence - so it is a waste to provide that in the standard tool, that should be a simple as possible.

3. And yes, I think that there were not enough resources to spend on keeping the old and complicated system working in and between all different versions of syslinux, grub, bios and uefi etc.

---

### Post by ventrical on 2015-12-17
> **sudodus said:**
> I think it is a 'both and' situation.

1. Making it simple makes it reliable too - we have the hybrid iso files, that allow us to simply clone the iso files - and it is a good idea to take advantage of it.

2. Maybe 95% or 99% of the usage needs no persistence - so it is a waste to provide that in the standard tool, that should be a simple as possible.

3. And yes, I think that there were not enough resources to spend on keeping the old and complicated system working in and between all different versions of syslinux, grub, bios and uefi etc.

I absolutely agree 100%! Although I do use mkusb to create persistent USB drives I basically just like to rip of live daily/currents and test them and try hard installs .. etc..

'disks' did an excellent job during the interim. The other positive is that SDC will be more user friendly for new comers and persons wanting to test and join the UDV team. 

Regards..

---

### Post by sudodus on 2015-12-17
For iso-testing I use a persistent live system now, where I update the iso file in place and reboot with the grub-n-iso method. It eliminates the need to copy/clone the file. It is stored in a fast USB 3 pendrive. See this link

[Compressed image file with a persistent live system](https://help.ubuntu.com/community/mkusb/persistent#A3._Compressed_image_file_with_a_persistent_live_system)

I use ***links2update*** to update the daily iso file(s). Very convenient and independent of a master computer.

---

### Post by flocculant on 2015-12-17
> **ventrical said:**
> 
Yes..but I meant that they do not have the resources (developers and keepers) to maintain and fix those problems . So it looks like a 'keep it simple' approach is the soup de jour:)  That may happen (is happening) to other apps as well.

Regards..aah - those resources :) hours not £'s 

> **sudodus said:**
> I think it is a 'both and' situation.

1. Making it simple makes it reliable too - we have the hybrid iso files, that allow us to simply clone the iso files - and it is a good idea to take advantage of it.

2. Maybe 95% or 99% of the usage needs no persistence - so it is a waste to provide that in the standard tool, that should be a simple as possible.

3. And yes, I think that there were not enough resources to spend on keeping the old and complicated system working in and between all different versions of syslinux, grub, bios and uefi etc.All that aside, if the guy who removed persistence (can't remember his name) is true to his word then removal of persistence is only a stop-gap. He said he would look at getting it back.

> **sudodus said:**
> For iso-testing I use a persistent live system now, where I update the iso file in place and reboot with the grub-n-iso method. It eliminates the need to copy/clone the file. It is stored in a fast USB 3 pendrive. See this link

[Compressed image file with a persistent live system](https://help.ubuntu.com/community/mkusb/persistent#A3._Compressed_image_file_with_a_persistent_live_system)

I use ***links2update*** to update the daily iso file(s). Very convenient and independent of a master computer.Can't be assed to daily install, so check the image with vbox and have it looped in grub too, so after a zsync I can check both.

---

### Post by sudodus on 2015-12-17
Marc Deslauriers - he is employed by Canonical but did that job as a volunteer. Yes, he has indicated that removal of persistence is kind of a quick fix, and that he would look into getting it back, but I have not seen any promise (and not expected any promise).

Marc and Nicholas Skaggs have also mentioned that it is feasible to tell people to use specialized tools for special tasks - for example persistent live systems and multibooting with iso files - but those tools will not come with Ubuntu. I think the Ubuntu group will watch the reaction from the users, and after that decide if it is necessary or an advantage at all to add persistence to the SDC.

By the way, he told me today that the problem with the mini.iso will be fixed in version 0.3.1 (the next version) :-)

---

### Post by ventrical on 2015-12-17
> **sudodus said:**
> Marc Deslauriers - he is employed by Canonical but did that job as a volunteer. Yes, he has indicated that removal of persistence is kind of a quick fix, and that he would look into getting it back, but I have not seen any promise (and not expected any promise).

Marc and Nicholas Skaggs have also mentioned that it is feasible to tell people to use specialized tools for special tasks - for example persistent live systems and multibooting with iso files - but those tools will not come with Ubuntu. I think the Ubuntu group will watch the reaction from the users, and after that decide if it is necessary or an advantage at all to add persistence to the SDC.

By the way, he told me today that the problem with the mini.iso will be fixed in version 0.3.1 (the next version) :-)

The main problem with  persistence, (in these and the most recent cycles) is that they will not keep  when swapping from one PC to another. If you make it , on let's say - a newer machine with Intel graphics and then switch to another PC that is a little older with an older BIOS and then switch  back or switch to yet another machine then I have noticed that there is breakage of some sort or the other which does not seem able to  readily be reconciled. I have noticed this type of breakage using mkusb also .  

  I still have an install of Maveric Meerkat and SDC works just fine from there - but  persistent installs have broken from there also (when switching) but it seems a little more stable. Of course if a persistent made USB stick is used on the original machine that it was created with it will usually work for the most part.

Regards..

edit:

Ok.. now I am off topic :)

---

### Post by sudodus on 2015-12-18
... off topic too:

I have better experience of persistent live systems, maybe because I avoid installing things, that might cause problems. Right now I tested my persistent live system, that I normally run in my Toshiba with Intel i5 for isotesting: I ran it in an old Dell Dimension 4600 desktop with Pentium 4. And I found no bad behaviour (it was much slower than in the Toshiba, but it worked).

I will do some testing during the next few days in order to see the problems you are describing.

---

### Post by ventrical on 2015-12-18
> **sudodus said:**
> ... off topic too:

I have better experience of persistent live systems, maybe because I avoid installing things, that might cause problems. Right now I tested my persistent live system, that I normally run in my Toshiba with Intel i5 for isotesting: I ran it in an old Dell Dimension 4600 desktop with Pentium 4. And I found no bad behaviour (it was much slower than in the Toshiba, but it worked).

I will do some testing during the next few days in order to see the problems you are describing.

Thanks. Time permitting I will try to present you with a more detailed and documented case in one of the tutorial forums you have created.

Regards..

---

### Post by sudodus on 2015-12-19
The SDC can use mini.iso now, it was fixed very quickly :-)

But I found a new bug, [Bug #1527900, SDC cannot fetch iso files from a directory with non-standard characters](https://bugs.launchpad.net/ubuntu/+source/usb-creator/+bug/1527900)

Using Swedish, the 'Downloads' folder is named 'Hämtningar', and the SDC cannot fetch files from that folder, probably because of the non-standard character ä (a-umlaut). I suppose there are similar problems with other non-standard characters, that might appear when other languages are used.

Please check it: make a directory with some non-standard character (umlaut or other special character), put an Ubuntu family iso-file into it, and try to use the SDC to clone it to a USB pendrive. If it affects you too, please mark it in the bug report to make the bug confirmed.

---

### Post by mörgæs on 2016-01-26
According to the bug report it's fixed now.
Thanks for reporting it, sudodus.

---

### Post by MikeMecanic on 2016-01-26
SDC works fine here.  I'm using it since at least 2 mounts (every Sunday in Kernel 4.4 cycle)) and it works in all flavors that Iv'e test so far.  I also have Proposed enable and there is an update related to USB that I'm not getting because it's not enable.  Never try to enable it and when it show up first is was in grey.

---

