---
title: "No language or try install menu screens"
date: 2012-11-08
forum: Ubuntu Development Version
---

### Post by nm_geo on 2012-11-08
Created a persistent USB of the current daily live iso Lubuntu desktop amd64. Booted USB and no screen for language, and no "try or install" menu.  Hitting enter twice and live session goes well. Installed full hard drive and followed with along-side both completed just fine.

[https://bugs.launchpad.net/ubuntu/+source/syslinux/+bug/1076836](https://bugs.launchpad.net/ubuntu/+source/syslinux/+bug/1076836)

bug link attributed to syslinux for now.

---

### Post by nm_geo on 2012-11-09
The issue turns out to be a problem with the SDC in Ubuntu 10.04 not the raring amd64 iso.

---

### Post by jerrylamos on 2012-11-10
This problem has existed for days.

What we do is boot the live raring image
then connect to internet
sudo apt-get update
sudo apt-get dist-upgrade
then do the install to your desired partition.

I've done this on three test pc's O.K.

I have no idea why develompment doesn't do the update, dist-upgrade before posting the .iso to the daily build.

BTW, of course, after booting your new install you need to do a 
sudo apt-get update
sudo apt-get dist-upgrade
all over again.  The install doesn not install the updates to itself.

Scan the Raring forum for additional postings about this.

---

### Post by kuvanito on 2012-11-10
as of this morning 6:00 AM ET the Daily Build for raring i386-32bit dektop has no problems what so ever.
installation is as good as always and usb created with Unetbootin worked as expected,all languages are present.
i see no major difference between 12.10 and 13.04 but it's too early and i know changes are coming any time now. :guitar:

---

### Post by nm_geo on 2012-11-10
> **kuvanito said:**
> as of this morning 6:00 AM ET the Daily between 12.10 and 13.04 but it's too early and i know changes are coming any time now. :guitar:

Yes, I found that my issue that appeared to be with the syslinux in the installation iso was really with the Startup Disk Creator in Ubuntu 10.04.  I will check to see if a bug exists on the SDC in lucid and file one if not. (it will be ignored as lucid approach end-of-life).

I continued with checking the current daily Lubuntu isos from a USB created with the SDC in precise 12.04 and had no issues at all.

I agree kuvanito it is to early to have many changes just yet.  Anyway I am glad the installs are clean as I know lots of work is being done in Ubiquity.

---

### Post by cariboo on 2012-11-10
With Startup Disk Creator being broken in QUantal, I used the following command to create a usb device with the Gnome Remix on it:

```
sudo dd if=/path/to/downloaded.iso of=/dev/diskN bs=1m
```

If you aren't sure what the device id of your usb device is, insert the device, and then open a terminal and type:

```
dmesg
```

the output of the last few lines should look something like this:

```
[ 8336.990588] sd 4:0:0:0: [sdc] Assuming drive cache: write through
[ 8336.992212]  sdc: sdc1
[ 8336.996710] sd 4:0:0:0: [sdc] No Caching mode page present
[ 8336.996715] sd 4:0:0:0: [sdc] Assuming drive cache: write through
[ 8336.996718] sd 4:0:0:0: [sdc] Attached SCSI removable disk
```

In my case the device is sdc, so in the first command it would look like this:

```
sudo dd if=~/Downloads/ubuntu-gnome-12.10-desktop-amd64.iso of=/dev/sdc bs=1m
```

---

### Post by jerrylamos on 2012-11-10
Today's zsync Nov 11 installed normally allowing manual selection of partition.

Now I did boot the .iso direct from the hard drive so I avoided the time and effort and problems of the quantal usb creation.  Someone else can test that.  

Sometimes I resort to unetbootin for usb creation.

More likely, just use precise pangolin 12.04.1 LTS's startup disk creator.  Or meerkat's.  Or lucid's.

BTW, I've got 12.04.1 partitions for backup and recovery, and raring ringtail on 3 test pc's.  No quantal quetzal in sight, except of course raring's mostly still quantal with the same problems I had with quantal...

---

### Post by nm_geo on 2012-11-10
[QUOTE=cariboo907;12347896]With Startup Disk Creator being broken in QUantal, I used the following command to create a usb device with the Gnome Remix on it:

Thanks cariboo907,  I also use the dd command to create bootable USBs as well. In fact that was how I first found out the SDC in Ubuntu lucid 10.04 was faulty. 

Typically though, I want a working persistent USB that allows me to go through the qa-tracker iso install tests and not have to tether my laptop to the ethernet.  That is why I use persistent USBs and I have had good results with the SDC in precise 12.04.

---

### Post by nm_geo on 2012-11-10
> **jerrylamos said:**
> Today's zsync Nov 11 installed normally allowing manual selection of partition.

Now I did boot the .iso direct from the hard drive so I avoided the time and effort and problems of the quantal usb creation.  Someone else can test that.   <snip>

l...

Hi Jerry,
  
I guess I be that somebody.. :)

I logged in about six different tests/installs amd64 and i386 on the Lubuntu raring 13.04 this afternoon all hardware installs on two different laptops.  I am dreading the powerpc iso but my old PowerBook G4 is ready. Maybe I will summons the desire soon.  Maybe not !!

---

