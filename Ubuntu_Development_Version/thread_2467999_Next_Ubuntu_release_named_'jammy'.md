---
title: "Next Ubuntu release named 'jammy'"
date: 2021-10-15
forum: Ubuntu Development Version
---

### Post by osse7 on 2021-10-15
The first packages are being built for 'jammy jellyfish' :P

[https://www.omgubuntu.co.uk/2021/10/ubuntu-22-04-codename-jammy-jellyfish](https://www.omgubuntu.co.uk/2021/10/ubuntu-22-04-codename-jammy-jellyfish)

---

### Post by hyapp on 2021-10-16
yessss wowwww

---

### Post by zebra2 on 2021-10-17
```

zebra3@zebra3-110-15ISK:~$ inxi1
No LSB modules are available.
Distributor ID:	Ubuntu
Description:	Ubuntu Jammy Jellyfish (development branch)
Release:	22.04
Codename:	jammy
inxi -Sxx
System:
  Host: zebra3-110-15ISK Kernel: 5.13.0-19-generic x86_64 bits: 64 
  compiler: gcc v: 11.2.0 Desktop: GNOME 40.5 tk: GTK 3.24.30 
  wm: gnome-shell dm: GDM3 Distro: Ubuntu 22.04 (Jammy Jellyfish) 
$DESKTOP_SESSION
ubuntu
$XDG_SESSION_TYPE
wayland
GNOME Shell 40.5
Version: 40.5-1ubuntu2
loginctl type
Type=wayland
zebra3@zebra3-110-15ISK:~$ 

```

---

### Post by grahammechanical on 2021-10-18
So, the jammy repositories are now in place. It is off we go!

Regards

---

### Post by zebra2 on 2021-10-19
Oct 19th 
Proposed may present dependency problems.  
Turn off Proposed, refresh cache and then update.

---

### Post by zebra2 on 2021-10-19
Proposed back up.  
October 19th 8am utc4
146mb 356 packages downloaded.

---

### Post by zika on 2021-10-19
```
:~$ lsb_release -a
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu Jammy Jellyfish (development branch)
Release:    22.04
Codename:    jammy
```

---

### Post by ajgreeny on 2021-10-20
I've been running Impish Xubuntu as a VM in KVM/QEMU since it first became available, and as a test I have this evening edited the sources.list file to the jammy, 22.04 repos and upgraded.
So far, and I realise it will not have changed much yet from the impish versions, the system has upgraded and is still running faultlessly.
I am also aware that this may be different from the possible problems of installing from a completely new .iso image file and installing a new OS.
Nevertheless, so far so good.

---

### Post by VMC on 2021-10-21
Yes, I always wait until the first ISO appears then install and *zsync* from there to release.

---

### Post by sudodus on 2021-10-22
The first iso files are published at the ISO tracker. I zsynced the Lubuntu iso file and it works live and persistent live. I have made a jammy version of ppa:mkusb/unstable, that works too. See the attached files.

---

### Post by guiverc on 2021-10-22
Thanks @sudodus

I just updated my system to use *jammy* version of mkusb instead of *impish *, and no longer see any reference to *impish* on `apt update` :)

---

### Post by Joe_Linux on 2021-10-22
Will there be a "Jammy Jellyfish" for the Raspberry PI ?

---

### Post by ajgreeny on 2021-10-23
Is there an iso available to download for jammy or is it a case of editing the sources.list file as I have done.
I have searched but can not find one.
See post #8

---

### Post by guiverc on 2021-10-23
[URL="http://iso.qa.ubuntu.com/qatracker/milestones/429/builds"]> **ajgreeny said:**
> Is there an iso available to download for jammy  or is it a case of editing the sources.list file as I have done.
I have searched but can not find one.
See post #8

