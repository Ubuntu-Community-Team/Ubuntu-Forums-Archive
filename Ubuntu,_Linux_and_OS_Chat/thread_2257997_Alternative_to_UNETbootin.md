---
title: "Alternative to UNETbootin?"
date: 2014-12-24
forum: Ubuntu, Linux and OS Chat
---

### Post by Kurt_Alan on 2014-12-24
The first time I used UNetbootin it  was smooth as butter.

The second time I used UNetbootin for Ubuntu it choked and I had to start a thread here (and found a solution).

The third time I used UNetbootin for a different distro (to dual-boot with Xubuntu), UNetbootin choked again with a file path error message, so now I have to investigate that.

It's starting to get a little CRAZY.

Is there another (or better) program for a flash drive install of an .iso?

---

### Post by coldraven on 2014-12-24
I use Unetbootin all the time and never had a problem with it. I do however wipe the memory stick before using it.
You could try Pendrive, I have not.
[http://www.pendrivelinux.com/](http://www.pendrivelinux.com/)

---

### Post by sudodus on 2014-12-24
Try [mkusb]("https://help.ubuntu.com/community/mkusb") in linux and [Win32 Disk Imager]("https://wiki.ubuntu.com/Win32DiskImager/iso2usb") in Windows to copy/clone/flash the iso file to a pendrive! If the iso file is a hybrid iso file it works after cloning (very high success rate). If it is a linux iso file but not a hybrid file, you can easily make it a hybrid iso file with the program isohybrid.

*Edit*: Unetbootin works most of the time for me. I use it when I want persistence.

---

### Post by cariboo on 2014-12-24
I've been using Disks->Restore Disk Image that was recommended by one if the developers, I haven't had a failure since.

---

### Post by sammiev on 2014-12-24
> **sudodus said:**
> Try [mkusb]("https://help.ubuntu.com/community/mkusb") in linux and [Win32 Disk Imager]("https://wiki.ubuntu.com/Win32DiskImager/iso2usb") in Windows to copy/clone/flash the iso file to a pendrive! If the iso file is a hybrid iso file it works after cloning (very high success rate). If it is a linux iso file but not a hybrid file, you can easily make it a hybrid iso file with the program isohybrid.

*Edit*: Unetbootin works most of the time for me. I use it when I want persistence.

+1 with mkusb. :)

---

### Post by Kurt_Alan on 2014-12-24
@coldraven

Thanks, I'll check your alternative. Yes, I have reformatted my flash drive before using UNetbootin, even tried FAT32 vs. ext4 -- didn't make a difference for my errors.

---

### Post by Kurt_Alan on 2014-12-24
@sudodus --

Thanks for the goldmine of alternatives. Um, I forgot, what is "persistence"? I did not check this in UNetbootin. Could this have anything to do with my problem?

---

### Post by sudodus on 2014-12-24
A normal live system is not saved, so when you reboot, it will be the same as the first time (from the iso file). A persistent live system uses an overlay method, so that you can save installed program packages, settings and tweaks, but you cannot upgrade the linux kernel. The persistence is stored in a casper-rw file or partition. Unetbootin creates a casper-rw file if you select persistence.

I'm not sure, but I don't think the current problems of Unetbootin depend on persistence. On the other hand, if you unplug the pendrive, before it has saved the overlayed changes to the drive (flushed the buffers), the system will be damaged.

You can search for posts by ***C.S.Cameron*** here at the Ubuntu Forums about persistent live systems.

---

### Post by Mike_Walsh on 2014-12-24
> **coldraven said:**
> I use Unetbootin all the time and never had a problem with it. I do however wipe the memory stick before using it.
You could try Pendrive, I have not.
[http://www.pendrivelinux.com/](http://www.pendrivelinux.com/)

I agree with coldraven. I, too, have never had a problem with UNetbootin.....but, like him, I also wipe the stick CLEAN.

When you format your stick, are you simply re-formatting.....or the FULL format, over-writing EVERYTHING with zeros? This is, I find, the only way to guarantee good results. It takes a little longer, depending on the capacity of your stick (I use 'Disks' for this).....anywhere from 15 minutes or so for a 4 GB, up to around 2 hrs for a 32 GB stick (due to the restricted read/write rates for a USB 2.0 stick on my elderly hardware) ; but the preparation time is well worth the hassle-free installation that results from it.

I have an assortment of sticks, from 4 GB up to 32 GB, which I have repeatedly used for not only 'Live-USB's, but also full installs. With the proper preparation, I can guarantee perfect results, every time.

Regards,

Mike. :)

---

### Post by sudodus on 2014-12-24
> **Mike_Walsh said:**
> I agree with coldraven. I, too, have never had a problem with UNetbootin.....but, like him, I also wipe the stick CLEAN.

