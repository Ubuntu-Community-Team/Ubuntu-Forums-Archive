---
title: "The 9 month release cycle..."
date: 2009-04-29
forum: Testimonials &amp; Experiences
---

### Post by garythegoth on 2009-04-29
.......Is pretty much what Ive found to be best. Jaunty is still too buggy for any real use yet.

---

### Post by stchman on 2009-04-29
> **garythegoth said:**
> .......Is pretty much what Ive found to be best. Jaunty is still too buggy for any real use yet.

Works fine for me.  What bugs?

---

### Post by cariboo on 2009-04-29
I have it installed on two different computers, with different cpu's and different graphics adaptors. One Nvidia and one Intel. Every thing just worked out of the box.

---

### Post by garythegoth on 2009-04-29
> **stchman said:**
> Works fine for me.  What bugs?

Like the USB Startup Disk Creator freezing when I select an ISO.

Like getting the error message of $Home./dmrc persmissions being ignored.

Like Wireless taking 20 seconds to connect when I turn the pc on to the almost instantaneous connection in Intrepid.

Like the random Firefox crashes.

Like the New Wave theme clashing with Open Office and being unable to read the menu bar.

Theres a few...

---

### Post by pparks1 on 2009-04-29
> **garythegoth said:**
> Like the USB Startup Disk Creator freezing when I select an ISO.

Like getting the error message of $Home./dmrc persmissions being ignored.

Like Wireless taking 20 seconds to connect when I turn the pc on to the almost instantaneous connection in Intrepid.

Like the random Firefox crashes.

Like the New Wave theme clashing with Open Office and being unable to read the menu bar.

Theres a few...


Jaunty has been very good to me.  Running on my work laptop and my home PC without any issues whatsoever.   My wireless connects faster at home and at work with Jaunty than it did with 8.10...not to mention it just worked out the box even before running an update.   My Firefox hasn't crashed 1 time that I am aware of.   And I don't use the New Wave theme, so I haven't experienced anything there.

Guess everybody has a different experience.

---

### Post by garythegoth on 2009-04-29
> **pparks1 said:**
> Jaunty has been very good to me.  Running on my work laptop and my home PC without any issues whatsoever.   My wireless connects faster at home and at work with Jaunty than it did with 8.10...not to mention it just worked out the box even before running an update.   My Firefox hasn't crashed 1 time that I am aware of.   And I don't use the New Wave theme, so I haven't experienced anything there.

Guess everybody has a different experience.

Theres also the fact that there doesnt appear to be an obvious way to format a USB stick, which is ridiculous.

---

### Post by wsonar on 2009-04-29
Many comps all rockin the Jaunty flawlessly :)

---

### Post by pparks1 on 2009-04-29
> **garythegoth said:**
> Theres also the fact that there doesnt appear to be an obvious way to format a USB stick, which is ridiculous.

Do you mean a graphical way to format it?    I would use fdisk and mkfs.ext3 at the command line with a USB drive just like I would an actual hard drive.

Here are some links on the process.
[http://www.cyberciti.biz/faq/howto-format-usb-pen-drive/](http://www.cyberciti.biz/faq/howto-format-usb-pen-drive/)
[http://computingtech.blogspot.com/2008/08/formatting-usb-drive-in-ubuntu.html](http://computingtech.blogspot.com/2008/08/formatting-usb-drive-in-ubuntu.html)

If you are the type that isn't comfortable command line, this thread discussions the use of gparted which will allow you to format it within the Ubuntu GUI
[http://ubuntuforums.org/showthread.php?t=468212](http://ubuntuforums.org/showthread.php?t=468212)

---

### Post by stchman on 2009-04-29
> **garythegoth said:**
> Like the USB Startup Disk Creator freezing when I select an ISO.

Like getting the error message of $Home./dmrc persmissions being ignored.

Like Wireless taking 20 seconds to connect when I turn the pc on to the almost instantaneous connection in Intrepid.

Like the random Firefox crashes.

Like the New Wave theme clashing with Open Office and being unable to read the menu bar.

Theres a few...

I have experienced none of these problems on my Aspire One that runs Jaunty.

- I created an Ubuntu bootable USB flash drive.
- No home permissions problems.
- Wireless on the Atheros card connects moments after I log on.
- Firefox never crashes on ANY of my (5) PCs running Ubuntu.
- Openoffice runs just fine.  Jaunty comes with OO 3.0.1 and I installed the repos for Hardy to install OO 3.0.1.

I guess I am just "lucky".

---

### Post by stchman on 2009-04-29
> **garythegoth said:**
> Theres also the fact that there doesnt appear to be an obvious way to format a USB stick, which is ridiculous.

To format a USB stick make sure you have gparted installed.

```
sudo apt-get install gparted
```

After you fire up gparted you can select what file system to format to(EXT2/3, NTFS, FAT, VFAT).  Actually really easy.

Formatting drives is an administrative task in Linux.

---

### Post by garythegoth on 2009-04-29
> **stchman said:**
> To format a USB stick make sure you have gparted installed.

```
sudo apt-get install gparted
```After you fire up gparted you can select what file system to format to(EXT2/3, NTFS, FAT, VFAT).  Actually really easy.

Formatting drives is an administrative task in Linux.

I am indebted to you my good sir ;P

---

### Post by ukripper on 2009-04-30
> **cariboo907 said:**
> I have it installed on two different computers, with different cpu's and different graphics adaptors. One Nvidia and one Intel. Every thing just worked out of the box.

I have exactly got the same setup and Jaunty is working flawlessly on both NV and intel.:)

---

### Post by Sef on 2009-05-01
> Theres also the fact that there doesnt appear to be an obvious way to format a USB stick, which is ridiculous.

There is GNOME Format  which is available from the repositories.

---

