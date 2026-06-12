---
title: "Upgrade trouble from 8.04 to 10.04.3"
date: 2011-09-20
forum: Server Platforms
---

### Post by tromboendue on 2011-09-20
I am having trouble upgrading from 8.04 to 10.04.3.  I am updateing thought the update manager.  Once the upgrade finishes I receive the following screen on boot segmentation fault.  I thought my boot loader may be wrong so I edited the boot loader to use the drives UID and I still get the same error.

---

### Post by tromboendue on 2011-09-21
OK I will get one posted here shortly.

---

### Post by tromboendue on 2011-09-21
Here is the screenshot.  Also when I enter rescue mode I am getting the following error: The installer could not find any partitions, so you will not be able to mount a root file system.  this may be caused by the kernel failing to detect your hard disk drive or failing to read the partition table, or the disk may be unpartitioned.  If you wish, you may investigate this from a shell in the installer environment.

---

### Post by arrrghhh on 2011-09-21
> **tromboendue said:**
> Here is the screenshot.  Also when I enter rescue mode I am getting the following error: The installer could not find any partitions, so you will not be able to mount a root file system.  this may be caused by the kernel failing to detect your hard disk drive or failing to read the partition table, or the disk may be unpartitioned.  If you wish, you may investigate this from a shell in the installer environment.

I would boot from a LiveCD and ensure the disks are OK and the UUID's match.

If they don't, you can try changing the fstab entries to their /dev/sdX location as a temporary fix - but they should be updated to match the UUID in the future.

---

### Post by tromboendue on 2011-09-22
> **arrrghhh said:**
> I would boot from a LiveCD and ensure the disks are OK and the UUID's match.

If they don't, you can try changing the fstab entries to their /dev/sdX location as a temporary fix - but they should be updated to match the UUID in the future.


I get this when trying to use the live cd

---

### Post by arrrghhh on 2011-09-22
> **tromboendue said:**
> I get this when trying to use the live cd

This is a Ubuntu Desktop LiveCD...?  I don't think there's a "live" version of the Server Edition.

If you can't even boot a LiveCD, something seems very wrong with your hardware.  Please confirm what exactly you're booting that gives you that error above...

---

### Post by tromboendue on 2011-09-22
Yes I tried the live Desktop CD.  I then tried the Server cd with the resucue broken system option and now I am getting this.  It seems crazy it would be hardware all this is being done in a ESX environment.

---

### Post by arrrghhh on 2011-09-22
> **tromboendue said:**
> Yes I tried the live Desktop CD.  I then tried the Server cd with the resucue broken system option and now I am getting this.  It seems crazy it would be hardware all this is being done in a ESX environment.

You never mentioned ESX.  Do you have other OSes running on this box?  Have you checked the host to ensure the disks are still configured correctly for it?

---

### Post by tromboendue on 2011-09-22
I run windows and Ubuntu on the ESX server.  On this VM there is only one OS.  What I have done is copied the production VM and upgraded it to 8.04.  I then took a snshot and upgraded it to 10.04.3.  After the update completes and I reboot the server is when I get all of these errors.

---

### Post by arrrghhh on 2011-09-22
> **tromboendue said:**
> I run windows and Ubuntu on the ESX server.  On this VM there is only one OS.  What I have done is copied the production VM and upgraded it to 8.04.  I then took a snshot and upgraded it to 10.04.3.  After the update completes and I reboot the server is when I get all of these errors.

So the server didn't start as 8.04...?  What version was it?  Is a complete reinstall out of the question?

Please give us ALL pertinent details.  I don't want to keep making assumptions about your setup.

---

### Post by tromboendue on 2011-09-22
The Server get to 8.04 just fine.  I have a issue going from 8.04 to 10.04.3.  I have tried updating the server though update manager and CD.  I thought about a clean install but the programer that uses the server doesn't want to copy all of the need files and software from the current server to this one.  I would like to do an in place upgrade if possible, but it just seems like the upgrade fails no matter how I do it.

---

### Post by arrrghhh on 2011-09-22
> **tromboendue said:**
> The Server get to 8.04 just fine.  I have a issue going from 8.04 to 10.04.3.  I have tried updating the server though update manager and CD.  I thought about a clean install but the programer that uses the server doesn't want to copy all of the need files and software from the current server to this one.  I would like to do an in place upgrade if possible, but it just seems like the upgrade fails no matter how I do it.

You're still not telling me how this all started.  I need all the details, otherwise I can't help.  Thanks.

---

