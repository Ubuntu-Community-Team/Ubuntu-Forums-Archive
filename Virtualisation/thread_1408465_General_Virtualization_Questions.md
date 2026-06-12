---
title: "General Virtualization Questions"
date: 2010-02-16
forum: Virtualisation
---

### Post by green351 on 2010-02-16
Hi (bare with me I'm a newb),
I have a Lenovo R61 with 1.9 GB Ram, 2.1 GHZ Core 2 Duo Processor, and about 89GB of hard drive space running Ubuntu 9.10.  For my work I need to use Microsoft Excel (the excel file I need to use runs macros which don't seem to work on openoffice).  I figured probably the best way to deal with this is to install a virtual windows and to do my work through that (though if there is another suggestion I would be open to that).
 
My questions are:
-When I allocate virtual memory for the windows system, does this memory become unusable by my Ubuntu even when I'm not using the vsystem?  Or does the memory become restored when I shut down the virtual system
-The same question as above but in regards to virtual hard drive space.
-Do virtual windows systems come with Excel?  If not, can I download excel from the internet while I'm using the vsystem to that vsystem?  If I do that does the software take up actual hard drive space or virtual hard drive space only?
-If I need to run excel and vlc at the same time (occasionally I might need to get on the web too) while i'm working in windows, how much allocated memory and hard drive space would be adequate?
-Whick virtualization would you suggest for my purposes?

Ok thank you very much.  Any help would be greatly appreciated.

---

### Post by Fire_Chief on 2010-02-16
> **green351 said:**
> 
My questions are:
-When I allocate virtual memory for the windows system, does this memory become unusable by my Ubuntu even when I'm not using the vsystem?  Or does the memory become restored when I shut down the virtual system
The memory is not permanently reserved for the virtual machine (VM). If it is not running, then the RAM is usable by Ubuntu just like any other application.
> **green351 said:**
> -The same question as above but in regards to virtual hard drive space.
Now this *is* permanently reserved space (just like application files on the system). Once you allocate the space for the virtual hard drive, the file which contains the virtual hard disk takes up that much space on your filesystem.
> **green351 said:**
> -Do virtual windows systems come with Excel?  If not, can I download excel from the internet while I'm using the vsystem to that vsystem?  If I do that does the software take up actual hard drive space or virtual hard drive space only?
So you need to look at it like this... The VM (virtual machine) makes the OS running inside it believe that it is on real hardware. The OS (in your case, Windows XP/Vista/7/whatever) is not a special version and behaves exactly the same as another copy of Windows on a real PC. It does not include Excel (separate Microsoft product). You can purchase Excel to install and use in the Windows VM or you may be able to get a license from your business to run it since you will be using it for work.
> **green351 said:**
> -If I need to run excel and vlc at the same time (occasionally I might need to get on the web too) while i'm working in windows, how much allocated memory and hard drive space would be adequate?
How much would you use for this on a physical computer? It is about the same (plus a bit of RAM overhead). You don't have to run everything inside the VM while it's running. You can just use the VM for Excel and any other Windows only apps while you run VLC and get on the web from Ubuntu natively. A baseline template for a Windows XP VM with Microsoft Office might be something like 6GB HDD space and 512MB of RAM or higher.
> **green351 said:**
> -Whick virtualization would you suggest for my purposes?
I personally like using xVM from Sun (formerly Virtualbox) but other popular choices are VMware workstation, Xen, and KVM.

Cheers!

---

### Post by bikeboy on 2010-02-16
> **Fire_Chief said:**
> 

Now this *is* permanently reserved space (just like application files on the system). Once you allocate the space for the virtual hard drive, the file which contains the virtual hard disk takes up that much space on your filesystem.



One minor point I beg to differ on. Most desktop virtualisation software such as xVM/Virtualbox (which I also use) allows you to use create a 'dynamic virtual hard disk'. That is, you tell the software to allocate, say, a 15 Gb drive (actually a file), but it will only be as big as the information in it. Your 15 Gb allocation might only be 8 Gb after Windows is installed, but will expand up to a maximum of 15 Gb as needed.

Quite a nice feature.

---

### Post by green351 on 2010-02-16
> **Fire_Chief said:**
> 
Now this *is* permanently reserved space (just like application files on the system). Once you allocate the space for the virtual hard drive, the file which contains the virtual hard disk takes up that much space on your filesystem.
Thanks.  One more question on this: is it easy to unallocate hard drive space, e.g uninstall the vsystem?  If I just uninstall the virtualization program will the hard drive space be restored to my ubuntu?

> **Fire_Chief said:**
> 
How much would you use for this on a physical computer? It is about the same (plus a bit of RAM overhead). You don't have to run everything inside the VM while it's running. You can just use the VM for Excel and any other Windows only apps while you run VLC and get on the web from Ubuntu natively. A baseline template for a Windows XP VM with Microsoft Office might be something like 6GB HDD space and 512MB of RAM or higher.
Oh so I can run both side by side and go back and forth between the two?  Can I get both to run on the same screen?


> **bikeboy said:**
> One minor point I beg to differ on. Most desktop virtualisation software such as xVM/Virtualbox (which I also use) allows you to use create a 'dynamic virtual hard disk'. That is, you tell the software to allocate, say, a 15 Gb drive (actually a file), but it will only be as big as the information in it. Your 15 Gb allocation might only be 8 Gb after Windows is installed, but will expand up to a maximum of 15 Gb as needed.

Quite a nice feature.
Very cool!

Ok thank you very much for advice.  Any other advice people would like to give would still be greatly appreciated.

(PS.  Hopefully someday soon I will be knowledgeable enough to add to discussions myself instead of just asking questions)

---

### Post by mkvnmtr on 2010-02-17
Working with virtual box is much easier than I thought it would be. If I screw something up I can delete it and start again in just a minute or so. You do not even need to burn disks to install. I find myself installing another distro just to see what it is like. Some I keep some just last an hour or so. Just try it you will like it. Go with the download from the Sun site it is a litttle better.

---

### Post by Fire_Chief on 2010-02-17
> **bikeboy said:**
> One minor point I beg to differ on. Most desktop virtualisation software such as xVM/Virtualbox (which I also use) allows you to use create a 'dynamic virtual hard disk'. That is, you tell the software to allocate, say, a 15 Gb drive (actually a file), but it will only be as big as the information in it. Your 15 Gb allocation might only be 8 Gb after Windows is installed, but will expand up to a maximum of 15 Gb as needed.

Quite a nice feature.

True, I forget this is a feature in desktop virtualization products. I usually allocate the full planned space for my VM disk to prevent virtual hard disk file fragmentation on the physical drive. Improves performance (somewhat) at the cost of space.

Green, yes, you can simply delete the created VM (don't even have to remove the virtualization software) to regain the drive space.
The VM can run either in a Window or can run in integrated mode to let you use both OSes at the same time. You'll see what we mean when you fire up the software. :)

Cheers!

---

