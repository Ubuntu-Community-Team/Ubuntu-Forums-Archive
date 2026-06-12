---
title: "Ways to run Ubuntu: virtual vs. native and my OS X dilemma"
date: 2015-03-06
forum: Ubuntu, Linux and OS Chat
---

### Post by zircon_34 on 2015-03-06
I am a huge linux fan, and read all the time stuff about ubuntu, open source etc...but run most of my work on OSX (mba), and would like to spend more time on linux. 

I mainly use it in a virtual environment when I want to program using ipython. Perhaps, for my next laptop I may take a pure linux environment, however, few things are scary. 

First, battery life, is a linux laptop capable of running more than 5 hours? outside a virtual machine? I tried dual boot on MBA, max was around 4-5h. Software alternatives for keynote/ppt (libre office does not the job for ppt it looks archaic) for preparing talks? Can I run OS X in a virtual machine in linux to begin with the transition? Has anyone had the OS X/linux dilemma??

---

### Post by TheFu on 2015-03-06
A few years ago, I got an OSX machine for work.  I wanted to like it, but after 15 yrs on Unix/Linux systems it just didn't "feel right."  I forced myself to use the OSX machine for 2 weeks for everything that I could.  I could see some beautiful design ideas in the machine and the OS. 
However, for me simple things were hard - CIFS, ssh, remote desktops ... just didn't work.  Apple didn't call standard things by the standard names, so I had to get a translation grid to learn things I've know for 20 yrs.  The CIFS connections had a bug at the time without a fix. The keyboard shortcuts I'd know since MS-DOS 5.x didn't work either.   It was frustrating.  
My muscle memory didn't get corrected in the 2 weeks, so I never got good with the keyboard.  Don't get me started about select/paste not working. 

There was some good stuff too - the move of my firefox and thunderbird settings to OSX "just worked" - I never got the built in OSX email program to work with my mail server. Probably an issue with my knowledge of OSX - I've been running email servers for a few decades now, so it wasn't lack of understanding on that side.

The experiment failed for me and I gave the new, hot, Core i5 to someone else.  He was also a Linux guy and ended up converting the machine into a media center. We are old and know what we like already. Don't plan to change.  That stubbornness prevented the beautiful OSX and hardware from working for us. Something similar is likely to happen with your Linux use unless you are more committed than we were. Just sayin'.

To increase battery life - don't use Unity, avoid discrete GPUs, do some disk tuning 9swappiness) and set the mount options to limit writes just for access. An SSD would use less power than a spinning HDD too - so you can set "trim" options on an SSD.

I was under the impression that OSX looked for very specific hardware during boot and that virtualization of that OS doesn't work on non-Apple hardware. Someone else can probably answer that - or google will.

Presentation tools?  I use an html/javascript tool and have for 5 yrs.  Prezi should work, I've never tried it.  You can check synaptic for presentation tools - don't just look in 'software center'. There are 200+ packages listed there. Calligra, Impress.js, Carettah, s5, sozi ... etc.

I get over 7 hrs of battery and real use with Ubuntu 14.04 running openbox (NOT Unity) on a cheap Haswell chromebook (acer C720). Getting Ubuntu installed on this specific hw was non-trivial. I wouldn't recommend someone without a few years of Linux experience try it. Wish I'd bought a real laptop from Dell instead - with the same CPU, but more storage and RAM - so it should easily provide 6+ hrs of use. Any Haswell or later CPU for a smaller laptop (13in or less) should do this. If you do get a chromebook, using chrubuntu which runs in a chroot environment using the same kernel as chromeos is fairly easy. That should provide the same battery life as running chromeOS does - in theory.  If you don't know or want to know these things ... maybe staying with OSX is best?

---