When you format your stick, are you simply re-formatting.....or the FULL format, over-writing EVERYTHING with zeros? This is, I find, the only way to guarantee good results. It takes a little longer, depending on the capacity of your stick (I use 'Disks' for this).....anywhere from 15 minutes or so for a 4 GB, up to around 2 hrs for a 32 GB stick (due to the restricted read/write rates for a USB 2.0 stick on my elderly hardware) ; but the preparation time is well worth the hassle-free installation that results from it.

I have an assortment of sticks, from 4 GB up to 32 GB, which I have repeatedly used for not only 'Live-USB's, but also full installs. With the proper preparation, I can guarantee perfect results, every time.

Regards,

Mike. :)

You are right, making the pendrive's file system clean helps a lot. But unless you want persistence (or an installed system), it is way too long time to wait for a USB boot drive system. Try mkusb, that will do the work in 1-4 minutes, and needs no cleaning.

A 1 GB iso file flashed to a slow pendrive (5 MB/s) needs 200 seconds, but flashing the same iso file to a fast USB 3 pendrive in a USB 2 port (25 MB/s) needs only 40 seconds.

See this link about pendrive speed (post #6) [Howto help USB boot drives]("http://ubuntuforums.org/showthread.php?t=2196858")

---

### Post by oldrocker99 on 2014-12-24
I had problems with Unetbootin until I formatted the drive as FAT (compatible with most filesystems) in the gnome-disk window. You do, of course, have to unmount the drive first, and remount it afterward. I have not had a problem with Unetbootin since.

---

### Post by Mike_Walsh on 2014-12-25
Thanks for that, sudodus. I'll have a look at that, & give it a try.

I don't mind waiting for things to sort themselves out these days; I have a fair bit of time on my hands, and plenty of other things to occupy it with! If I'm formatting one of the larger ones, I simply set it going, and then go off and get on with something else. But if there IS a way of speeding things up a bit, then I'll have a look at mkusb, and give that a try; I've got to start getting used to using some of the shell commands sooner or later!

I WILL agree with you about the SanDisk Cruzer Blades; I have no end of these, as, like you, I've found out that they work extremely well, are very reasonably priced, and in general, boot reliably. I've only had one out of a dozen of so in the last 2 or 3 years that had a number of 'bad' blocks, and wouldn't behave itself.

Probably a 'Friday afternoon' job..!

I find the 'nano' form-factor Cruzer 'Fit' works very reliably, too.

Regards,

Mike. ;)

---

### Post by Tadaen_Sylvermane on 2014-12-25
```
sudo dd if=/path/to/iso of=/dev/sd? oflag=direct bs=1M
```

the simplest ways are the best.

---

### Post by sudodus on 2014-12-25
The direct ***dd*** method is risky. ***dd*** is nick-named 'disk destroyer' because there are no check-points, no questions asked, and a small misunderstanding or even a typing error can destroy your family pictures.

Otherwise, when the command is correct, it is very good. This is why I made ***mkusb*** to 'wrap security' around ***dd***.

---

### Post by Tadaen_Sylvermane on 2014-12-25
While I agree at the same time by that logic one should avoid the command line altogether. Anything done directly from the command line is inherently more risky than a gui scenario. Nature of the beast. But you can't really use the true power of a linux system unless you are willing to use the terminal to some degree.

---

### Post by sudodus on 2014-12-25
There are several command line tools that are safer than ***dd***. Some of them have check-points and questions are asked. But I won't say that you should not use ***dd***, only that I made a tool to make it safer. For example, ***mkusb-nox*** is a command line tool, that 'wraps security' around dd (for people who prefer command line tools to GUI tools, and for servers, that lack GUIs).

And I must admit that I use ***dd*** sometimes, but ***I double-check and triple-check***, that everything is correct before hitting the Enter key.

---

### Post by Stinger on 2014-12-26
You can use the gnome disk tool for generating a live USB-stick too, it's quite easy if you have gnome-disks installed, Ubuntu and quite a few derivatives have.
You need a USB-stick you can spare for the purpose, because this operation destroys any data present on the stick when generating the live media.

You just right-click an iso and choose the "Image writer" option, choose your USB-stick as destination, then you hit "restore image"  and you are promted "if you are really sure you wanna do this ?" hit "restore" and are promted for your password. Badabing badabum you have Created a Live USB-media from your iso.
It really can't be any easier, use it all the time now.

There is a nice tutorial on the Fedora Magazine covering this, not quite the same approach as I use but it's the same.
[How to make a Live USB stick using GNOME Disks]("http://fedoramagazine.org/how-to-make-a-live-usb-stick-using-gnome-disks/")

---

### Post by Kurt_Alan on 2014-12-26
OP Conclusion:

mkusb is an order of magnitude more precise than UNetbootin. mkusb is a joy to behold.  I just started with it and haven't had any problems.

Good-bye UNetbootin.  My UNetbootin is working with some snags, so this will now be my number two choice.

---

### Post by mips on 2014-12-27
dd

