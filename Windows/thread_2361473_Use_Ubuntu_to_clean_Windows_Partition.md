---
title: "Use Ubuntu to clean Windows Partition"
date: 2017-05-17
forum: Windows
---

### Post by thewhitewolverine on 2017-05-17
Hi
Windows does not boot 80% of the times when I boot through grub. It shows the purple grub screen with periodical cuts or freezes. And the 20% of the times that it does boot, BSOD loop occurs. Is it a problem with grub? Is there a way I can scan my windows partition for virus using Ubuntu?

---

### Post by howefield on 2017-05-17
Thread moved to the "*Windows*" forum.

If you have an anti virus application installed in your Ubuntu partition then yes, you could scan the Windows partition from it but I'd suggest downloading a bootable anti virus solution, Windows Defender Offline for example but there are a ton of others.

Is the boot problem restricted to booting Windows ?

---

### Post by thewhitewolverine on 2017-05-17
Yes
Ubuntu boots fine.
And about the bootable anti virus 
can i make it usb bootable using ubuntu?
Which software would i have to use to do so? ( I have no idea about the softwares in Ubuntu)

---

### Post by howefield on 2017-05-17
> **thewhitewolverine said:**
> Ubuntu boots fine.

I should also have asked if the issue started as soon as you installed Ubuntu or is it a recent problem, if recent nothing that you can think of that could have precipitated it ?

> And about the bootable anti virus 
can i make it usb bootable using ubuntu?

Yes, in most cases you would download an image and "burn" to optical media or more likely a USB stick.

> Which software would i have to use to do so? ( I have no idea about the softwares in Ubuntu)

Most of the options that you have would consider have media creation steps outlined on their web page. If you need to burn an image in Ubuntu I'd recommend xfburn.

Do you have a preferred anti virus vendor ?

---

### Post by thewhitewolverine on 2017-05-17
The issue started with the latest Windows Updates (not related at all with Ubuntu)
I am suspecting virus corrupting my partition
I prefer Malwarebytes. But the problem is I can't find an image of it anywhere.
I am looking online for solutions.
But if you have any do tell me.
And thanks for your help so far.

---

### Post by howefield on 2017-05-17
> **thewhitewolverine said:**
> The issue started with the latest Windows Updates (not related at all with Ubuntu)

Sounds more likely that this is the cause rather than a virus. I'd suggest creating a new thread entitled something like "Windows won't boot after update - broken grub" or along those lines.

> I am looking online for solutions.

I have used the Kaspersky live media in the past, details and download links from [https://support.kaspersky.com/4162](https://support.kaspersky.com/4162)

As I mentioned there are many others, eg [Windows Defender Offline]("https://support.microsoft.com/en-us/help/17466/windows-defender-offline-help-protect-my-pc"). Not endorsing these particular solutions only mention as I have used in the past.

---

### Post by thewhitewolverine on 2017-05-17
Thanks
I have one last query.
I had partitioned about 157 (default) gB for installation of Ubuntu 16.04. However, after installation, Ubuntu shows its partition to have only 1.0 Gb of free space. How to solve this?

---

### Post by howefield on 2017-05-17
Well, this sounds like the stuff for a separate thread, but a screenshot of how gparted sees the disk/partitions might be helpful. Is the Ubuntu installation encrypted or LVM by any chance ?

---

