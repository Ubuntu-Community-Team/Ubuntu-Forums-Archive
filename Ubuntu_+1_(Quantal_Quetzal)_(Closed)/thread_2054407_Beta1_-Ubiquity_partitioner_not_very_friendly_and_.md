---
title: "Beta1 -Ubiquity partitioner not very friendly and cannot specific partition manually."
date: 2012-09-07
forum: Ubuntu +1 (Quantal Quetzal) (Closed)
---

### Post by philinux on 2012-09-07
[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1047275](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1047275)

These new + and - and the gear for more options is a not a step in the right direction for me. 

Not being able to manually specify my /data partition is a royal pain.

---

### Post by coffeecat on 2012-09-07
> **philinux said:**
> 
Not being able to manually specify my /data partition is a royal pain.

I remember a similar bug appearing at the last moment a few releases ago (Maverick?) and because it was last minute, it was not fixed and survived into the release ISO. The (unsatisfactory) workaround then was to open gedit, type in your path to mountpoint and copy-paste that into the mountpoint field. Does that work with the Beta1 Ubiquity? I haven't downloaded the ISO yet so haven't had a chance to test this myself yet.

---

### Post by ventrical on 2012-09-07
Worked just beautiful here Phill with <SomethingElse>

+Add a Partition
-Delete a Partition

---

### Post by jerrylamos on 2012-09-07
This is a netbook, 250 GB hard drive shared with Windoze...7 and 40 GB USB hard drive for unstable linux code.

Off at the side there was a button with " - + @ " I didnt know what to do with.  Tried it, wanted to resize something I really do NOT ever do that with Ubiquity.  No way will I willing let "Unstable" Ubiquity trash my partition table.  So I didn't.  

As usual Ubiquity anything but intuitive did manage to chase around and select a partition - there must be 15 of them - then what?  No "change" button?  Somehow thrashed around the mouse and whatever and got the drop down, selected the partition, no I do NOT want to resize it, did select format, and "/".  

I'm NOT resizing there's a big warning window comes flashing up as if Ubiquity is about to resize something in spite of my selection NOT to! 

Same thing on my notebook. Seems to me for a "Newbie" that "install" should be lead pipe simple and iron bound. I do wonder if they actually take some neophytes and try Ubiquity out....

Anyway up and running.  Off to chase some bugs.

---

### Post by kansasnoob on 2012-09-07
> These new + and - and the gear for more options is a not a step in the right direction for me.


I beat my brains out on that one:

[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1045799](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1045799)

I still believe some total noob is going to select a partition and click on "-" thinking it'll reduce the size of the partition, whereas it actually deletes the partition.

Sadly I'm just a mere mortal whose opinion doesn't count ;)

---

### Post by skibler on 2012-09-07
Hopefully this isn't too out of place here, but I am also having trouble with the partitioner.

If you want to specify your own partitions, there doesn't seem to be any option to do encryption.

And on my system when I allow the installer to do the partition scheme (Erase disk and install Ubuntu) and select disk encryption, I cannot get past the next screen where you choose a security key. There are no visible text boxes (where you might enter a key) and the "Install Now" button is not accessible. Quit and Back work.

---

### Post by GreatDanton on 2012-09-07
I totally agree. Luckily I have made partitions before I installed OS, but the new icons are indeed confusing.

---

### Post by coffeecat on 2012-09-07
With regard to specify a mountpoint for data partitions.

> **coffeecat said:**
> I haven't downloaded the ISO yet so haven't had a chance to test this myself yet.

I've tested the beta iso live now. You can't paste a custom mountpoint as you could with the buggy Maverick version. With a NTFS data partition it offered me /dos or /windows, neither of which I would use in a thousand years.

I've me-too's philinux's bug report.

---

### Post by skibler on 2012-09-07
I managed to get disk encryption working in the installer by manually destroying the LUKS partitions already on the disk. The installer did not like them, apparently.

---

### Post by philinux on 2012-09-07
> **kansasnoob said:**
> I beat my brains out on that one:

[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1045799](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1045799)

I still believe some total noob is going to select a partition and click on "-" thinking it'll reduce the size of the partition, whereas it actually deletes the partition.

