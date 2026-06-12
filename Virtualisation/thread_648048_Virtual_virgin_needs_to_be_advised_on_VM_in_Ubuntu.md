---
title: "Virtual virgin needs to be advised on VM in Ubuntu"
date: 2007-12-23
forum: Virtualisation
---

### Post by theZoid on 2007-12-23
I have a dual boot system right now with Vista HP 32 and Ubuntu Gutsy 7.10.  I want to run some vertical market tax programs in Linux via a Virtual Machine.  I have installed VMware server in Ubuntu and that much appears to be ok.  When I power on the 'Vista' VM it asks for an OS installation disk (Vista).  Do I need to reinstall this on the virtual disk or is there some other way of setting this up since Vista is already on the machine?  I also have a copy of XP pro....I wonder if I have to install another OS if I should use XP instead for better compatibility?

thanks in advance for any enlightenment and opinions.

---

### Post by seshomaru samma on 2007-12-23
you can add an existing windows partition as a vmware virtual machine, xp or vista
look here :
[http://digg.com/linux_unix/HowTo_Run_Your_Existing_Vista_Installation_in_Ubuntu_with_Vmware_player](http://digg.com/linux_unix/HowTo_Run_Your_Existing_Vista_Installation_in_Ubuntu_with_Vmware_player)

you can also install a new OS - up to you...

---

### Post by theZoid on 2007-12-23
> **seshomaru samma said:**
> you can add an existing windows partition as a vmware virtual machine, xp or vista
look here :
[http://digg.com/linux_unix/HowTo_Run_Your_Existing_Vista_Installation_in_Ubuntu_with_Vmware_player](http://digg.com/linux_unix/HowTo_Run_Your_Existing_Vista_Installation_in_Ubuntu_with_Vmware_player)

you can also install a new OS - up to you...

Interesting, I went to install a legit copy of xp I have, and XP said it couldn't find the HD...although I do have a 16gig virtual disk set up....I also noticed VMware gave me a warning at the bottom with a yellow triangle symbol, that I don't have VMtools installed.  Who, what, when, where, why?  thanks :D

---

### Post by theZoid on 2007-12-23
Help appreciated.  I'm trying migrate most everything to Ubuntu and basically shrink down my Vista partition for pretty much gaming only booting.  thanks in advance.  btw, I'm using VMServer to install (try) XP

---

### Post by Goofee691 on 2007-12-25
how is the virtual hard drive hooked up to the vm, ide or scsi

---

### Post by theZoid on 2007-12-25
> **Goofee691 said:**
> how is the virtual hard drive hooked up to the vm, ide or scsi

I've got it installed now, no problem....XP Pro VM in Ubuntu....question though, I have shared partition for Vista/Ubuntu, but it is FAT32...any reason for that?  I seem to able to read/write to NTFS....so should I convert the FAT32 to NTFS?  Or is there some kind of advantage to FAT32 re: linux?  My 25 gig Virtual XP disk resides on the partition, and IT is formatted NTFS.

thanks

---

### Post by L0stAngel on 2007-12-27
How did you fix your problem? I am having one too...I get  a BSOD when I try booting my XP partition in vmware.

---

### Post by rickycodie on 2007-12-27
how's installing vmware, because it's killing me.

---

### Post by fjgaude on 2007-12-27
Use Synaptic to install. It's in the repos of Ubuntu's Partner. Click Setting/Repositories/Third-Party Software, then do a Search for VMware. Install.

---

