---
title: "VirtualBox inconsistent cd/external hdd recognition."
date: 2011-12-04
forum: Virtualisation
---

### Post by flickerclear17 on 2011-12-04
Hi,

I'm running Ubuntu 11.04, and installed Virtualbox.  I created a Windows XP virtual machine and updated it to SP3 fine.  I then installed Office 2010 from DVD, again no problems, and following this I installed iTunes and linked it to my music library on my external hdd, as well as taking the opportunity to copy a few files I wanted over.  There were no problems with virtualbox not recognising dvds/external hdds throughout.  

However, when I tried to rip a CD to itunes, the virtual machine would not recognise the cd - I checked the mount CD/DVD drive option was ticked and it was. I turned the machine off, had a look for some solutions, and I tried enabling passthrough, as well as a "virtual network" share folder between my OS and the virtual machine.  When I turned the machine back on, it wouldn't recognise my external HDD either.  

I changed back all of the options to how they originally were but the virtual machine still does not recognise either cds or my external hdd. I'm not sure what changed - is there any chance this is due there being not enough data allocated to the virtual machine? 

Thanks for any help

---

### Post by leclerc65 on 2011-12-04
Verify that you have done these:
- Download and install Extension Pack.
- Install Guest Additions.
- Include your user profile in the 'vboxusers' group.
- Create 'usb' group and include your user profile in that.

---

### Post by flickerclear17 on 2011-12-04
Thanks for the reply,
I've now done all of the above.
(problem still persists)

Also, it may be helpful to know that when I mount the External HDD in virtualbox, 
a. Windows plays "usb connected" notes and USBDeview is aware it is connected to the system but the system neither makes it viewable/accessible nor assigns it a drive letter.  
b. Virtualbox occasionally freezes when the External HDD is currently mounted, and can be unfrozen by unmounting the External HDD.

---

### Post by tlcstat on 2011-12-05
Greetings,
This solution may get a few comments but I have a separate VM for doing funky stuff. I run it from root. IE "sudo virtualbox". This tends to solve every problem I have encountered with device access. I only use it for .... well... ahem.... ripping!
tlcstat

---

### Post by flickerclear17 on 2011-12-05
tlcstat,

This has made things worse - when using sudo the VM froze on the "windows is starting up" screen.  So I reverted back to running it through my own account only to find that the VM is inaccessible.  I removed and attempted to readd the VM but got: 

"Failed to open virtual machine located in /home/adc/VirtualBox VMs/WindowsXP/WindowsXP.vbox.

Runtime error opening '/home/adc/VirtualBox VMs/WindowsXP/WindowsXP.vbox' for reading: -38 (Access denied.).

/home/vbox/vbox-4.1.6/src/VBox/Main/src-server/MachineImpl.cpp[452] (nsresult Machine::init(VirtualBox*, const com::Utf8Str&amp;, const com::Guid*)).

Result Code: NS_ERROR_FAILURE (0x80004005)
Component: VirtualBox
Interface: IVirtualBox {c28be65f-1a8f-43b4-81f1-eb60cb516e66}"

Any idea how I might fix this?

---

### Post by tlcstat on 2011-12-05
Greetings,
Yes, I don't know exactly what you have done there. Open a terminal and type sudo virtualbox. Delete the VM in the window if one exists. Then do a new installation of your Windows XP. In the top menu bar choose File/Extensions and install the VM Extensions that match the version of VirtualBox that you are using. Be sure to enable DVD passthrough and map all of the shared folders that you need. Run your Windows XP vm and you should be in business. Just remember that this won't be the same VM that you are trying to open when you the use the vm outside of root. The root vm will be stored at root not in the Home dir. You will have to use a terminal and type sudo virtualbox anytime you want to use it. Sorry you are having problems. These problems started with Natty from my experience and have continued.
tlcstat

---

### Post by flickerclear17 on 2011-12-05
Don't worry about it.  
But I'm going to hold out for someone to post a solution rather than set it up all over again.

I managed to find a solution to the ownership access problem here:[http://superuser.com/questions/341529/virtualbox-not-working-on-ubuntu-11-04-natty-narwhal](http://superuser.com/questions/341529/virtualbox-not-working-on-ubuntu-11-04-natty-narwhal)

So it's just the problem detailed in my first post that is still present.

Another quirk which seems worth noting - the VM did pick up on a 2GB USB device I mounted (showed it in "My Computer"), but also thought that it was still there some time after I had removed it.

---

