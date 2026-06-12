---
title: "googled but not get it ,,,,,"
date: 2011-10-22
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by raja.genupula on 2011-10-22
Hi i do wanna participate in testing of 12.04 LTS ,where i can get 12.04 LTS ISO ?

Thanks in advance.
Raja

---

### Post by overdrank on 2011-10-22
[Ubuntu +1 (Precise Pangolin)]("http://ubuntuforums.org/forumdisplay.php?f=412") :)

---

### Post by collisionystm on 2011-10-22
> **raja.genupula said:**
> Hi i do wanna participate in testing of 12.04 LTS ,where i can get 12.04 LTS ISO ?

Thanks in advance.
Raja

Try one of these

[http://www.thehosthelpers.com/general-chat/upgrade-ubuntu-11-10-to-12-04-today-1797/](http://www.thehosthelpers.com/general-chat/upgrade-ubuntu-11-10-to-12-04-today-1797/)

---

### Post by nothingspecial on 2011-10-22
Moved to Ubuntu +1

---

### Post by Iowan on 2011-10-22
Check [this]("http://ubuntuforums.org/showthread.php?t=1859235") sticky.

---

### Post by raja.genupula on 2011-10-22
> **overdrank said:**
> [Ubuntu +1 (Precise Pangolin)]("http://ubuntuforums.org/forumdisplay.php?f=412") :)

Hi man , thanks for picking up this but  to be here i need 12.04 right , so where i can get that ISO of 12.04 LTS .

---

### Post by PaulInBHC on 2011-10-22
December 1st

[http://ubuntuforums.org/showthread.php?t=1859118](http://ubuntuforums.org/showthread.php?t=1859118)

---

### Post by paul_in_london on 2011-10-22
There's no iso for 12.04 yet (it's pre-alpha), but assuming you have 11.10 installed you can upgrade to 12.04 "in place".

See this thread:

