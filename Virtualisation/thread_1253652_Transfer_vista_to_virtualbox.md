---
title: "Transfer vista to virtualbox"
date: 2009-08-30
forum: Virtualisation
---

### Post by Vinger on 2009-08-30
Hello,

I have a running Kubuntu 9.04 installation on a dualboot with windows Vista. I repartitionned the harddisk to install Kubuntu next to Winvista.

For few programs, i need winvista, but then i have to close Kubuntu to reboot.

Does there exists a way of transferring the existing partition to a virtualbox partition? Or is it possible to work on my vista system without closing Kubuntu?

Allready tx.
grz.

---

### Post by scrooge_74 on 2009-09-20
you could just make a virtual PC and reinstall stuff in it and never have to go back to dual booting

---

### Post by stlsaint on 2009-09-22
> **Vinger said:**
> Hello,

I have a running Kubuntu 9.04 installation on a dualboot with windows Vista. I repartitionned the harddisk to install Kubuntu next to Winvista.

For few programs, i need winvista, but then i have to close Kubuntu to reboot.

Does there exists a way of transferring the existing partition to a virtualbox partition? Or is it possible to work on my vista system without closing Kubuntu?

Allready tx.
grz.


im not 100% sure that its possible to do what it is you are asking...since when you install windows...the needed setup files are not there on the partition for installing. (meaning the same files that are on the disk for installation arent transferred to the hdd) if they were than ppl wouldnt need the disc nor recovery partitions =) but the best solution would be to use your vista disc(if you have one) to make a installation into a virtual machine. or...u can install a ubuntu distro into a vm and see about getting those needed programs to work via wine in the vm.

Hope this helps

---

### Post by DariusS on 2009-09-23
Vinger, if you do a quick search, you may find step-by-step instructions on how to do this.
Now, if I read it right, you're trying to turn an existing Vista installation into a virtual machine in Linux? If so, I have indeed seen tutorials.
With a quick search, I found this: [http://ubuntuforums.org/showthread.php?t=984437](http://ubuntuforums.org/showthread.php?t=984437)

Check it out and let us know if it helps :)

---

### Post by dj_lightning on 2009-09-24
I actually was wondering the same thing... then I remembered about Vista's Back up & Restore.

I have done this once with vista and worked well jumping the OS to a bigger drive. Do a Full PC Backup, save it to another drive.  Now I think you have 2 options.

1: Install Vista to VB and then do a restore on it with your backup.

2: (not sure about this one) You might be able to convert the VHD from the back up to a VDI and then mount it.

Personally I am going the #1 route so I don't have to deal with the pain of the os booting to a new hardware profile and freaking out about it.  
The tutorial is great if you still want to dual boot...... however I doubt I will ever install Vista on anything dedicated again. Plus I can move the drive from my desktop to my mac book... god forbid I need to take vista with me.

Anyways thanks for the rant... wanted to share these other 2 ways of doing it.

[http://articles.techrepublic.com.com/5100-10878_11-6179067.html](http://articles.techrepublic.com.com/5100-10878_11-6179067.html) (Some info on Backup & Restore w/Vistdump)

---