### Post by zircon_34 on 2015-03-06
thanks for the comments, I am thinking of a dell laptop next (xps 13 once it comes out), but not sure yet. I am running all on OSx and iOS, and its kind of difficult to disconnect once you got a habit. But thats the thing, I feel kind of trapped in apple hardware, its good stuff, but once you are in, its kind of difficult to get out. I like all the possibilities using linux, its kind of more fun, OS X is solid but very static not much going on. It looks always the same. And not much to talk about with the community. its still a dilemma for me, but I have a linux box, desktop I built up from scratch and it only runs linux, so I can play with it during the weekend.

I will need to have a better look at presentation software. Its just I did all my presentations in Keynote, and would need something compatible on linux, so I don't have to redo all the work...

---

### Post by TheFu on 2015-03-07
I've never heard of anything compatible with keynote.  Perhaps using a service like Fivrr.com to get 1 converted?

Google found a few .key to .ppt online conversion tools. It doesn't look good.

Perhaps there is a translation tool for keynote to some other format?  Probably just for PPTX ... but then from that another translation to something like HTML5?  I give a few presentation every month and have a collection of talks built up too. Fortunately, mine are in PDF or HTML only now and have been for a few years.  I use s5 - there's a package in the repos (discovered trying to fine options for you).

---

### Post by pmi2 on 2015-03-07
I think I would just use a dual boot, Ubuntu/Unity or whatever desktop you like, and OSX.

Some people I know were doing this (OSX Linux dual boot), using a boot manager now called "rEFInd".  This makes dual booting on Macs a smoother and cleaner process.

