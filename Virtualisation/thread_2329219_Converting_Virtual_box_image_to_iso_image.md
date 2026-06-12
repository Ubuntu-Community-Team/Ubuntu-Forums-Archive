---
title: "Converting Virtual box image to iso image"
date: 2016-06-29
forum: Virtualisation
---

### Post by luckystar3 on 2016-06-29
Does anyone know how id go about converting an ubuntu virtual machine to an install image on another pc? Or allowing me to run it on the hd of a wiped pc?

---

### Post by howefield on 2016-06-29
Thread moved to the "*Virtualisation*" forum for a better fit.

---

### Post by Habitual on 2016-06-29
> **luckystar3 said:**
> Does anyone know how id go about converting an ubuntu virtual machine to an install image on another pc? Or allowing me to run it on the hd of a wiped pc?

Method 1:
Export your appliances regularly and the ova is "portable" to a new host of new install of Virtualbox.
[COLOR=#ff0000]Same or Lesser Architecture, a 64 bit export will not work on a new 32 bit host.[/COLOR]
[https://www.maketecheasier.com/import-export-ova-files-in-virtualbox/](https://www.maketecheasier.com/import-export-ova-files-in-virtualbox/)

Method 2:
Copy the "/home/user/Virtualbox VMs/*" director{y,ies} to the new host in the same place.
"/home/user/Virtualbox VMs" should be created upon first run of Virtualbox, IIRC.
Fire it up, Close it, and "/home/user/Virtualbox VMs" should exist on the new host.
Copy the former to the latter, same place, Fire up Virtualbox and your appliance(s) 
will be there.

After a "wiped PC"? I've only heard words like testdisk, photorec rlinux.
Sorry, I don't have any experience with desktop recovery tools.
[This]("https://help.ubuntu.com/community/DataRecovery") seems to be a good starting point, if it "were me"...

**If it were me** and I had one of those tools, I'd be interested in anything resembling "/home/user/Virtualbox VMs"

Others will pop in and offer more help, so hang in there....

Advice: Don't do any thing further to the partition/drive/device until they do.
Have a Great Day!

---

### Post by &amp;KyT$0P# on 2016-06-29
Yeah, Habitual's advice is the best way to move/copy a VM to a new instance of VirtualBox or another host that supports those VM formats.

However, if you want to do something else outside VirtualBox, such as installing this Ubuntu to a physical computer, you would create the image the same way you would convert an existing bare metal Ubuntu system into a live CD.  This is known as "remastering" and there are various tools you can use to do it, some free and some not... I don't really know what all is out there now, or what works and what doesn't with recent Ubuntu, as it's been a while since I've played with remastering.
Keep in mind to A) **backup or snapshot your VM before proceeding** and B) uninstall the Guest Additions before remastering (if installed), especially if you're planning to install this on bare metal.  Guest Additions can conflict with the live CD system used by Ubuntu.
If you installed Guest Additions using VirtualBox, follow [this instructions]("https://www.virtualbox.org/manual/ch04.html#idm2140") to uninstall.  If you installed Guest Additions from the Ubuntu package repositories, just use [FONT=Courier New]apt-get purge[/FONT] to remove the packages.

**Very Important: If you are going to use this on a physical computer, make sure you have FIRST tested the image THOUROUGHLY inside a disposable environment of some sort and that it works flawlessly for you!  You might not be able to fully clean up after it if something goes wrong, especially if installing alongside other OS.**

