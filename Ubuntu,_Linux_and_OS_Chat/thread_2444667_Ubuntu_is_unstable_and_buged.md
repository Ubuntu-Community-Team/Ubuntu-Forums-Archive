---
title: "Ubuntu is unstable and buged"
date: 2020-06-02
forum: Ubuntu, Linux and OS Chat
---

### Post by empleat on 2020-06-02
This system is crap... when you copy something on high-end pc, system is freezing. Or sometimes, it won't even finish... Live-usb freezes, after a same period approximately. This system is joke... I am done with this crap, getting some other distro pffff...

---

### Post by CelticWarrior on 2020-06-02
No, it's usually fine provided all the required drivers are installed, namely proprietary drivers for Nvidia graphics.
And often the hardware needs proper settings in UEFI and/or an updated UEFI itself, firmware updates for SSDs...

Knowledgeable users make the most of it. Those who rant showing off their limited knowledge either learn or better stick with Windows.

---

### Post by MoebusNet on 2020-06-02
That's why there are numerous distro's - what suits one may not suit another. I do have to notice, though, that as a new user you don't ask for help. You just flame and move on. That's OK, best of luck whatever you wind up with.

---

### Post by QIII on 2020-06-02
You have based your assessment on a sample size of one.  That is called a hasty generalization.  There used to be a common saying that put the definition succinctly:  "All *<insert some distinctive group here> *walk in single file.  At least the one I saw did."

It may be that your particular installation is corrupt, that you have modified config files incorrectly, installed third-party software, have hardware issues ... etc.

Have your support requests provided answers?  If not, did you bump them to get more responses?

---

### Post by poorguy on 2020-06-04
> **empleat said:**
> This system is crap... when you copy something on high-end pc, system is freezing. Or sometimes, it won't even finish... Live-usb freezes, after a same period approximately. This system is joke... 

Without **the willingness to learn** **the** **simple basic Linux knowledge** prior to installing Linux the new user will be unable to **properly install **and **update **and **configure** their new Linux install for a first good Linux experiance.

Failure to do this will undoubtedly result in a bad first Linux experience.

> **empleat said:**
> I am done with this crap, getting some other distro pffff...

Another distro will not be any different without **the willingness to learn the** [B]simple basic Linux knowledge needed prior to installing.


[/B]A good read.[URL="http://linux.oneandoneis2.org/LNW.htm"]

http://linux.oneandoneis2.org/LNW.htm[/URL]

---

### Post by TheFu on 2020-06-04
There is a learning curve with every OS.  People forget that they had similar effort with all new things.
It is easy to become frustrated in the beginning because things we think we know from other OSes doesn't apply anymore.  With any Linux distro, you may not be around others using it often enough to see what's possible.

We can assure you that Ubuntu isn't "buged" and is highly stable for most people. You just have to accept that learning any new system takes time AND effort.  One of my systems has been running 16 days:
```
$ uptime 
 09:24:37 up 16 days,
```

Like any worthwhile endeavor, you get back what you put in.  If you don't have the desire or time to learn, then staying with the OS previously being used would make more sense?  Nothing wrong with that.

OTOH, if you just let some frustration get the best of you, we understand. Everyone gets frustrated.  You should have seem my first 3 weeks on a Mac desktop! ;)  Talk about being frustrated!

---

### Post by kansasnoob on 2020-06-04
> **empleat said:**
> This system is crap... when you copy something on high-end pc, system is freezing. Or sometimes, it won't even finish... Live-usb freezes, after a same period approximately. This system is joke... I am done with this crap, getting some other distro pffff...

Sadly you don't even mention what exact hardware you're using or what version and flavor of Ubuntu you're using. I've personally found Focal (20.04) to be incredibly unstable running anything based of the substructure of GNOME - eg; gvfs, gtk+, nautilus, etc. But I've found both Lubuntu and Kubuntu to be "stable enough", although I'm still running a heavily modified Ubuntu Xenial (16.04) on more than half of the production machines I maintain. I may even have most users of Xenial sign up for Extended Security Maintenance, that's undecided.

BTW I've tried GNOME and other desktop environments using gvfs & gtk+ in other distros and since mid to late 2017 they've all become downright frustrating. So it's not just an Ubuntu or Debian thing. Apparently others have fared better or I'd think GNOME's funding would have suffered enough they'd have gotten the message by now. In my personal case I want to "fall in love" with another desktop / distro like I had with variously (and sometimes heavily) tweaked out-of-box Ubuntu up until about mid to late 2017, but so far that hasn't happened. 

As I said above the closest I've come to "loving" Focal is either using Lubuntu or Kubuntu. Linux Mint's Cinnamon DE also comes close but still I just don't love it :(

---

