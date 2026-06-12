---
title: "Ubiquity crashes when installing iso to bare metal, or as VM in KVM/QEMU"
date: 2021-11-16
forum: Ubuntu Development Version
---

### Post by ajgreeny on 2021-11-16
I have tried several times to install the daily-live versions of Xubuntu 22.04 but the ubiquity installer always seems to crash.
I have reported this as requested at the crash and there is now a bug which can be found at [https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1951093](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1951093)

Anyone else tried this with the same result in Xubuntu or any other DE version.

I have used both bare metal and KVM/QEMU virtual machines always with the same result.

---

### Post by oldfred on 2021-11-16
How are you booting ISO.
I always use grub2's loopmount and toram parameter and have to unmount isodevice. The pop-up that asks to unmount partitions does not do anything, and it locks up if isodevice not unmounted.
sudo umount -lrf /isodevice

Have not tried installing Jammy for a couple of weeks.

---

### Post by Frogs Hair on 2021-11-16
I had the same result with Ubuntu Budgie on bare metal. I never even get into the live session.

---

### Post by ajgreeny on 2021-11-16
For the hard metal installs I create a live system USB with the iso using mkusb and can always (so far) boot successfully to a live OS which runs beautifully with no obvious problems.
Fo the KVM1QEMU installation I simply point virt-manager to the iso image file.  This also boots to a good live OS but seems to crash at the same point, just after the file copying operation has completed and the installation proper begins.

Very frustrating but I do have a fully updated and successful instance 22.04 after editing the sources.list file of a VM, again in KVM/QEMU, of 21.10.  It is simply the installer that crashes at present.

---