Also, these links might be helpful:
[LiveCDCustomization (starting from an existing LiveCD)]("https://help.ubuntu.com/community/LiveCDCustomization")
[https://help.ubuntu.com/community/LiveCDCustomizationFromScratch]("https://help.ubuntu.com/community/LiveCDCustomizationFromScratch")
Note that in these instructions it doesn't say to un-mount-bind /run, but that is necessary to prevent potential errors when creating the squashfs.

---

### Post by MAFoElffen on 2016-06-29
Well... as you can see, there was 2 different directions that went.

The first response thought you wanted to migrate you VirtualBox VM Guest to another Machine running as the same Virtual Machine in VirtualBox on another physical machine. From reading your post, I can see that this is not what you meant.

The second response suggested to remaster to create a LiveCD image... which will not work... as that was meant to take a physical system and create to a LiveCD Image.

VirtualBox is a type 2 hypervisor, so the whole machine is virtualized. It is not close to running on on-metal, like a type 1 hypervisor is. Vmware has a program to convert a physical to a VM (P2V), but that is backwards to what you want.

Both responses have there points and directions, but I think I understand what you are trying to do, which is sort of a third direction. To convert a VM to a LiveCD, you would need to add a few more steps.

Because virtio drivers need to replaced by drivers for physical:
- Convert VirtualBox VM to VMware VM. 
- Convert VMware VM to Physical (using Vmware vRealize OPS). 
- Then use Remaster to convert the physical to a LiveCD Image. 

That one way to move in that direction...

The other way is to install new. Dump a list of the installed application and/or service packages, to install on the physical. Migrate the data, and select config files  from the virtual to the physical... Just like you would if your were migrating a physical server to another server on different hardware, What is similar to that, is like migrating a system of the same OS, but onto another platform ... Like moving between x86, x86_64, ARM, Itanium, etc.

Honestly, I've converted physical to LiveCDs. I've converted physical to VM's. But I have not converted from virtual to physical. My focus is more in the direction of moving towards virtualization, to consolidate my resources.

Unanswered yet is what is the OS that you are trying to move? Just wondering if it is a "licensed" offering or opesource.

---

### Post by &amp;KyT$0P# on 2016-06-29
> **MAFoElffen said:**
> The second response suggested to remaster to create a LiveCD image... which will not work... as that was meant to take a physical system and create to a LiveCD Image.
Why a physical system is needed?  I didn't run into any problems with the 14.04 live CD I made of a VirtualBox VM (using remastersys inside the VM), but what would the problem(s) be with such a live CD?  And could such problems be resolved by applying the steps in the LiveCDCustomization guide but using the "remaster" CD image?

> Unanswered yet is what is the OS that you are trying to move? Just wondering if it is a "licensed" offering or opesource.
My understanding is that Ubuntu is the guest OS and the OS they're trying to move or copy.

---

### Post by MAFoElffen on 2016-06-29
@halogen2
It's been a while since I've made LiveCD's from physical (I created an Ubuntu flavored, minimum resource, text console distro, with text console apps.)

I have not tried to use remastersys with a VM Guest. I can see it running... but not *sure* what drivers it will try to use from the image for an install of the image onto physical hardware. 

I try to answer with what I know will work based on my own experience, rather than try to guess on what might work. But what I don't know, I try to confirm on my own before I recommend that to someone.

Not saying that you are wrong, Sorry if you took it that way. Just saying I (personally) cannot confirm that. I guess if no-one has done it personally, I could spin one up tonight and see if it will install okay to one of my physical (test) machines. (To see.)

---

### Post by &amp;KyT$0P# on 2016-06-29
> **MAFoElffen said:**
> @halogen2
It's been a while since I've made LiveCD's from physical (I created an Ubuntu flavored, minimum resource, text console distro, with text console apps.)

I have not tried to use remastersys with a VM Guest. I can see it running... but not *sure* what drivers it will try to use from the image for an install of the image onto physical hardware. 

I try to answer with what I know will work based on my own experience, rather than try to guess on what might work. But what I don't know, I try to confirm on my own before I recommend that to someone.

Not saying that you are wrong, Sorry if you took it that way. Just saying I (personally) cannot confirm that. I guess if no-one has done it personally, I could spin one up tonight and see if it will install okay to one of my physical (test) machines. (To see.)
No problem, I'm not offended :) I also answer based only on personal experience, but I tend to take things somewhat more literally than I probably should, and understood your saying "will not work" to mean you had tried it and either got error or a bad ISO or had a computer disaster 8-[ and I was curious what exactly had happened.

Anyway, as far as specifically remastersys there is an unofficial Ubuntu flavor "Cubuntu" which I think uses a custom version of remastersys to make their ISOs, however I cannot recommend using Cubuntu on a physical machine due to the nature of much of the software they chose to preload :roll:
Since they now have a 16.04 ISO, I've just dpkg-repack'd their remastersys package from 16.04 and will definitely be playing with this more.  If it seems to work for me on my Xubuntu 16.04 VM, I can post the package here if that would be helpful.
EDIT scratch that, it looks like it should be possible to make to work but doing so is apparently not straightforward at all.  sorry about that!

---

