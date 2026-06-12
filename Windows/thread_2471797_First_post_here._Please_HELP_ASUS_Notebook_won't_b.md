---
title: "First post here. Please HELP ASUS Notebook won't boot into windows."
date: 2022-02-09
forum: Windows
---

### Post by medicatnoob-818 on 2022-02-09
I don't know what info you guys need. I'm not exactly extremely tech savy. But I learn fast. ASUS laptop/notebook F556UA-EB71. Upon powering on stuck at ASUS logo nothing else not even a loading spinning circle or anything. I've booted from a usb into Boot Repair. I've created a bootinfo summary. I'll pastebin it here: 
[http://paste.ubuntu.com/p/Cjg8VqKkWn/](http://paste.ubuntu.com/p/Cjg8VqKkWn/)
What do I do next? I'm using Boot-Repair which came on my bootable medicat usb I made so far. Help me get back into windows please! I feel like this happened shortly after a windows update. Thanks! Look forward to seeing how this forum works!

---

### Post by howefield on 2022-02-09
Thread moved to the "*Windows*" forum.

---

### Post by tea for one on 2022-02-09
> **medicatnoob-818 said:**
>  Help me get back into windows please! I feel like this happened shortly after a windows update. Thanks! Look forward to seeing how this forum works!
[COLOR="#0000FF"]Line 76[/COLOR] - OS#1:   [COLOR="#FF0000"]Windows XP[/COLOR] (boot) on sda3
Windows XP reached end of life in 2014 and does not receive any updates.
I wonder which update you think prevents your PC from booting?

The best advice is to backup your data, download and install a supported OS and then restore your data.

---

### Post by medicatnoob-818 on 2022-02-10
Wow amazing 'tea for one' thank you! I just created an account here today. I don't know alot but this really helps! You're my first response here. Yeah so that makes sense I think the laptop originally had XP on it. I clicked something to upgrade to windows 10 and shortly after that I believe is when I ran into this issue. Sorry for all the quotations but I could have kept my computer running XP without ever upgrading?? It worked so much better before! Is this why now that I'm using a windows 10 recovery usb to boot from when I try to repair the system automatically it doesn't work? What should I do? Proceed with upgrading to win 10? Or should I go back to XP somehow and how? Thank you so much for your time!

---

### Post by yancek on 2022-02-10
I expect you could have continued using XP but if you used the internet, you would be jeopardizing other users with the unsupported and insecure OS.  You would need an XP install CD and if you don't have one, I'm not sure you would be able to get one.  I don't know but I doubt a windows 10 "recovery" CD will install or repair XP.  If you tried to update tto windows 10 and t didn't work, you would need too post the exact error you got.  You might be better off at a windows forum

---

### Post by tea for one on 2022-02-10
> **medicatnoob-818 said:**
>  What should I do?
Have you backed up your personal data? If not, that is a [COLOR="#0000FF"]priority[/COLOR].
> **medicatnoob-818 said:**
> Or should I go back to XP somehow 
No, that would be a retrograde step. Join the modern world with an Ubuntu flavour or Windows 10.

Are you familiar with an Ubuntu live session (Try Ubuntu)?
You can download an Ubuntu ISO, create a bootable USB device and examine the OS to see if it meets your needs?
More info:-
[https://ubuntu.com/tutorials/create-a-usb-stick-on-windows#9-installation-complete](https://ubuntu.com/tutorials/create-a-usb-stick-on-windows#9-installation-complete)
[https://ubuntu.com/tutorials/install-ubuntu-desktop#4-boot-from-usb-flash-drive](https://ubuntu.com/tutorials/install-ubuntu-desktop#4-boot-from-usb-flash-drive)

---

### Post by medicatnoob-818 on 2022-02-11
Ok I have a brand new official windows 10 usb stick with fresh license & everything from Best Buy. If I want to install fresh then... what about my files and data on the laptop? Will that be lost or inaccessible? Whats my best way to backup and restore everything to the new version?  That works? I have a Medicat Bootable USB. Best way to backup data to this Toshiba external hard drive and then put back on my ASUS laptop... will all the data be compatible in the modern version win 10?

---

### Post by yancek on 2022-02-11
A standard install of windows will format the partitions on the drive overwriting all data.  Windows 10 has a Custom install option so if you are familiar with installing windows, creating partitions and filesystems, you could use that option.

Backing data to an external drive and then copying it back to the new install is a common method used. I would think the data would be compatible but it might depend upon the type of files.  Better off looking for an answer to that at a windows forum.

---

### Post by TheFu on 2022-02-11
> **medicatnoob-818 said:**
> Ok I have a brand new official windows 10 usb stick with fresh license & everything from Best Buy. If I want to install fresh then... what about my files and data on the laptop? Will that be lost or inaccessible? Whats my best way to backup and restore everything to the new version?  That works? I have a Medicat Bootable USB. Best way to backup data to this Toshiba external hard drive and then put back on my ASUS laptop... will all the data be compatible in the modern version win 10?

You are asking Windows questions in a forum mainly used by Linux people. We will guess the answers, but I've never seen Windows10.  None of my systems run it.
There are general rules.
For example, if you install Windows, it will wipe any OS and files from the system first. That means your 'dual boot' will be gone and I'd guess that all Linux files will be gone too.  Backup anything you don't want to lose to disconnected media.

I cannot see the boot-info data, sorry.  I'm getting this error: 
> You need to be logged in to view this paste.

You can use a flash drive with the Ubuntu installer as your OS if you like while you decide what to do. Also, I hope you didn't actually pay anything for Win10.  I'm pretty sure there are legal ways to get it free from MSFT, if you want Windows.  Why, I don't understand at all. Just use Linux.  A computer that came with WinXP will likely need to run Lubuntu for you to have the best chance at happiness. Lubuntu is nice, simple, usable, but most importantly, it is maintained, so you won't be running an unsupported OS. The internet is a dangerous place. It is up to you to protect yourself.  I suspect your network knowledge and equipment isn't fully maintained, so using something like Lubuntu would be 100x more important for safety.



IMHO.

---