[/URL][http://iso.qa.ubuntu.com/qatracker/milestones/429/builds](http://iso.qa.ubuntu.com/qatracker/milestones/429/builds)


ISOs are available, with a number of QA-tests performed already  (one of the first posts I read this morning included pictures of a *live* QA-test using a *jammy* ISO; posted here on UF & elsewhere by @sudodus)

---

### Post by ajgreeny on 2021-10-23
Many thanks guiverc.

That site seems well hidden!

---

### Post by guiverc on 2021-10-23
You can follow the links to cdimage.ubuntu.com.... 

(*I use every chance I get to attempt to push the ISO QA test site & hopefully get more testers, thus the link I provided  :P  *)

---

### Post by mIk3_08 on 2021-10-23
> **osse7 said:**
> The first packages are being built for 'jammy jellyfish' :P
[https://www.omgubuntu.co.uk/2021/10/ubuntu-22-04-codename-jammy-jellyfish](https://www.omgubuntu.co.uk/2021/10/ubuntu-22-04-codename-jammy-jellyfish)
Wow. this is cool. Amazingly cool. Go Ubuntu!

---

### Post by ajgreeny on 2021-10-23
> **guiverc said:**
> You can follow the links to cdimage.ubuntu.com.... 

(*I use every chance I get to attempt to push the ISO QA test site & hopefully get more testers, thus the link I provided  :P  *)
I did not manage to find the jammy version through that site even after trying for some time. I have looked again a minute ago and see it is labelled canary which is a new description as far as I'm aware.

I must have missed that before but no matter, I've now got it and can try an installation from the iso.

---

### Post by zebra2 on 2021-10-23
[http://cdimage.ubuntu.com/daily-live/current/](http://cdimage.ubuntu.com/daily-live/current/)

---

### Post by guiverc on 2021-10-23
> **ajgreeny said:**
> I did not manage to find the jammy version through that site even after trying for some time. I have looked again a minute ago and see it is labelled canary which is a new description as far as I'm aware.

I must have missed that before but no matter, I've now got it and can try an installation from the iso.

This is just FYI - ignore if none of it interests you.  (*I sort of assume this is common knowledge; but I've been QA-testing awhile so it is for me anyway*)

From the link I provided (*which is high up the chain*; as if I'd provided daily links below [http://iso.qa.ubuntu.com/qatracker/milestones/429/builds](http://iso.qa.ubuntu.com/qatracker/milestones/429/builds) they'll become stale when a new *daily* ISO is spun,* my provided link meant navigation was required* *though*)

ie.   if you follow the link for Ubuntu *amd64* desktop you'll end up at (*right now, do this after the next ISO is created and the link will differ*)

[http://iso.qa.ubuntu.com/qatracker/milestones/429/builds/238579/testcases](http://iso.qa.ubuntu.com/qatracker/milestones/429/builds/238579/testcases)

where if you click the "*Link to Download Information*" near the top you'll get

[http://iso.qa.ubuntu.com/qatracker/milestones/429/builds/238579/downloads](http://iso.qa.ubuntu.com/qatracker/milestones/429/builds/238579/downloads)

which includes that day's ISO, ie. 

[http://cdimage.ubuntu.com/daily-live/20211023/jammy-desktop-amd64.iso](http://cdimage.ubuntu.com/daily-live/20211023/jammy-desktop-amd64.iso)

From that file, I'd navigate one step up & you'll get to [https://cdimage.ubuntu.com/daily-live/](https://cdimage.ubuntu.com/daily-live/) where you'll see a /current/ directory which is where my `zsync_jammy` script will download from (*ie. files from [https://cdimage.ubuntu.com/daily-live/current/](https://cdimage.ubuntu.com/daily-live/current/), or it will when I modify the impish script to handle jammy!*).  I also download the .manifest file & depending on the *flavor *I'm downloading my script does a `diff` of the manifest with the prior ISO I'd downloaded to show the differences, so I know where to test, look etc.  *(for Lubuntu it highlights specific package changes too, but that's a special case*)


Also **NOTE: **the **CANARY** build refers to the ISO with the new installer.  It's my belief the canary build still contains an ***impish ***system on it though & not *jammy*, though that'll change sometime soon I suspect.  [https://discourse.ubuntu.com/t/new-desktop-installer-preview-build/24765](https://discourse.ubuntu.com/t/new-desktop-installer-preview-build/24765)

---

### Post by ajgreeny on 2021-10-23
Hmmm!

Confusing isn't it, though as I said, I have now managed to navigate my way through the cdimage.ubuntu.com site again and found the jammy iso for Xubuntu which is what I couldn't find originally.

Thanks for the guide.

---

### Post by ajgreeny on 2021-10-23
I have just installed the current Xubuntu iso that I downloaded earlier today, 23rd Oct 2021 from [https://cdimage.ubuntu.com/xubuntu/daily-live/current/jammy-desktop-amd64.iso](https://cdimage.ubuntu.com/xubuntu/daily-live/current/jammy-desktop-amd64.iso) and have had no problems of any sort.

Success reported at the ISO Tracker site, [https://iso.qa.ubuntu.com/qatracker/milestones/429/builds](https://iso.qa.ubuntu.com/qatracker/milestones/429/builds)

---

### Post by guiverc on 2021-10-23
> **ajgreeny said:**
> I have just installed ...

Success reported at the ISO Tracker site, [https://iso.qa.ubuntu.com/qatracker/milestones/429/builds](https://iso.qa.ubuntu.com/qatracker/milestones/429/builds)

**Thank you** for helping QA-test the next *jammy* release & recording your QA-test.  :P 

I suggest in future you add an **optional** line in the comments section with some details about the hardware.  eg. I use the format 

`make model (cpu, ram, gpu)`

If I was to test on the box I'm using now, it'd be 

```
dell [optiplex] 960 (c2q-q9400, 8gb, amd/ati cedar radeon hd 5000/6000/7350/8350)
```

(*details just from `lshw` which I keep in a text file I just copy/paste from when I QA-test*)

---

### Post by ajgreeny on 2021-10-24
A good point which I thought about after reporting. I don't know if it's possible to edit my report but I'll investigate that and do so if I am able.

FYI, in my case it was done using KVM/QEMU as I had no system available for a bare metal installation. It is how I usually test new distros.

---

### Post by guiverc on 2021-10-24
Yes you can edit reports (*when you can find them!*) and I do see KVM/QEMU mentioned semi-frequently in QA-test reports :)

---

### Post by lammert-nijhof on 2021-11-04
I have installed a number of Virtualbox VM to prepare for the future:

[LIST]
[*]Ubuntu 22.04 on OpenZFS running a nested version of Virtualbox to test my future Host OS. 
[*]Xubuntu 22.04 with all the communication stuff, like Email, torrents, WhatsApp etc. . 
[*]Ubuntu Studio 22.04 to check whether I like the transfer to KDE or stick to 20.04 and XFCE. 
[*]Ubuntu  Mate 22.04 with QEMU/KVM nested on top of Virtualbox of the Host.  Checking whether it is feasible to move from Virtualbox to QEMU/KVM. 
[*]Ubuntu Budgie 22.04 
[*]Windows 11 Pro 
[/LIST]

---