[http://sourceforge.net/projects/refind/](http://sourceforge.net/projects/refind/)

This way each OS has the full power of your laptop at its disposal.

---

### Post by Lars Noodén on 2015-03-07
I used to have dual boot with OS X.  However, one thing that I have heard about and that is on my list of things to try is getting a VM to point to a real disk, so that both the VM and the native Ubuntu use the same file system.  I have only heard that it is possibile to set up but have not actually tried.  But maybe that is of interest to you.

---

### Post by zircon_34 on 2015-03-07
> **pmi2 said:**
> I think I would just use a dual boot, Ubuntu/Unity or whatever desktop you like, and OSX.

Some people I know were doing this (OSX Linux dual boot), using a boot manager now called "rEFInd".  This makes dual booting on Macs a smoother and cleaner process.

[http://sourceforge.net/projects/refind/](http://sourceforge.net/projects/refind/)

This way each OS has the full power of your laptop at its disposal.

Yes, I tried this for a while and that worked. I also got a GPT partition instead of hybrid and spent a lot of time tuning the process. But I had some random issues, for e.g. I could not boot anymore using Refind after an OS X update, so each time I had to reinstall the program. That is why I prefer now to run it in a VM.

---

### Post by zircon_34 on 2015-03-07
> **TheFu said:**
> I've never heard of anything compatible with keynote.  Perhaps using a service like Fivrr.com to get 1 converted?

Google found a few .key to .ppt online conversion tools. It doesn't look good.

Perhaps there is a translation tool for keynote to some other format?  Probably just for PPTX ... but then from that another translation to something like HTML5?  I give a few presentation every month and have a collection of talks built up too. Fortunately, mine are in PDF or HTML only now and have been for a few years.  I use s5 - there's a package in the repos (discovered trying to fine options for you).

Can you use animations (appear, move in etc..) with html5? I use latex and if it would be possible to create pdf presentations with animations, I would use it right away. From my experience, translating from one format to another rarely works flawlessly, except to pdf. I am just wondering how people using linux to prepare their talks, I have been at conference and there its either mac or windows to load your talks and its always ppt...

I saw that it is possible to run now Keynote in a web browser, perhaps that would be a possibility if I transition to another non-mac laptop in the near future. 

It has been few years I have been using OSx because the hardware does not break down easily. I guess for now I will use linux in VM and for the next laptop in the near future I will have to make up my mind. Its a big step to make such a radical transition. I did from windows to mac, and I was so liberated, no more virus programs, no more pop ups, no more crashes. But now I realize I have to use mac to get things to work, and I do not like this, I also want to try other hardware...

---

### Post by TheFu on 2015-03-07
> **Lars Noodén said:**
> I used to have dual boot with OS X.  However, one thing that I have heard about and that is on my list of things to try is getting a VM to point to a real disk, so that both the VM and the native Ubuntu use the same file system.  I have only heard that it is possibile to set up but have not actually tried.  But maybe that is of interest to you.

I would virtualize Linux on the apple hardware and run full screen as you transition.  Stop using Keynote for new presentations too. Kick that proprietary habit ASAP.  Once you get down to only a remaining tasks that need OSX, setup a remote OSX system and use Linux to remote in as needed. 

HTML5 is like a replacement for flash, but uses open standards. If you've ever played any flash games, you have an idea of animation that html5 can do.  It also handles audio and video files, (specific formats depend on your installed codec support). h.264, vp8, and vorbis are well supported.

Lars, the best use for share storage is for data or home directories. Not for the OS.  OTOH, you can mount much of a Linux OS over NFS - the file system hierarchy is designed to support that use. In the old days of 2G disks, we did this all the time.

Having local storage directly accessible to a VM is only possible with IOMMU/VT-d PCI passthru. Those are HW, BIOS and Kernel specific and generally being tied to specific hardware is one of the main reasons to move towards virtualization and away from direct physical installs on hardware.  I find virtual disk access to be fast enough - it isn't the slow down here when running Linux VMs. Pushing files from windows to Linux routinely achieves 65-80MB/s. Of course, all the network-based storage capabilities still work - from the client or a server, local or remote. Up to you.  Locally, I use NFS whenever possible and either sftp/scp/sshfs when remote, as needed. FUSE file systems often don't have enough of the POSIX standards to be used for the core OS, however.  sshfs doesn't support hard or symbolic links, for example.

I like the convenience of having a virtual machine - access multiple OSes at the same time and don't need to close all the apps to reboot some other OS. Much more convenient, though for laptops, I prefer to completely shut down when traveling for security reasons (whole disk encryption only works when completely dis-mounted). Suspend is NOT secure., IMHO.

The flexibility in Linux is amazing. Guess that is really a major reason I use it.

---

### Post by Lars Noodén on 2015-03-07
> **TheFu said:**
> Lars, the best use for share storage is for data or home directories. Not for the OS.  OTOH, you can mount much of a Linux OS over NFS - the file system hierarchy is designed to support that use. In the old days of 2G disks, we did this all the time.

This wouldn't be for shared storage.  You are right about data or home directories being shared, but this is (I have heard) a way to have the VM under OS X use the same disk as the native Ubuntu.  OS X is a hard habit to kick because there are so many things that are OS-specific and hard to get out of once one starts using them.

---

### Post by TheFu on 2015-03-07
> **Lars Noodén said:**
> This wouldn't be for shared storage.  You are right about data or home directories being shared, but this is (I have heard) a way to have the VM under OS X use the same disk as the native Ubuntu.  OS X is a hard habit to kick because there are so many things that are OS-specific and hard to get out of once one starts using them.

Well - because Linux discovers hardware at boot, it should work. The only issue would be with the udev rules for the networking - that is MAC-based, so there would be a conflict to resolve.  eth0 for the hostOS MAC and eth1 for the VM?  
Disk UUIDs would be different - use device labels to get around that.

There would be video driver issues too ... stay with the F/LOSS versions, not the proprietary offers from nvidia/ATI.

---

### Post by montag dp on 2015-03-09
For extending battery life, look into a program called TLP:

[http://linrunner.de/en/tlp/docs/tlp-linux-advanced-power-management.html](http://linrunner.de/en/tlp/docs/tlp-linux-advanced-power-management.html)

It works well for me on my laptop and on the previous one I had.  In my experience, it reduces idle battery power by a couple watts.

---

### Post by zircon_34 on 2015-03-10
A while ago I also used: laptop-mode-tools, this increased my battery life from<2 to 4h on mba. [COLOR=#000000]
[/COLOR]

---

