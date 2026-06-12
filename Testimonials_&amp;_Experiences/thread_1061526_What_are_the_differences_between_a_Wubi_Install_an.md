---
title: "What are the differences between a Wubi Install and full install"
date: 2009-02-05
forum: Testimonials &amp; Experiences
---

### Post by trixman on 2009-02-05
a friend of mine is looking to try Linux and wanted to know if the Wubi install is a true full os, and what are the benefits of a full install.

thanks
:KS

---

### Post by abn91c on 2009-02-05
Wubi requires no partitioning, ideal for new users, once installed it will be a 100% fully usable Ubuntu. Only "issues" are the same as full install with such a things as wireless adapters and Video cards. If the live cd runs fine in the computer, it will run fine when installed. Just make sure you defrag windos before installing Wubi and avoid hard reboots.

---

### Post by trixman on 2009-02-06
> **abn91c said:**
> Wubi requires no partitioning, ideal for new users, once installed it will be a 100% fully usable Ubuntu. Only "issues" are the same as full install with such a things as wireless adapters and Video cards. If the live cd runs fine in the computer, it will run fine when installed. Just make sure you defrag windos before installing Wubi and avoid hard reboots.

how much disk space should he give the Ubuntu install ?

thanks
:KS

---

### Post by armandh on 2009-02-06
8.10 install to a partition on my mini 9 including swap and free space about 7G includes the usual VLC & medibuntu.org codex and a few extra apps

---

### Post by trixman on 2009-02-06
> **armandh said:**
> 8.10 install to a partition on my mini 9 including swap and free space about 7G includes the usual VLC & medibuntu.org codex and a few extra apps

he would like to give more than 7g of space his hard drive is about 190gig
can he give it at least 80gig

thanks again
guys
:popcorn:

---

### Post by perlluver on 2009-02-06
Sure 80GB is plenty, or more if he wants, there are no limits on it.

---

### Post by stchman on 2009-02-06
> **trixman said:**
> a friend of mine is looking to try Linux and wanted to know if the Wubi install is a true full os, and what are the benefits of a full install.

thanks
:KS

A WUBI install will look/feel/taste/smell just like a regular install.  The only problem with a WUBI install is that you are subject to the NTFS file system fragmentation.

---

### Post by jbysmith on 2009-02-06
> **perlluver said:**
> Sure 80GB is plenty, or more if he wants, there are no limits on it.

Keep in mind too that your Windows partition is still accessible as well.  For example, your audio, videos, documents and such, you can link the Windows directories into your home directory, so they're accessible from both operating systems with no hunting around.  No point having duplicate files wasting space, especially with a smaller Wubi installation.

You may or may not want to make a file called .hidden in these directories, and put thumbs.db in them so they don't show up under a normal Nautilus view unless you set it to view hidden files.  Those thumbnail databases irk some people for whatever reason.  

> **stchman said:**
> A WUBI install will look/feel/taste/smell just like a regular install.  The only problem with a WUBI install is that you are subject to the NTFS file system fragmentation.

True that.  Defragging your Windows partition will significantly help.  Even better if you use something other than the weak built in defragger.  I'm a big fan of PerfectDisk for example,  not only sorts by what gets used most, but also intelligently moves the swap file as well, things like that, but that's just my opinion.  Even the built-in one is better than nothing.  It'll make both OS's run smoother.

Also keep in mind your Wubi installation is at the mercy of NTFS errors as well.  If your Windows partition gets blown up, it'll take your Linux installation with it.  On the plus side, if you have the space, backing up your Wubi installation is dead easy.  You can either run a traditional Linux backup, or if in Windows, just copy the Wubi virtual disk files.  Either or is sufficient, just pick whatever suits your needs.  

Personally, Wubi is a great option if you're not sure if you want to commit to having full blown Linux partitions.  Storage aside, it's 100% identical to an actual installation, and removal couldn't be simpler.  Control Panel -> Add/Remove Programs -> Buh-bye.  

My only complaint would have to be that it only currently supports the Buntu's.  Sure, a lot of distros have LiveCD's, and there's virtual machines, but neither option really gives you a true feel for the OS after it's installed and running on your hardware.

---

### Post by trixman on 2009-02-07
> **jbysmith said:**
> Keep in mind too that your Windows partition is still accessible as well.  For example, your audio, videos, documents and such, you can link the Windows directories into your home directory, so they're accessible from both operating systems with no hunting around.  No point having duplicate files wasting space, especially with a smaller Wubi installation.

You may or may not want to make a file called .hidden in these directories, and put thumbs.db in them so they don't show up under a normal Nautilus view unless you set it to view hidden files.  Those thumbnail databases irk some people for whatever reason.  



True that.  Defragging your Windows partition will significantly help.  Even better if you use something other than the weak built in defragger.  I'm a big fan of PerfectDisk for example,  not only sorts by what gets used most, but also intelligently moves the swap file as well, things like that, but that's just my opinion.  Even the built-in one is better than nothing.  It'll make both OS's run smoother.

Also keep in mind your Wubi installation is at the mercy of NTFS errors as well.  If your Windows partition gets blown up, it'll take your Linux installation with it.  On the plus side, if you have the space, backing up your Wubi installation is dead easy.  You can either run a traditional Linux backup, or if in Windows, just copy the Wubi virtual disk files.  Either or is sufficient, just pick whatever suits your needs.  

Personally, Wubi is a great option if you're not sure if you want to commit to having full blown Linux partitions.  Storage aside, it's 100% identical to an actual installation, and removal couldn't be simpler.  Control Panel -> Add/Remove Programs -> Buh-bye.  

My only complaint would have to be that it only currently supports the Buntu's.  Sure, a lot of distros have LiveCD's, and there's virtual machines, but neither option really gives you a true feel for the OS after it's installed and running on your hardware.

thanks so much for all this great info, i first started with the Wubi install then i went over to 100% LINUX. my friend wants to get his feet wet before going over to linux. for me personally i have no need for windows anymore. whatever you want to do in windows you can accomplish in linux.

thanks
;)

---