### Post by Chanath on 2020-06-05
> **poorguy said:**
> Without **the willingness to learn** **the** **simple basic Linux knowledge** prior to installing Linux the new user will be unable to **properly install **and **update **and **configure** their new Linux install for a first good Linux experiance.



Not exactly true. The willingness to learn the "simple basic Linux Knowledge" is not enough. The OP is talking about high end PCs. You need to know how to change, for example, RST to AHCI, why the installer not seeing the nvme drive etc and not everyone is ready to test their luck with their expensive computers.

---

### Post by poorguy on 2020-06-05
> **Chanath said:**
> Not exactly true. The willingness to learn the "simple basic Linux Knowledge" is not enough. The OP is talking about high end PCs. You need to know how to change, for example, RST to AHCI, why the installer not seeing the nvme drive etc and not everyone is ready to test their luck with their expensive computers.

I guess I'm the exception because the first thing I do with anything I own is to find user information and user manuals so that I know and understand what I have and how it works and what it is capable of and what options it offers and how to make any necessary changes if needed.

Perhaps since I do that I take for granted that everyone else does the same.

---

### Post by TheFu on 2020-06-05
> **poorguy said:**
> I guess I'm the exception because the first thing I do with anything I own is to find user information and user manuals so that I know and understand what I have and how it works and what it is capable of and what options it offers and how to make any necessary changes if needed.

Perhaps since I do that I take for granted that everyone else does the same.

Yes, you are the exception.  Most people **wing it**, see how far they can get without any training, especially people who have experience on another system they think applies (cough - Windows) regardless of whether that belief is accurate or not.  

Just think about all the things that Windows expects/does that don't work on any other OS. There are hundreds of things and many would be seen as part of an attempt to setup dual boot.  Just a few:
[LIST]
[*]C: isn't a drive, it is a partition. Mixing "drive" with "partition" means Windows users aren't used to the truth about non-floppy disks.  After all, when was the last time a drive was without any partitioning? Just floppies that I can recall ... well, and a few RAID setups which violate best practices.
[*]Partitioning isn't pushed on Windows. 
[*]Most Windows system come pre-installed with the OS. Linux is almost always installed by the user.
[*]NTFS isn't the only file system. What are ext3, ext4, zfs, btrfs, xfs, jfs, and LVM?
[*]Having to deal with swap files/partitions.
[*]\ vs / (though not as important as it seems; just use / on Windows)
[*]Default BIOS options work, for Windows.
[*]Windows is the only OS, so wiping storage is fine at install.
[*]Having/getting to choose MBR or GPT partitioning.
[*]Getting new GPU drivers from the vendor is good (not on Linux)
[*]The GUI is the OS. The GUI is just another program on Unix/Linux.
[*]The GUI is a special program on Windows. There are 50 GUIs on Unix.
[*]Nothing is case-sensitive. Everything is case-sensitive on Unix.
[*]File permissions don't matter on Windows.
[*]Symbolic and Hard links are used all the time on Unix, but hardly ever on Windows
[*]Looking for setup.exe is expected to install software, though this is finally changing 30 yrs later
[*]Package management is centralized ... well, it was until snaps, flatpaks, AppImages.
[*]Restore points are created for the users. Unix has something called _backups_, which are **not** automatic.
[*]Networked file systems don't support permissions. NFS remote storage behaves just like local storage for permissions (except for snaps, which don't work with NFS).
[/LIST]
Those are off the top of my head.

---

### Post by grahammechanical on 2020-06-05
New users are also unfamiliar with the difference in philosophy/business model between companies like Apple and Microsoft and Linux developers. Linux developers have the freedom to do things differently. This leads to choice. In Linux the user is also a tester. We can report bugs. Indeed we are invited to do so. Linux distributions are never finished in the same sense that an Apple or Microsoft executive would declare their product ready for release.

An effort was made a few years ago by Ubuntu developers to make even the future versions of Ubuntu under development stable. As someone who runs the development version alongside an LTS release I would say that it is rare for the development version to crash or become unusable after being updated. Which is what used to happen.

Linux gives users the greater freedom to experiment or to put it another way, break the system. I myself have learnt how to do that. Which is why I always have more than one install of Ubuntu on my machine and I experiment on the installation I do not mind re-installing.

Regards.

---

### Post by VMC on 2020-06-05
I'm more surprised the OP got as much attention as he did. It was apparent from his post, he had no attention of trouble shooting.

---

### Post by TheFu on 2020-06-05
> **VMC said:**
> I'm more surprised the OP got as much attention as he did. It was apparent from his post, he had no attention of trouble shooting.

And doesn't have any account activity in the last 3 days ... same as the age of this thread.  So we have the choir and priests talking here, no parishioners. ;)

---

### Post by ajgreeny on 2020-06-05
As the last two posters have said, empleat appears to have moved on and has no further interest in his thread.

CLOSED

---

