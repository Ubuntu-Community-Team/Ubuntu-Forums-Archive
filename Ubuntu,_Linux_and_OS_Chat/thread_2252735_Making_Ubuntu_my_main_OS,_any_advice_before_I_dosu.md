---
title: "Making Ubuntu my main OS, any advice before I do/suggestions for set up?"
date: 2014-11-14
forum: Ubuntu, Linux and OS Chat
---

### Post by baudrillard on 2014-11-14
TL;DR, I'm wiping my 256 gb SSD so that I can make Ubuntu my main OS w/    the most dedicated space, and will put windows 8.1 in a secondary    partition for compatibility reasons.'m not a pro at Ubuntu, so that's  why I'm asking    for help. Anything I should set up from the get go? Special  configurations? With windows, you don't really have to worry about  anything, but with Ubuntu you have all these options thrown at you and I  don't know (yet!) what I should definitely(or not) do/install.

Hi  everyone, I've recently dual booted ubuntu on both of my laptops(one   of  which ended up not working out, I have a thread on that if you   think you  can help!) and I've decided that I actually really like the    feel/freedom/benefits of Ubuntu, so I actually want to make it my main    OS to use. Windows 8.1 Pro is good and all, so I'll be reinstalling it   on the  smaller two of my partitions for obvious reasons of   compatibility for  some programs, etc, but I want the majority of my SSD   to go to Ubuntu. Windows is an OS that when you install it, you kind  of have everything you need and you don't have to worry about partition  set up or any administrative controls over X folders, blah blah blah,  it's good to go. But since I'm making Ubuntu my main OS, I am obviously  running the risk of setting it up in a way that might make me need to  uninstall it later for technical reasons, or because I just flat screwed  up.

I  would like some advice before making ubuntu my main OS.  I've   already seen the generic  threads created by ubuntu, I know how to  install Ubuntu (at least the standard, copy cutter way) and so I'm  looking   for those bits of advice  that you all have from personal experience.

Thank you!

---

### Post by SagaciousKJB on 2014-11-14
Okay well before you go any further, do you need a clean installation of Windows?  You can save yourself some work of having to reinstall it if you just resize the current partition it resides on.  Use the Ubuntu LiveCD and install "gparted" to do this, resize it from the beginning leaving unallocated space at the beginning for your Ubuntu install.

Ubuntu guided partition can take it from there and offer you a few options, but I would suggest that you use a separate partition for "/home".  The majority of your personal data ( including configuration settings ) will be stored here, and if you need to subsequently reinstall Linux then you can do so without having to overwrite this data.  It's not too complicated, just make a separate partition and designate it to be mounted as "/home" and then use the other for /  If your system has plentiful RAM, I wouldn't even worry about a swap partition--and in the case of trying to dual-boot Windows with MBR and a separate home partition you may be forced to due to the 4 primary partition limit.

Either way you go about it, always install Ubuntu before Windows.  The installer can detect and setup booloader configurations for Windows, but the Windows installer is not so nice--so if you install Windows AFTER Ubuntu you will probably have to reconfigure GRUB.  I'd suggest downloading "SuperGRUB" which can detect operating systems to boot from, just so you don't wind up shut out of your system.

Once everything is happy and running, some base software you'll probably want to install...

Samba: Can read windows network shares
*ubuntu-restricted-extras: Contains closed-source and/or proprietary software such as Flash and MP3 support
libdvdcss: Provides playbacke for copyrighted DVDs
build-essential: Has mostly what you need to compile software from source

Beyond that familiarize yourself with how to add PPA software repositories to your apt sources.

That's about all I can think of.  Are you interested in encrypting your home directory or anything like that?

---

### Post by makitso on 2014-11-14
> I'm wiping my 256 gb SSD so that I can make Ubuntu my main OS w/    the most dedicated space, and will put windows 8.1

As noted in post#2,  you can keep your win8 install.  However, you should use the win8 disk manager [not gparted] to squeeze the partition down to a size that allows ubuntu to be installed after it.


> Either way you go about it, always install Ubuntu before Windows.
I have always installed windows first and then ubuntu.  That way grub can create the dual boot configuration.

During the install, when it asks you about your disk setup, select other and set up your system like below.

---

