---
title: "Migrating to DMRAID after installation ?"
date: 2008-07-10
forum: Server Platforms
---

### Post by PlexorAB on 2008-07-10
I have a perfect running Ubuntu Server 8.04 that i spent alot of time configuring things on. It's running on a Fujitsu-Siemens Econel 100 S2 server with onboard RAID. I created a RAID-1 logical volume and installed Ubuntu on it (at least i thought so). Now when i reboot i sometimes seems to boot from the second harddisk in what i thought was the RAID-1 volume. After reading some posts here i understand that i should had installed DMRAID first before i installed Ubuntu. So the questions is:

Is there a way to migrate to DMRAID now, or do i have to reinstall Ubuntu again?

/PlexorAB

---

### Post by fjgaude on 2008-07-10
I've run **mdraid** before, don't now, and I never installed it before installing Ubuntu, how could you?

If you have **grub** on both drives you should boot from one of them.

We don't know anything about your system. What does **sudo fdisk -l** show?

How do you mount the raid1 array?

---

### Post by jaakan on 2008-07-15
> **PlexorAB said:**
> I have a perfect running Ubuntu Server 8.04 that i spent alot of time configuring things on. It's running on a Fujitsu-Siemens Econel 100 S2 server with onboard RAID. I created a RAID-1 logical volume and installed Ubuntu on it (at least i thought so). Now when i reboot i sometimes seems to boot from the second harddisk in what i thought was the RAID-1 volume. After reading some posts here i understand that i should had installed DMRAID first before i installed Ubuntu. So the questions is:

Is there a way to migrate to DMRAID now, or do i have to reinstall Ubuntu again?

/PlexorAB

Your better off backing up your data and reinstalling.

Give this a try
[https://help.ubuntu.com/community/FakeRaidHowto](https://help.ubuntu.com/community/FakeRaidHowto)

Sounds like installing 8.10 on RAID could/will be even easier. I'm hoping for "WILL" be easier than that how-to!

---