### Post by Doug S on 2021-11-16
I had the same installation crash problem. At the time, I did not know if [bug #1950132]("https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1950132") was the correct one, and ended up filing [https://bugs.launchpad.net/subiquity/+bug/1950914](https://bugs.launchpad.net/subiquity/+bug/1950914). I have since marked it as a duplicate. I also think that two bugs filed yesterday (i'll find them later) are also duplicates.

What I didn't know before wasting my time, was to first go to the [daily overview page]("http://cdimage.ubuntu.com/cdimage/daily-live/") and look at the date of the stuff in the "current" directory, the one that says "Latest images to have passed any automatic testing; try this first", where I saw the iso files dates 2021.11.05. That one installed fine.

Normally I just go to the [QA tracker page]("http://iso.qa.ubuntu.com/") to get whatever ISO I am looking for, and fill out the test case also. I observe that many of the sever edition pages are obsolete, without an ISO even available.

EDIT 1: Many bugs [here]("https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bugs?orderby=-id&start=0") are the same thing.

EDIT 2: I have been talking about Ubutnu Desktop, whereas this thread was originally about Xubuntu, where the [current directory]("http://cdimage.ubuntu.com/xubuntu/daily-live/current/") shows todays date for the ISOs.

---

### Post by zebra2 on 2021-11-16
Nov 13th Ubuntu 22.04 ISO Legacy Install crashes.  I used Startup Disk Creator. 
Installed Impish ISO, Did not update. Changed repositories to Jammy, Updated, Upgraded. All OK.

---

### Post by pqwoerituytrueiwoq on 2021-11-16
reported this bug the other day

[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1950880](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1950880)

---

### Post by pqwoerituytrueiwoq on 2021-11-16
> **oldfred said:**
> How are you booting ISO.
I always use grub2's loopmount and toram parameter and have to unmount isodevice. The pop-up that asks to unmount partitions does not do anything, and it locks up if isodevice not unmounted.
sudo umount -lrf /isodevice

Have not tried installing Jammy for a couple of weeks.

```

    menuentry "Kubuntu 22.04 Desktop 64bit" --class jammy --class gnu-linux --id jammy {
        set isofile="/iso/Jammy/kubuntu-22.04-desktop-amd64.iso"
        loopback loop $isofile
        linux (loop)/casper/vmlinuz boot=casper iso-scan/filename=$isofile noeject noprompt splash --
        initrd (loop)/casper/initrd
    }

```

i just installed 21.10 and use sed to do in a inline update to sources.list after the installer crashed as soon as it got to apt twice

---

### Post by ajgreeny on 2021-11-19
Just zsynced the most recent iso of Xubuntu and the crash problem is still there, exactly as it was the last time I tried.

This still means that other running the jammy version which I upgraded from 21.10 recently, there is no way (that I know of) to install and test running 22.04 at this time.
The live system appears to run without a problem; it is only the installation that crashes.

---

### Post by Doug S on 2021-11-19
> **ajgreeny said:**
> Just zsynced the most recent iso of Xubuntu and the crash problem is still there, exactly as it was the last time I tried.

This still means that other running the jammy version which I upgraded from 21.10 recently, there is no way (that I know of) to install and test running 22.04 at this time.
The live system appears to run without a problem; it is only the installation that crashes.Agreed, seems to be an ongoing issue. There are now a large number of related bug reports.

---

### Post by ajgreeny on 2021-11-20
Same problem with today's daily iso (20 Nov 2021).

As bob-H says in the bug at [https://bugs.launchpad.net/bugs/1951399](https://bugs.launchpad.net/bugs/1951399) we seem to be trying hard but getting nowhere with this; if we can't install the OS how can we test it?

---

### Post by pqwoerituytrueiwoq on 2021-11-20
only way we can test the os is to upgrade to it, is there a mini.iso? then we could just install the meta package to get as clean of a upgrade as possible

---

### Post by Doug S on 2021-11-20
At this point all we can do is wait. At least the bug reports are more or less sorted out now, and finally realized to all be the same thing. If readers have not done so already, please click on "This bug affects me also" in the now [main bug report]("https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1951399") to increase the heat. I won't even try the daily again until the date of the AMD64 file in the [Ubuntu current directory]("http://cdimage.ubuntu.com/cdimage/daily-live/current/") becomes the date of the day I look. Since we know it is the same root issue for all flavours of Ubuntu, I suggest that others could do the same.

---

### Post by ajgreeny on 2021-11-21
Good idea and I shall be doing the same, though I will keep trying the live session to ensure that it runs well; I'll just not bother to attempt installing until the iso date matches the day of the install attempt.

---

### Post by guiverc on 2021-11-21
For those interested in the issue, refer Norbert's post on [https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1951399](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1951399)

[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1951399/comments/26](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1951399/comments/26)

A workaround is provided too; though if that's too much work; Lubuntu *jammy* still installs :P  (as does Ubuntu Studio...)

*Sorry I couldn't help myself with the Lubuntu ref...  (I'm a Lubuntu team member for those that didn't know...)*

---

### Post by ajgreeny on 2021-11-22
Assuming I have the time I shall try Norbert's workaround later today.

Thanks for pointing us in that direction; it's been difficult to keep up to date with this problem and all of the duplication across all of the different *buntu versions so this is very helpful.

[COLOR="#FF0000"]EDIT:[/COLOR]

Woowhooo!!!

It worked fine installing today's (22 Nov 2021) iso of Xubuntu in KVM/QEMU in UEFI mode, so many thanks are due to Norbert for managing to figure that out.

What we now need is a new iso build that contains the working version of debianutils or the old debianutils_4.11.2_amd64.deb in its place.

---

### Post by VMC on 2021-11-24
It's fixed with today's "2021-11-24 08:32" ISO.

---

### Post by ajgreeny on 2021-11-24
> **VMC said:**
> It's fixed with today's "2021-11-24 08:32" ISO.
But not for all the ISOs of the different DE versions.

I have just zsynced today's iso of Xubuntu-jammy timed at 2021-11-24 02:14 and tried installing it using KVM/QEMU.

Unlike today's Ubuntu iso mentioned above, the Xubuntu ISO still suffers with the crash when installation starts.  I had assumed that all the daily ISOs would now be OK to install but apparently that's not yet the case.

---

### Post by pqwoerituytrueiwoq on 2021-11-25
> **ajgreeny said:**
> But not for all the ISOs of the different DE versions.

I have just zsynced today's iso of Xubuntu-jammy timed at 2021-11-24 02:14 and tried installing it using KVM/QEMU.

Unlike today's Ubuntu iso mentioned above, the Xubuntu ISO still suffers with the crash when installation starts.  I had assumed that all the daily ISOs would now be OK to install but apparently that's not yet the case.
from what i saw in [the bug report](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1951399/comments/35), the xubuntu daily just missed the update for the fix when it was made

---

### Post by ajgreeny on 2021-11-25
> **pqwoerituytrueiwoq said:**
> from what i saw in [the bug report](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1951399/comments/35), the xubuntu daily just missed the update for the fix when it was made
Yes, I saw that on the bug site a short while ago so I'll zsync yesterday's ISO and try again later with today's. 

It sounds as if it has definitely been fixed at last!

Huge thanks to all.

[COLOR="#FF0000"]EDIT[/COLOR]

Yes, it seems to be fixed now and I've installed Xubuntu 22.04 into a newly made partition in dual boot with my main 20.04 system.
Working well at the moment but who knows how it will go between now and April next year.
Time will tell.

---