### Post by ajgreeny on 2014-11-14
> **SagaciousKJB said:**
> Okay well before you go any further, do you need a clean installation of Windows?  You can save yourself some work of having to reinstall it if you just resize the current partition it resides on.[COLOR=#ff0000]  Use the Ubuntu LiveCD and install "gparted" to do this, resize it from the beginning leaving unallocated space at the beginning for your Ubuntu install.[/COLOR]
**NO, NEVER EVER DO THAT !**

Sorry about the shouting, but if you do, you will probably not be able to boot into windows again.

Moving the start point of a windows partition is one of the worst moves you could possibly make; moving the end point is less of a problem, but it is still not recommended, and you should **always** use Window's own disk-management utility to shrink its partitions, not a third party application like gparted.  **Do not** make new partitions using Windows; just leave unallocated space.

I also very strongly recommend that you install Windows first and check that it is running properly, then shrink the Windows partition to make space for Ubuntu using Disk-management, and before you install Ubuntu boot to windows again and run chkdisk or whatever it's called a couple of times to make sure it still runs OK.

Now install Ubuntu using the **"Something else**" option so you can choose the free space you made with disk-management.
If you do things the other way round and install Windows after Ubuntu you will lose grub and the ability to boot Ubuntu until you have reinstalled grub, which while possible to do, is another unnecessary step if you install Ubuntu after Windows.

---

### Post by SagaciousKJB on 2014-11-15
Whoops, yeah pay attention to last two posters, I got the  part about which to install first mixed up and also apparently am good at breaking Windows installations.  Probably explains why I needed SuperGRUB :P

---

### Post by baudrillard on 2014-11-15
Thanks for all of the advice, I was wondering, can I delete stuff on windows, and will my 'potential' shrink size in the partition menu increase? Because if I can just delete a bunch of stuff until I truly minimize window to what I will need it for, then I really will just stick with shrinking it and just expanding the /home directory.

On my ssd now, Windows doesn't use that much space to start with, so would that be possible (deleting stuff to increase potential shrinkage)?

Also, how do I go about telling Ubuntu to reclaim that now empy partition? It technically comes before even the / partition, so isn't that a logical partition in the sense that it comes physically before the /home partition? /home is the very last partition on my ssd, coming after windows, /, and swap.

Thanks!

---

### Post by oldfred on 2014-11-15
Are installs UEFI or BIOS?
That is a hardware choice that is not specifically Windows or Linux.

If BIOS then you have MBR(msdos) partitions. And the 4 primary partition limit, and Windows requires a primary partition to boot from. Part of reason why to install Windows first. 

Windows NTFS partition needs 30% free space to run well. At 10% free you have too little room to run defrag and it will take forever.  So delete, houseclean but understand that Windows grows and you may want some extra room. If booting both, you may want a shared NTFS data partition. Better to use shared data than writing into NTFS from Linux.
 Lots of detail, screenshots and essential info.14.04  Something Else example
[http://www.dedoimedo.com/computers/ubuntu-14-04-install-guide.html](http://www.dedoimedo.com/computers/ubuntu-14-04-install-guide.html)
[http://askubuntu.com/questions/343268/how-to-use-manual-partitioning-during-installation](http://askubuntu.com/questions/343268/how-to-use-manual-partitioning-during-installation)
[http://askubuntu.com/questions/163962/install-alongside-option-missing-how-do-i-install-ubuntu-beside-windows-using](http://askubuntu.com/questions/163962/install-alongside-option-missing-how-do-i-install-ubuntu-beside-windows-using)

   Any install with Something Else which is required with  external drives or any second drive or any install with separate /home
Also shows combo box with location of grub2 boot loader
[https://help.ubuntu.com/community/Grub2/Installing](https://help.ubuntu.com/community/Grub2/Installing)
Does not hightlight changing boot loader to sdb, if external drive, but shows other install screenshots:
[http://askubuntu.com/questions/312782/how-to-install-ubuntu-on-separate-hard-drive-in-a-dual-boot](http://askubuntu.com/questions/312782/how-to-install-ubuntu-on-separate-hard-drive-in-a-dual-boot)
[http://askubuntu.com/questions/274371/install-on-second-hard-drive-with-startup-boot-optiond](http://askubuntu.com/questions/274371/install-on-second-hard-drive-with-startup-boot-optiond)

---

### Post by oldrocker99 on 2014-11-15
One thing that nobody mentioned about installation: I **highly recommend** selecting "Something Else" at the installation page of the installer and creating two partitions. The first, / (root) can be as small as 64GB (which I have never exceeded) and then apportion the rest of the drive as /home. Then, should you have to, or want to, reinstall or try a different distro, you can tell the installer to mount sda1, /, and format it, and to mount sda3 (usually) as /home. Then, all your program settings are intact, and all your downloads, music, documents, and videos, along with a whole lot more, will be preserved.

Not that you shouldn't backup /home regularly, or anything, but this makes reinstallations much quicker. Favorite programs you install after you reboot will behave as they did before the reinstallation.

If you have a desktop with more than one HD, mount one as /home, the other as / and the format the rest as storage. It works for me.

---

### Post by rewyllys on 2014-11-17
+1 to OldRocker's recommendation that / and /home be on separate partitions.

Keeping your root directory, /, and your /home directory separate is one of the most useful and helpful things you can do in using Linux.  Doing so lets you update your distro version, or change to a different distro, at will, without destroying your own irreplaceable files.

---

