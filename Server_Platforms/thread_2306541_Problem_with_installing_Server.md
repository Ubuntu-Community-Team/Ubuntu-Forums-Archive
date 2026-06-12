---
title: "Problem with installing Server"
date: 2015-12-16
forum: Server Platforms
---

### Post by John_Stacy on 2015-12-16
All,
I have a HP Proliant DL380 server.. its about 5 years old. anyways I am re-provisioning it so that I can run Ubuntu on it however I keep running into a problem during the partitioning phase. The server has a built in SATA Raid controller and is currently configured in a RAID 1 configuration. During the disk detection process it sees that there is a SATA RAID configurations and asks to activate them... I say yes and move on to the partitioning stage when it gives me the overview of the mounting points and partitions it gives me only 3 options. Configure ISCSI Volumes, Undo Changes to Partitions, and Finish partitioning and write changes to disk.

When I select to write to disk I get an error of "No root file system"

I assume there must be some incompatibility with Ubuntu and the SATA RAID Controller or the driver in Ubuntu for that particular controller however even in advance mode I do not see where I have the option to inject a driver...

Any advice on how to get past the error so I can continue with the installation would be great.

Thanks!

---

### Post by slickymaster on 2015-12-16
Hi John_Stacy, welcome to the forums.

I moved your thread to the **Server Platforms** sub-forum, which is the proper venue for it and where helpfully your chances of receiving the appropriate help increase.

---

### Post by darkod on 2015-12-16
It does not show a disk at all? Maybe you simply didn't partition it and specified a mount point?

Anyway, if the built in raid is fakeraid I would investigate how to completely disable it (flashing FW if necessary) and use mdadm SW raid. Much better option compared to fakeraid.

If you have dedicated HW raid card you might decide to use it.

---

### Post by SeijiSensei on 2015-12-16
What RAID card?  Many of them are supported natively in Linux, but so-called "fakeraid" cards require an operating system driver that may only exist for Windows.

A Dell server I maintain uses the SAS driver, which is probably the most common hardware RAID protocol.  We installed CentOS on it, not Ubuntu, and the device was recognized immediately and treated as a single drive, /dev/sda.  I also gave Ubuntu a try at the time, and I believe it also saw the device.  Since Ubuntu is based on Debian, I suggest taking a look at this page: [https://wiki.debian.org/LinuxRaidForAdmins](https://wiki.debian.org/LinuxRaidForAdmins)

Are you trying to retrieve existing partitions or start from scratch?  If the latter, how does the array appear if you choose the manual partitioning step during installation?

---

### Post by John_Stacy on 2015-12-16
It's a hardware RAID running on a Intel 82801GR SATA RAID Controller. As for what I am trying to accomplish. I am trying to deploy Ubuntu from scratch on the server. The server use to be a Windows server and it does still have the windows partitions on it but figured the installer would let me wipe those before laying down new partitions...

---

### Post by darkod on 2015-12-16
Usually the OS would not be aware of a HW raid. Each array would be presented to the OS as single disk, regardless of the number of members in the array.
Telling you it has found raid and asking to activate it sounds more like fakeraid. It doesn't matter much if it's a separate card or not, it matters how the card works.
Unless you are 100% sure it is HW raid, I would investigate in detail the card spec and performance to make sure you know what you will be using and make the best decision.

Also do a search for that specific card model and chipset and ubuntu server installation to see if you can find some advice...

---

### Post by SeijiSensei on 2015-12-16
I'd see if CentOS 7 will work with that device before investing a lot of time and effort in Ubuntu.  Intel distributes a [driver]("https://downloadcenter.intel.com/download/25551/ESRT2-RAID-driver-for-Linux-") for that device that works with SUSE and RedHat, and thus CentOS, but it's not packaged for Ubuntu.  A quick scan through /lib/modules/`uname -r`/kernel/drivers on a 14.04 machine doesn't show it there, nor does "locate esrt".  Maybe a more thorough search might find it.

---