Sadly I'm just a mere mortal whose opinion doesn't count ;)

I did the "-" option on my test machine  and yes it deleted it no warning. But I quit ubiquity and rebooted and all was well. It must do it all as use when u click install.

---

### Post by jerrylamos on 2012-09-07
> **philinux said:**
> I did the "-" option on my test machine  and yes it deleted it no warning. But I quit ubiquity and rebooted and all was well. It must do it all as use when u click install.I had no problem at all with the "change" button.  Anyone have any clue why development replaced it with some cryptic undecipherable symbols?

Just asking....

---

### Post by mc4man on 2012-09-07
> **jerrylamos said:**
> I had no problem at all with the "change" button.  Anyone have any clue why development replaced it with some cryptic undecipherable symbols?

Just asking....
I assume it was drawn from here
[https://docs.google.com/a/canonical.com/document/preview?id=1bZ4yQIVgGaUGSYu3qiUHnQt3ieBZoqunP_DcleHCr3I&pli=1#heading=h.2a1b9d1febe6](https://docs.google.com/a/canonical.com/document/preview?id=1bZ4yQIVgGaUGSYu3qiUHnQt3ieBZoqunP_DcleHCr3I&pli=1#heading=h.2a1b9d1febe6)

---

### Post by cariboo on 2012-09-07
I just did a fresh Beta 1 install, I had to rearrange my partition scheme, and aside from compiz crashing, and the resulting slow down while it gathered information, the partitioner worked the way I expected. I used the ***something else*** option.

---

### Post by sammiev on 2012-09-07
I made a post on the new install options back when it was Daily and thought I would pretend I was a new comer and select the defaults. I did have a place on the HD I want it to go but it took over part of the Windows partition without given me any options at that point. Liked better the way it was. Just my 2 cents.

---

### Post by jerrylamos on 2012-09-07
Two Beta 1 installs I was able to do manual partition, select the partition, double click on the selection and get the drop down to select format type, do format, and "/"

Third install on my 3.3 gHz no way could I double click fast enough.  Could not select ext4 etc.  I could get a blank drop down menu with nothing in it.

So I did a update,dist-upgrade on the live ubuntu.  It was already the latest daily build zsync.  Boring........

Double click worked, drop down menu legible.  I have no clue if it is an Ubiquity problem or a problem handling drop down menus.

Install O.K., now doing the update/dist-upgrade all over again....no clue why updating the live environment wasn't good enough.

BTW, I boot the .iso directly from the hard drive, then un-mount the isodevice.  I don't know how live can update itself and then still have the un-updated packages...

Oh, well, booted and running.

---

### Post by cariboo on 2012-09-07
> **jerrylamos said:**
> Two Beta 1 installs I was able to do manual partition, select the partition, double click on the selection and get the drop down to select format type, do format, and "/"

Third install on my 3.3 gHz no way could I double click fast enough.  Could not select ext4 etc.  I could get a blank drop down menu with nothing in it.

So I did a update,dist-upgrade on the live ubuntu.  It was already the latest daily build zsync.  Boring........

Double click worked, drop down menu legible.  I have no clue if it is an Ubiquity problem or a problem handling drop down menus.

Install O.K., now doing the update/dist-upgrade all over again....no clue why updating the live environment wasn't good enough.

BTW, I boot the .iso directly from the hard drive, then un-mount the isodevice.  I don't know how live can update itself and then still have the un-updated packages...

Oh, well, booted and running.

The Live CD is run in ram and is read only, even if you run if from your hard drive, being read only any changes are lost when the system is shut down.

---

### Post by jerrylamos on 2012-09-08
> **cariboo907 said:**
> The Live CD is run in ram and is read only, even if you run if from your hard drive, being read only any changes are lost when the system is shut down.Live installer is in ram with nothing else available to it, no USB, no CD, the source .iso was on an un-mounted partition so when ubiquity does the install it's got to be using stuff from ram (or else internet - no evidence of downloading).  Somehow live was able to contain both the original beta ubuntu stuff for install while running from updated code which allowed selecting partition & setting ext4, format, /.

Just observations.  It's up and running, and perhaps a hint to other testers if their ubiquity isn't working but live is, try an update to the live.  It worked for me.

---

