---
title: "Bugs to the left of me, borkage to the right, here I am ....................."
date: 2014-08-02
forum: Ubuntu, Linux and OS Chat
---

### Post by kansasnoob on 2014-08-02
It's probably evil to laugh at a time like this, but I couldn't help but laugh when *Stuck in the Middle With You* came on while typing this reply:

[http://ubuntuforums.org/showthread.php?t=2220264&page=4&p=13088662#post13088662](http://ubuntuforums.org/showthread.php?t=2220264&page=4&p=13088662#post13088662)

**First** came all of the reported borkage related to [Precise HWE EOL]("https://wiki.ubuntu.com/1204_HWE_EOL") upgrades which could largely have been avoided by adding a simple suggestion to the [Ubuntu download page ]("http://www.ubuntu.com/download/desktop")when 12.04.2, 12.04.3, and 12.04.4 were released:

*Users not requiring the absolute latest hardware support may prefer using the archived 12.04.1 installation media to avoid [HWE EOL]("https://wiki.ubuntu.com/1204_HWE_EOL") upgrades. Please take a moment to review [the LTS hardware enablement policy]("https://wiki.ubuntu.com/Kernel/LTSEnablementStack").*

I did in fact add a task to my to-do list for November to file a documentation bug report between the release of 14.10 and 14.04.2 so we can hopefully avoid some of these problems when we encounter Trusty HWE EOL shortly before the release of 14.04.5.

**Second** came discovering that both [Precise -> Trusty]("https://bugs.launchpad.net/ubuntu/+source/ubuntu-release-upgrader/+bug/1347964") and [Saucy -> Trusty]("https://bugs.launchpad.net/ubuntu/+source/apt/+bug/1347721") release upgrades were borked during [14.04.1 iso/upgrade testing]("http://iso.qa.ubuntu.com/qatracker/milestones/318/builds/73744/testcases/1635/results"). This is AFAIK why users are not receiving automated upgrade notifications ATM. And, yes, Trusty upgrades are [still somewhat borked]("https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1351414").

**Third**, either of those two situations may necessitate the need for reinstallation which may lead to disastrous consequences due to [this installer bug]("https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1265192") :(

So help me with some lyrics :lolflag:

---

### Post by sudodus on 2014-08-02
Yes particularly if I was eager to get the 'latest and greatest' and fell into a black hole (black screen or even worse, wiped the family photos).

So it is more important than ever to recommend a ***good and tested backup*** of the whole hard disk drive or at least of all personal files

[https://help.ubuntu.com/community/BackupYourSystem](https://help.ubuntu.com/community/BackupYourSystem)
[http://clonezilla.org](http://clonezilla.org) or some Windows tool for Windows if you have a dual boot system.

and to [***try*** Ubuntu (Kubuntu, Lubuntu, Xubuntu,  ...) before installing it]("http://ubuntuforums.org/showthread.php?t=2230389")

*Lyrics*:

"Tough guys never backup their data, the do the work twice instead"
"Do you drive your car without a safety belt? Then install a new version without backup and without trying it live!"

---

### Post by ventrical on 2014-08-02
@noob

This bug:

[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1265192](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1265192)

Not happening here (with most recent ubtuntu&kubuntu trusty.)[I downloaded both full isos yesterday.]

Will try again.

*note* Also .. with Windows 8 (if already installed)  I always have to use GRub Rescue after I install ubuntu alongside. It's no big deal.

---

### Post by sudodus on 2014-08-02
> **ventrical said:**
> @noob

This bug:

[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1265192](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1265192)

Not happening here (with most recent ubtuntu&kubuntu trusty.)[I downloaded both full isos yesterday.]

Will try again.

*note* Also .. with Windows 8 (if already installed)  I always have to use GRub Rescue after I install ubuntu alongside. It's no big deal.

Let us hope that bug is squashed :-D but maybe your system is somehow different from those suffering from it. Is Windows installed with UEFI? Are you running the Ubuntu installer in UEFI or BIOS mode?

---

### Post by ventrical on 2014-08-02
> **sudodus said:**
> Yes particularly if I was eager to get the 'latest and greatest' and fell into a black hole (black screen or even worse, wiped the family photos).

So it is more important than ever to recommend a ***good and tested backup*** of the whole hard disk drive or at least of all personal files

[https://help.ubuntu.com/community/BackupYourSystem](https://help.ubuntu.com/community/BackupYourSystem)
[http://clonezilla.org](http://clonezilla.org) or some Windows tool for Windows if you have a dual boot system.

and to [***try*** Ubuntu (Kubuntu, Lubuntu, Xubuntu,  ...) before installing it]("http://ubuntuforums.org/showthread.php?t=2230389")

*Lyrics*:

"Tough guys never backup their data, the do the work twice instead"
"Do you drive your car without a safety belt? Then install a new version without backup and without trying it live!"

  I just grab all my newly created vids, pics and docs and place them on another storage device. it is so much easier. With the hoard of hdds and USBs I have + with my USB to SATA/IDE bridge it's a cinch.

Regards..

---

### Post by sudodus on 2014-08-02
> **ventrical said:**
> I just grab all my newly created vids, pics and docs and place them on another storage device. it is so much easier. With the hoard of hdds and USBs I have + with my USB to SATA/IDE bridge it's a cinch.

Regards..

This is a good idea. I also do it, but I also have a separate backup drive, that is only running when I synchronize the multimedia partition with the backup drive.

---

### Post by kansasnoob on 2014-08-02
> **ventrical said:**
> @noob

This bug:

[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1265192](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1265192)

Not happening here (with most recent ubtuntu&kubuntu trusty.)[I downloaded both full isos yesterday.]

Will try again.

*note* Also .. with Windows 8 (if already installed)  I always have to use GRub Rescue after I install ubuntu alongside. It's no big deal.

I think someone suggested that the Kubuntu installer is somehow more intuitive than it's Ubuntu counterpart. No doubt it's not easy to reproduce so it's all that much harder for the devs to fix.

---

### Post by ventrical on 2014-08-02
> **sudodus said:**
> Let us hope that bug is squashed :-D but maybe your system is somehow different from those suffering from it. Is Windows installed with UEFI? Are you running the Ubuntu installer in UEFI or BIOS mode?

Ahhh .... I always disable UEFI before installing Windows 8. But once, during testing, I had UEFI on and  GRub Rescue fixed it.  I have been super busy as of late but now I have time to test this.

 btw .. I have 10 active ubuntu towers at various stages of dev, 8 of them running on KVMs.

Regards.

 First to try .. *upgrade*  my Toshiba laptop from 13.10 to latest trusty from July 30 ubuntu-14.04.1-desktop-amd64.iso

---

### Post by ventrical on 2014-08-02
Upgrade from 13/10 to 14.04.1 went fine. I used the 'something else' option. It is a dual boot system with a previous version of trusty already on it. [s] I made one little mistake thought. Not thinking , I inadvertently used a different user name and password and , of course, the result was that all tabs , history were lost( as I think that this is the method one has to use if they want to bring all of their tabs, docs, pics etc.. into the new upgrade.(At least the earlier versions of trusty did this.[/s]

You have to make sure if you are using the 'something else' option to allow it to partition the drive when you want to upgrade any particular install. I missed this step the last time as I am quite sure it should bring in all users. (bu t that test is currently running now).

 [s]So I end up with a virgin install with the exception that it still has all the old kernels from 13.10 still in GRub.[/s]

 The installer DID NOT give me the option to update the 13.10 partition. I had to use 'something else' option.

 As it stands.. I consider this attempt a fail but in Ubuntu's defence I should have used original name/password. So back at a second try!

:)

---

### Post by ventrical on 2014-08-02
*note*

Restoring Previously installed packages...

just wait .. wait ... don't touch that dial..

..geee .. about 5 minutes or better ..

Success!

---

### Post by ventrical on 2014-08-02
> **kansasnoob said:**
> I think someone suggested that the Kubuntu installer is somehow more intuitive than it's Ubuntu counterpart. No doubt it's not easy to reproduce so it's all that much harder for the devs to fix.


@noob and sudodus

 Installed Windows 8 with UEFI. After successful install , stuck in latest ubuntu-trusty desktop .iso. Absolute nightmare!! Can't find any other operating systems when installer comes up!! I went to /something else/ and , yes, it's all there but it is labyrinth of partitions and  it looks to me as if one would have to spend some serious time at the chair.

 Thanks for bringing this up because I was about to set up a demonstration for a large company here in my area.  I'm not sure now if this will work with UEFI disabled. The ENABLED UEFI test case may be the  bug of all bugs ?

Regards..

---

### Post by ventrical on 2014-08-02
> **kansasnoob said:**
> I think someone suggested that the Kubuntu installer is somehow more intuitive than it's Ubuntu counterpart. No doubt it's not easy to reproduce so it's all that much harder for the devs to fix.

Kubuntu will not  work in system with UEFI enabled. At least not here. I get a GRuB menu with three options.

1. Start Kubuntu
2. OEM  Original  Install err sumthing  like that.
3. Check Disk for defects.

The first 2 give me nothing, nadda. Goes nowhere yet it works fine on non UEFI 64bit install.

These are serious bugs with 14.04.1

So there is that stress, that trepedation of whats next to come down the pipe.

Regards..

---

### Post by sudodus on 2014-08-02
Thanks for sharing your results ventrical :-)

---

### Post by kansasnoob on 2014-08-02
> **ventrical said:**
> *note*

Restoring Previously installed packages...

just wait .. wait ... don't touch that dial..

..geee .. about 5 minutes or better ..

Success!

I've seen that step take as long as 30 minutes, particularly if it's searching for packages that it'll never find like PPA stuff. Then when it's done it'll warn that it couldn't reinstall all packages.

---

### Post by kansasnoob on 2014-08-02
> **ventrical said:**
> Kubuntu will not  work in system with UEFI enabled. At least not here. I get a GRuB menu with three options.

1. Start Kubuntu
2. OEM  Original  Install err sumthing  like that.
3. Check Disk for defects.

The first 2 give me nothing, nadda. Goes nowhere yet it works fine on non UEFI 64bit install.

These are serious bugs with 14.04.1

So there is that stress, that trepedation of whats next to come down the pipe.

Regards..

I'd prefer it not working at all to erasing peoples other OS' and data.

---

### Post by ventrical on 2014-08-02
> **kansasnoob said:**
> I'd prefer it not working at all to erasing peoples other OS' and data.


 I am going to try another Win8 install with UEFI with the exception that this time I will set up a partition during the installation process. The Windows 8 installer gives that option from the dvd. Of course this is useless for someone who has already bought a system with Win8 pre-installed.


hrrrmmmnnnn.... I'm going to try an experiment.  I'll let you know later how it turned out ...geeesh em bzy!

---

### Post by ventrical on 2014-08-02
I went 'live' . Used gparted and got this far ... but I couldn't make the 1MB partition but went ahead anyways to install ubuntu-desktop.


......

---

### Post by ventrical on 2014-08-02
Ok.. some partial success.  gparted from 'live' did in fact install the partition. Ubuntu-desktop installed successfully and then re-booted into ubuntu-desktop. I then:

sudo update-grub

and got an error of some sort but it did not detect Windows 8. I shut PC down, rebooted and it boot up into Windows 8. All is well.

Now for Grub Rescue disk!

Keep in mind .. this all being done while UEFI enabled.

who knows what next lol

Regards..

---

### Post by ventrical on 2014-08-02
Grub Rescue gave me complete fail. Windows 8 only will come up.  I know how to fix it. Put the 1MB partition in ...ect... but for complete noobs trying to discover the 'awe' of ubuntu - they'll get lost in the translation right there.

Regards..

---

### Post by sudodus on 2014-08-02
> **ventrical said:**
> Grub Rescue gave me complete fail. Windows 8 only will come up.  I know how to fix it. Put the 1MB partition in ...ect... but for complete noobs trying to discover the 'awe' of ubuntu - they'll get lost in the translation right there.

Regards..

I think this is one of the main reasons why they invented UEFI ;-)

By the way, do you remember that way back in March you tried this system?

[Portable installed system that boots in UEFI as well as in BIOS mode]("http://ubuntuforums.org/showthread.php?t=2213631")

---

### Post by ventrical on 2014-08-02
> **sudodus said:**
> I think this is one of the main reasons why they invented UEFI ;-)

By the way, do you remember that way back in March you tried this system?

[Portable installed system that boots in UEFI as well as in BIOS mode]("http://ubuntuforums.org/showthread.php?t=2213631")



Thanks for the trip down memory lane:) lol... I stuck with it and decided to try and reinstall ubuntu after making that 1MB partition for [Reserved BIOS boot area] which now translates into [biosgrub] in the Ubiquity partitioner. This may mean that this install might  be successful.

  I'll get back to your other thread in a bit.

Regards..

---

### Post by ventrical on 2014-08-02
> **sudodus said:**
> I think this is one of the main reasons why they invented UEFI ;-)

By the way, do you remember that way back in March you tried this system?

[Portable installed system that boots in UEFI as well as in BIOS mode]("http://ubuntuforums.org/showthread.php?t=2213631")

Ubuntu trusty iso is booting fine in UEFI and non UEFI mode on the machine I am currently experimenting with.

Err.. if the devs can take some of your ideas and perhaps incorporate a script-patch so as to recognize the Windows 8 bootloader.. but I see how complex this may be depending on whichever conventions any particualr developer is using.. etc..

---

### Post by ventrical on 2014-08-02
One thing of notice is that when I enabled UEFI on my Intel Board the red light started blinking and stayed blinking on or off. Two short blinks .. then pause .. then 2 short blinks. Now, since [biosgrub] partition was created it stopped.

Any guesses as to why?

---

### Post by ventrical on 2014-08-02
[s] Success! [/s]

```

ventrical@ventrical-desktop:~$ sudo update-grub
[sudo] password for ventrical: 
Generating grub configuration file ...
Found linux image: /boot/vmlinuz-3.13.0-32-generic
Found initrd image: /boot/initrd.img-3.13.0-32-generic
Found Windows Boot Manager on /dev/sda2@/EFI/Microsoft/Boot/bootmgfw.efi
done
ventrical@ventrical-desktop:~$ 


```

Looking back over the past few hours I see how important it is to follow certain recommended procedures. It proves again that , with a little effort, ubutu provides a rock solid solution for difficult work-a-rounds but would behove itself if it were better tailored for the next set.

regards..

edit:

  I really do have to curb my enthusiasm :) Now windows 8 is going through this continuous loop, Hi, were getting ready etc... please wait a few millenia while we prepare your PC .. and then those colours ...

sudo update-grub borked it right up indeed but the way things are going today .. it will probably heal itself overnight :) lol

---

### Post by ventrical on 2014-08-03
Decided to do a long read up of the history of UEFI and it's current status. Being that it is the exploitable security vulnerability that it is I just don't get why people would want to leave their systems open to get bricked. I still got blinking lights on my mobo after yesterday's ordeal. Most lileky an ATM prob. I can fix it but thats a lot of down time. I'm not bellyaching. Just making notes. I am a tester and I epexect these things but this is 2014 and UEIF is like some kind of new dinosaur... err ... or better yet , an elephant in the box.
My apologies for off topic msg.

Regards..

---

### Post by kansasnoob on 2014-08-03
I filed a new bug report regarding upgrade instructions in the release notes:

[https://bugs.launchpad.net/ubuntu-website/+bug/1351826](https://bugs.launchpad.net/ubuntu-website/+bug/1351826)

And added a comment here to stir the pot:

[https://bugs.launchpad.net/ubuntu/+source/ubuntu-release-upgrader/+bug/1347964/comments/16](https://bugs.launchpad.net/ubuntu/+source/ubuntu-release-upgrader/+bug/1347964/comments/16)

---