[http://ubuntuforums.org/showthread.php?t=1860337](http://ubuntuforums.org/showthread.php?t=1860337)

---

### Post by raja.genupula on 2011-10-22
Hi Friends

        Actually i wanna go for a fresh installation of 12.04 and dont wanna go for upgrade to avoid the some problems . please provide me a link for ISO of 12.04 .

Thanks to all.

---

### Post by matt_symes on 2011-10-22
Hi

Raja. Hope you are well.

> Actually i wanna go for a fresh installation of 12.04 and dont  wanna go for upgrade to avoid the some problems . please provide me a  link for ISO of 12.04 .Sorry missed this bit.

I've looked for a daily build but i can't see any yet. Maybe someone else knows.

From an Oneiric install, upgrade to precise.
```

matthew@matthew-Aspire-7540:~$sudo  sed -i 's/oneiric/precise/g' /etc/apt/sources.list
<snip>
matthew@matthew-Aspire-7540:~$sudo apt-get update
<snip>
matthew@matthew-Aspire-7540:~$sudo apt-get upgrade
<snip>
matthew@matthew-Aspire-7540:~$ cat /etc/lsb-release
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=12.04
DISTRIB_CODENAME=precise
DISTRIB_DESCRIPTION="Ubuntu precise (development branch)"
matthew@matthew-Aspire-7540:~$
```Kind regards

---

### Post by raja.genupula on 2011-10-22
@matt_symes

I am doing well and I Hope you too.
SO after looking at all the posts i thought that another fresh installation (already have Xubuntu 11.10 and Ubuntu 11.10) of 11.10 and then doing the things you suggested to me for going to The 12.04 .

I think this is the only thing i can do with out having any problem to my current installation(s). 

Thanks to  matt_symes ,paul_in_london,PaulInBHC,Iowan,nothingspecial,collisionystm & overdrank.

thanks to all once again.

---

### Post by paul_in_london on 2011-10-22
Actually there are daily builds here:

[http://archive.ubuntu.com/ubuntu/dists/precise/main/installer-i386/current/images/netboot/](http://archive.ubuntu.com/ubuntu/dists/precise/main/installer-i386/current/images/netboot/)

[http://archive.ubuntu.com/ubuntu/dists/precise/main/installer-amd64/current/images/netboot/](http://archive.ubuntu.com/ubuntu/dists/precise/main/installer-amd64/current/images/netboot/)

---

### Post by matt_symes on 2011-10-22
Hi

> **paul_in_london said:**
> Actually there are daily builds here:

[http://archive.ubuntu.com/ubuntu/dists/precise/main/installer-i386/current/images/netboot/](http://archive.ubuntu.com/ubuntu/dists/precise/main/installer-i386/current/images/netboot/)

[http://archive.ubuntu.com/ubuntu/dists/precise/main/installer-amd64/current/images/netboot/](http://archive.ubuntu.com/ubuntu/dists/precise/main/installer-amd64/current/images/netboot/)

For the netboot; yes. I also found them for the cloud version but i could not see any for the standard and alternative install.

Kind regards

---

### Post by paul_in_london on 2011-10-22
> **matt_symes said:**
> Hi



For the netboot; yes. I also found them for the cloud version but i could not see any for the standard and alternative install.

Kind regards

Yes, sorry I should have made that clear. I always prefer to install a minimal system and then just add the packages I want.

---

### Post by raja.genupula on 2011-10-22
> **paul_in_london said:**
> Actually there are daily builds here:

[http://archive.ubuntu.com/ubuntu/dists/precise/main/installer-i386/current/images/netboot/](http://archive.ubuntu.com/ubuntu/dists/precise/main/installer-i386/current/images/netboot/)

[http://archive.ubuntu.com/ubuntu/dists/precise/main/installer-amd64/current/images/netboot/](http://archive.ubuntu.com/ubuntu/dists/precise/main/installer-amd64/current/images/netboot/)

yup! but i agree with matt_symes.

---

### Post by ranch hand on 2011-10-22
You will just have to check for the dailies then.
[http://cdimage.ubuntu.com/](http://cdimage.ubuntu.com/)

That is a link to all images from Ubuntu.

The "daily" will be out first and be most reliable.  "The daily live" will be slower to start.

Have no idea when they will start but if you want to get in before Dec. upgrading the version from 11.10 is your most reliable way to do it.  That or the netboot.

Those first dailies have a tendency to be pretty flaky.  No surprise there, they are building an iso that has never been built before.

The netboot I have not used yet, maybe tonight, but they are pretty simple and reliable generally.

---

### Post by jerrylamos on 2011-10-23
Those of us who are running Precise Pangolin mostly do:

- create new test partition - early "unstable" development releases crash, often, ... be prepared to re-install when the test Precise Pangolin borks.  If not installing a bunch of applications 6 GB will usually do.

- Fresh install of new Oneiric Ocelot from
[http://cdimage.ubuntu.com/cdimage/daily-live/current/](http://cdimage.ubuntu.com/cdimage/daily-live/current/)

- remember to back up anything you want to keep, preferably not on that same pc.

- Always have another running partition of something, say oneiric or lucid lynx LTS for recovery purposes.

- Have a bootable CD and/or bootable USB stick with oneiric or ... in case what is borked is Grub2.  That's happened to me already on a failed oneiric install even after release - install got an "error" on "configuring apt" after which the pc would only boot to "grub rescue>" that itself was borked and would not do half the grub rescue commands.  Live CD to the rescue with help from Ubuntu wiki community support for Grub2.

- sudo gedit /etc/apt/sources.list, then replace all oneiric with precise.

- sudo apt-get update, sudo apt-get dist-upgrade

- Cross your fingers and reboot

- do cat /proc/version and see what you've got

- check this forum for any warnings about what's broken

- update daily with sudo apt ... as above

- reboot and see if it will work or not.

Have fun...

Jerry

p.s. A probably bootable precise pangolin .iso will show up in the CD Daily Builds url above at or a little later than the time promised in the Release Schedule thread.  Then check the forums to see if people are having any luck booting it.  Essentially daily builds are sweeping up the current state of lots of packages, throwing them together, may not be compatible....

---

### Post by raja.genupula on 2011-10-23
> **jerrylamos said:**
> Those of us who are running Precise Pangolin mostly do:

- create new test partition - early "unstable" development releases crash, often, ... be prepared to re-install when the test Precise Pangolin borks.  If not installing a bunch of applications 6 GB will usually do.

- Fresh install of new Oneiric Ocelot from
[http://cdimage.ubuntu.com/cdimage/daily-live/current/](http://cdimage.ubuntu.com/cdimage/daily-live/current/)

- remember to back up anything you want to keep, preferably not on that same pc.

- Always have another running partition of something, say oneiric or lucid lynx LTS for recovery purposes.

- Have a bootable CD and/or bootable USB stick with oneiric or ... in case what is borked is Grub2.  That's happened to me already on a failed oneiric install even after release - install got an "error" on "configuring apt" after which the pc would only boot to "grub rescue>" that itself was borked and would not do half the grub rescue commands.  Live CD to the rescue with help from Ubuntu wiki community support for Grub2.

- sudo gedit /etc/apt/sources.list, then replace all oneiric with precise.

- sudo apt-get update, sudo apt-get dist-upgrade

- Cross your fingers and reboot

- do cat /proc/version and see what you've got

- check this forum for any warnings about what's broken

- update daily with sudo apt ... as above

- reboot and see if it will work or not.

Have fun...

Jerry

p.s. A probably bootable precise pangolin .iso will show up in the CD Daily Builds url above at or a little later than the time promised in the Release Schedule thread.  Then check the forums to see if people are having any luck booting it.  Essentially daily builds are sweeping up the current state of lots of packages, throwing them together, may not be compatible....

Yeah thanks for this clear information . But i wanna install it in the same box where i already have Xubuntu 11.10&Ubuntu  11.10 (dont have another box ).

---

### Post by jerrylamos on 2011-10-23
> **raja.genupula said:**
> Yeah thanks for this clear information . But i wanna install it in the same box where i already have Xubuntu 11.10&Ubuntu  11.10 (dont have another box ).

I've got one tower pc with Lucid Lynx, Meerkat, Oneiric, and Pangolin all four bootable and running.

This is a $248 Acer Aspire one netbook, the main 250 GB hard drive has Windozzz...7, Meerkat, and Oneiric on it.  I have seen these netbooks down to $200.

On the netbook I'm testing Pangolin installed on an external USB Hard Drive.  It's got Oneiric and Pangolin on it.  I happened to have a spare 2.5" IDE hard drive laying around, new ones cost starting from $50, and USB enclosures from $10 at Tiger Direct.  Hopefully when Pangolin "unstable" screws up I can recover the USB hard drive using the Oneiric boot, or else boot up Oneiric from the main hard drive and re-build the USB hard drive.

I've also got a notebook again which had Windowzzzz...7, Narwhal and Oneiric on it.  Three bootable images.  Actually during Oneiric Alpha an install screwed up royally and I had to re-install Windoze from four DVD's.  Not fun!  I got it running again with Windoze 7, Narwhal, and Oneiric on it.  

Being chicken, when Precise Pangolin came around, I got out my trusty screwdriver and removed the Windoze 7 2.5" hard drive and replaced it with a spare 2.5" SATA hard drive so I can play around and not blow the Windoze 7 which I haven't been using but would be very useful should I pass the notebook on to someone else.  The replacement drive is 100 GB which I have two 10 GB bootable partitions plus a swap. Testing Pangolin with a 2nd partition with Oneiric for recovery.

The Windoze...7 hard drive is again in a Usb enclosure so I can get at the files on it.  So far I'm chicken to see if Windoze 7 would actually boot from the USB. 

Yes, I'm retired, one of my hobbies is this.

Jerry

---

### Post by raja.genupula on 2011-10-23
> **jerrylamos said:**
> I've got one tower pc with Lucid Lynx, Meerkat, Oneiric, and Pangolin all four bootable and running.

This is a $248 Acer Aspire one netbook, the main 250 GB hard drive has Windozzz...7, Meerkat, and Oneiric on it.  I have seen these netbooks down to $200.

On the netbook I'm testing Pangolin installed on an external USB Hard Drive.  It's got Oneiric and Pangolin on it.  I happened to have a spare 2.5" IDE hard drive laying around, new ones cost starting from $50, and USB enclosures from $10 at Tiger Direct.  Hopefully when Pangolin "unstable" screws up I can recover the USB hard drive using the Oneiric boot, or else boot up Oneiric from the main hard drive and re-build the USB hard drive.

I've also got a notebook again which had Windowzzzz...7, Narwhal and Oneiric on it.  Three bootable images.  Actually during Oneiric Alpha an install screwed up royally and I had to re-install Windoze from four DVD's.  Not fun!  I got it running again with Windoze 7, Narwhal, and Oneiric on it.  

Being chicken, when Precise Pangolin came around, I got out my trusty screwdriver and removed the Windoze 7 2.5" hard drive and replaced it with a spare 2.5" SATA hard drive so I can play around and not blow the Windoze 7 which I haven't been using but would be very useful should I pass the notebook on to someone else.  The replacement drive is 100 GB which I have two 10 GB bootable partitions plus a swap. Testing Pangolin with a 2nd partition with Oneiric for recovery.

The Windoze...7 hard drive is again in a Usb enclosure so I can get at the files on it.  So far I'm chicken to see if Windoze 7 would actually boot from the USB. 

Yes, I'm retired, one of my hobbies is this.

Jerry
Hi Thanks for the reply... 
 But Really large information and making me confuse ...:(.

---

### Post by cariboo on 2011-10-23
The misspelling of Windows so many times doesn't help either.

---

### Post by raja.genupula on 2011-10-23
So i think i can move with 12.04 now with the suggestions from this posts , but still is there any other things that i should take care ?

---

### Post by ikt on 2011-10-23
> **raja.genupula said:**
> Hi i do wanna participate in testing of 12.04 LTS ,where i can get 12.04 LTS ISO ?

Thanks in advance.
Raja

[http://ubuntuforums.org/showpost.php?p=11374867&postcount=11](http://ubuntuforums.org/showpost.php?p=11374867&postcount=11)

If you are able to help get bugs fixed in 11.10 then that should help make 12.04 more stable.

---

### Post by effenberg0x0 on 2011-10-23
> **raja.genupula said:**
> Hi Thanks for the reply... 
 But Really large information and making me confuse ...:(.

Hi Raja, 

The best advice one will give you if you feel like testing Ubuntu Precise Pangolin is to either do it in a **separate machine**, at a **separate HDD **or a** separate HDD partition** in your PC. 

If you test it using one of the ways I mentioned above, you don't face the risk of ending up with no usable PC or losing your data. **DO NOT** **store your important data in the PP machine/disk/partition**. 

There's a good read on using partitions in Ubuntu docs at [https://help.ubuntu.com/community/HowtoPartition](https://help.ubuntu.com/community/HowtoPartition)

Test versions may get unusable, fail to boot, fail to boot to a desktop,  corrupt data, etc. The truth is that no one knows what the next update  will bring when using a test version. You must be skilled enough to  understand bugs, work around them, differentiate a wrong setting  / expected behavior from a real new bug, and hopefully create a viable and correct bug  report from it, something that developers can work with. Otherwise there's little sense to  testing. You won't get support for a testing version. 

Regards,
Effenberg

---

### Post by raja.genupula on 2011-10-24
> **ikt said:**
> [http://ubuntuforums.org/showpost.php?p=11374867&postcount=11](http://ubuntuforums.org/showpost.php?p=11374867&postcount=11)

If you are able to help get bugs fixed in 11.10 then that should help make 12.04 more stable.

yeah this is where i wanna come, but i am not expert so i need some time .

---

### Post by raja.genupula on 2011-10-24
> **effenberg0x0 said:**
> Hi Raja, 

The best advice one will give you if you feel like testing Ubuntu Precise Pangolin is to either do it in a **separate machine**, at a **separate HDD **or a** separate HDD partition** in your PC. 

If you test it using one of the ways I mentioned above, you don't face the risk of ending up with no usable PC or losing your data. **DO NOT** **store your important data in the PP machine/disk/partition**. 

There's a good read on using partitions in Ubuntu docs at [https://help.ubuntu.com/community/HowtoPartition](https://help.ubuntu.com/community/HowtoPartition)

Test versions may get unusable, fail to boot, fail to boot to a desktop,  corrupt data, etc. The truth is that no one knows what the next update  will bring when using a test version. You must be skilled enough to  understand bugs, work around them, differentiate a wrong setting  / expected behavior from a real new bug, and hopefully create a viable and correct bug  report from it, something that developers can work with. Otherwise there's little sense to  testing. You won't get support for a testing version. 

Regards,
Effenberg

Yeah I am not gonna store any of my imp data in 12.04 , Actually my data will stored in separate partition of my system . so i can surely say that i am not gonna worry about data loss .upto now i am just good with reporting them(bugs ) with enough data but not expert with solving the bugs and i wanna be a bug fixer.

---

