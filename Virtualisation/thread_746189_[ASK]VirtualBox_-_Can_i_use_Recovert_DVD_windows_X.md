---
title: "[ASK]VirtualBox - Can i use Recovert DVD windows XP?"
date: 2008-04-05
forum: Virtualisation
---

### Post by doliharahap on 2008-04-05
Hello.
I wanna ask about this virtualization.
Do you know that if we buy a notebook, s'times vendor do not give us the windows copy rite? Instead vendor give us recovery CD/DVD which is we will use that CD/DVD to reinstall our windows.

Can i use that Recovery DVD in my virtualBox to install a new Windows XP on my Ubuntu??

TQ:confused:

---

### Post by Kyle138 on 2008-04-07
It depends on your recovery cd.
Some actually check for their intended hardware before they install and may balk at the "hardware" of the VM.
Also the recovery cd most likely uses an image of the installed OS. This image will already have all the drivers for the hardware installed, the VM won't have the same "hardware" and windows may barf on the first boot. 
The only way to know for sure tho is to just try it, you can't hurt anything.

---

### Post by cmay on 2008-04-07
hi.
i am not sure if the recove cd is not just an ordinary windows installation cd whit the label recorevy cd. mine was i found out. however i do not toy around whit the 
virtual stuff just yet so i dont know if it works.
the two tings  i have found about whit these recover cds of mine is that if i put in a new blank hardisk i needs to be formattet by an livecd first. then i could install full windows xp from that recover cd. the things that it says on the label does not have to be true all the way apperently.
i live in denmark so i do not know if its the same kind of cds you got.
mine was just a recover cd and driver utility cd and a new computer whit nothing on it when i got it.
its not all the cd there are the same. some has some programs installed by the manufacture of the oem products so mine can only be installed on a fujitsu siemens computer .
i dont think that if i went on on tried to install this on a wmware or other virtual box it could work. but like i say i nerver tried to do that.
good luck anyway.

---

### Post by doliharahap on 2008-04-09
@Kyle138

I get the logic from you. I know that my Recovery DVD are automatically installs all the driver of my notebook. But, it will be different with the VM's hardware.

You said that it will not hurt anything rite?Anyway i'll try it..

hehe..

Thanks anyway

---

### Post by Kyle138 on 2008-04-10
Well, if you do it right it can't hurt anything. ;)

Create the new VM with the appropriate harddrive,mem,etc... Put your restore cd in the drive, and before you start the VM change the settings to mount the cd/dvd drive rather than an ISO image. Then when you start the machine it should try and "boot" off the restore cd, it'll either work or it wont. If it doesn't all you do is delete the VM, nothing harmed.

Now, if you leave the restore cd in the drive and restart you actual computer it'll run and wipe out all your information. Thats what you gotta be careful about.

---

