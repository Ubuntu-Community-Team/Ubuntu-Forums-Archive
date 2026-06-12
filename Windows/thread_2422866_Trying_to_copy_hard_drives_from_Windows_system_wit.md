---
title: "Trying to copy hard drives from Windows system with corrupt intelide.sys file"
date: 2019-07-14
forum: Windows
---

### Post by toodoperecords on 2019-07-14
Long story short my windows pc is no longer booting because of a corrupt intelide.sys file in the system32 folder causing it to go into a repair loop. A friend of mine suggested I use a bootable usb with Linux on it to copy my hard drives to an external before putting a fresh version of windows on my PC. I ordered a USB with 15 versions of Linux in order to do this because I don’t have a second computer. I’m trying to copy all 3 of my drives, so I started with the smallest one which is 250 GB. I’m basically just highlighting all the folders and copying them over to the usb external drive, but it keeps stopping somewhere in the middle of transferring. When it stops moving the only thing I can do is reboot to get it to copy again because if I don’t nothing happens when I copy them a second time after it hangs. I’ve tried using the Ubuntu first, then I tried the Fedora, and now I’m trying Zorin and all three hang during transfer and never finish. I’m wondering if I’m over looking something or if perhaps there is a more reliable way of copying these files or a better distribution to use to do this. I do not have much experience using Linux only once before this in a high school programming class.

---

### Post by coffeecat on 2019-07-14
Welcome to the forum.

As this is a Windows problem, and as I believe you are unlikely to succeed with a Linux live USB, I've moved this to the Windows sub-forum. I'll replace your thread title with something more suitable as soon as I have posted.

Health warning with what follows: I haven't used Windows for years.

My guess is that you are using Windows 10, which employs a hybrid shutdown/hibernation/pseudo-fast-startup franken-abomination. Which would mean that the filesystems on the hard drives are not in a state that can be copied by a Linux system. Hence my belief that trying this with a Linux USB is not a productive idea. But maybe someone with more recent experience of Windows will be able to offer a different view, in which case I will gladly defer.

Have you tried a Windows forum? I believe there are bootable utilities designed for repairing Windows systems, but I have no direct or detailed knowledge of them. Perhaps someone on a Windows forum  would be able to point you to one.

Good luck.

---

### Post by westie457 on 2019-07-14
This is probably the easiest and quickest way to fix the issue.   [https://neosmart.net/wiki/boot-critical-file-is-corrupt/](https://neosmart.net/wiki/boot-critical-file-is-corrupt/)

If you choose to continue fixing this by using a Linux USB it will be a little bit harder.

---

### Post by CharlesA on 2019-07-14
Are you getting I/O errors when trying to copy the files? That's the only reason I can think of that would cause a Linux OS to bomb out.

Assuming you have an external drive that is large enough to hold raw disk images, you could look into using [ddrescue]("https://www.forensicswiki.org/wiki/Ddrescue") to image the entire drive and not choke on I/O or read errors.

Do you have a backup of the data on this drive minus the OS?

---

### Post by toodoperecords on 2019-07-16
I figured out why it was hanging it was because it wasn’t able to move “special files” and I was able to get around this issue by moving the folders pretty much one by one from each drive and successfully backed up all of my data. Now I want to run an windows startup disc to fix the operating system, but I’m not sure which edition or architecture disc I need to run to do this and that seems to be important. Is there any way to find windows system info without being able to boot into windows? That way I can ensure I’m using the right disc.

---

### Post by CharlesA on 2019-07-16
> **toodoperecords said:**
> I figured out why it was hanging it was because it wasn’t able to move “special files” and I was able to get around this issue by moving the folders pretty much one by one from each drive and successfully backed up all of my data. Now I want to run an windows startup disc to fix the operating system, but I’m not sure which edition or architecture disc I need to run to do this and that seems to be important. Is there any way to find windows system info without being able to boot into windows? That way I can ensure I’m using the right disc.

This might work, but I've never tried it.

[https://superuser.com/questions/939150/how-to-identify-the-windows-version-of-a-dead-install-from-linux-by-having-acces](https://superuser.com/questions/939150/how-to-identify-the-windows-version-of-a-dead-install-from-linux-by-having-acces)

---