Works on all unix/linux based systems and there is also a [dd for windows]("http://www.chrysocome.net/dd"). never failed me.

---

### Post by nomenkultur on 2014-12-27
dd works fine for me for stuff like manjaro/lubuntu etc...

 for some reason ubuntu next or chromixium etc give me boot errors with dd 

must be a uefi thing

---

### Post by sudodus on 2014-12-27
> **nomenkultur said:**
> dd works fine for me for stuff like manjaro/lubuntu etc...

 for some reason ubuntu next or chromixium etc give me boot errors with dd 

must be a uefi thing

Maybe those iso files need treatment with isohybrid.

```
isohybrid file.iso
```

---

### Post by sudodus on 2014-12-28
> **sudodus said:**
> [QUOTE=Mike_Walsh;13193816]I agree with coldraven. I, too, have never  had a problem with UNetbootin.....but, like him, I also wipe the stick  CLEAN.

When you format your stick, are you simply re-formatting.....or the FULL  format, over-writing EVERYTHING with zeros? This is, I find, the only  way to guarantee good results. It takes a little longer, depending on  the capacity of your stick (I use 'Disks' for this).....anywhere from 15  minutes or so for a 4 GB, up to around 2 hrs for a 32 GB stick (due to  the restricted read/write rates for a USB 2.0 stick on my elderly  hardware) ; but the preparation time is well worth the hassle-free  installation that results from it.

I have an assortment of sticks, from 4 GB up to 32 GB, which I have  repeatedly used for not only 'Live-USB's, but also full installs. With  the proper preparation, I can guarantee perfect results, every time.

Regards,

Mike. :smile:

You are right, making the pendrive's file system clean helps a lot. But  unless you want persistence (or an installed system), it is way too long  time to wait for a USB boot drive system. Try mkusb, that will do the  work in 1-4 minutes, and needs no cleaning.

A 1 GB iso file flashed to a slow pendrive (5 MB/s) needs 200 seconds,  but flashing the same iso file to a fast USB 3 pendrive in a USB 2 port  (25 MB/s) needs only 40 seconds.

See this link about pendrive speed (post #6) [Howto help USB boot drives]("http://ubuntuforums.org/showthread.php?t=2196858")
[/QUOTE]

After a few years one of my pendrives, a Sandisk Extreme, 32 GB, was slowing down to about 30-40 % or the original writing speed (in USB 2 ports, where I use it most of the time). I cleaned it by overwriting the whole drive with zeros. After that it is running at its full speed (in the same kind of ports) again.

I'm sharing this result to verify that over-writing EVERYTHING with zeros keeps pendrives in good shape.

---

### Post by monkeybrain20122 on 2014-12-29
Multisystem [http://liveusb.info/dotclear/index.php?pages/install](http://liveusb.info/dotclear/index.php?pages/install)
An attractive feature over unetbootin or dd is that you can easily create multiboot (with multi OSes) usb easily (with dd you also need to remove the content with dd by overwriting if you want to use the usb again for other things, reformatting with things like gparted apparently doesn't work)

---

### Post by mc4man on 2014-12-29
The thing I used to hate about unetbootin is that when you're in it's 'browse' mode it allows the moving of dir. or files (& with root priv.
Used to be an occasional issue here with a laptop & enabled touchpad. 
(- currently use a wireless mouse with touchpad disabled thru a log in script as Ubuntu can't seem to fix keeping a touchpad disabled so not an issue anymore

Still like s-d-c the best though generally better to preformat & doesn't always work with non ubuntu kernels

---

### Post by Jacob_Goff on 2014-12-30
I've used Pendrive and UNetbootin, UNetbootin definitely made it easier for me to use my Ubuntu Linux system in the operating system file initial install and continues to run my system today... I think you should redo your whole thing if it's not working for you. The sooner you delete and redownload/install UNetbootin, the better.

---

### Post by Kurt_Alan on 2014-12-30
OP Conclusion:

I have tried mkusb via a PPA install.  It worked without any hiccups or issues and I was able to install OS's on four flash drives as well as install a dual boot system.

---

### Post by sammiev on 2014-12-30
> **Kurt_Alan said:**
> OP Conclusion:

I have tried mkusb via a PPA install.  It worked without any hiccups or issues and I was able to install OS's on four flash drives as well as install a dual boot system.

I guess you can mark this one as solved.

---

### Post by Kurt_Alan on 2014-12-31
@sammiev --


Can't mark as "solved" because this is in the OS chat sub-forum. I really raised this as an opinion question and not a problem.  But, yes, thanks to the posts here, my "problem" is solved!

---

### Post by sudodus on 2014-12-31
This has been (and is) a good thread with a lot of information, tips and opinion from many people :KS

Thanks [Kurt_Alan]("http://ubuntuforums.org/member.php?u=113594") 	  						for starting it, and Happy New Year to all of you :-)

---

