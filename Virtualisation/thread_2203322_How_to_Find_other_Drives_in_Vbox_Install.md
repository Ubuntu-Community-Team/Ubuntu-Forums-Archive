---
title: "How to Find other Drives in Vbox Install ?"
date: 2014-02-02
forum: Virtualisation
---

### Post by shearer4 on 2014-02-02
I have Ubuntu 12.04 installed on Vbox and running well.  I am not able to see any of my other drives, including DVD, HDD or USB sticks under any circumstances I can create?  I've tried adding another drive to the SATA controller, but it doesn't show anything recognizable, when browsing for a drive? 

Am I missing some kind of driver file or not understanding Vbox correctly?  I have RTFM, several times. 

AS

---

### Post by bashiergui on 2014-02-02
Install the guest additions.
[https://www.virtualbox.org/manual/ch04.html#idp55744480](https://www.virtualbox.org/manual/ch04.html#idp55744480)

Then add the USB or DVD drive to your VM
[https://www.virtualbox.org/manual/ch03.html#idp55342960](https://www.virtualbox.org/manual/ch03.html#idp55342960)

if you want certain files on your hard drive you can share files.
[https://www.virtualbox.org/manual/ch04.html#sharedfolders](https://www.virtualbox.org/manual/ch04.html#sharedfolders)

---

### Post by varunendra on 2014-02-02
> **shearer4 said:**
> I have RTFM, several times.
LOL !! :P

I hope I am not missing or misunderstanding anything here..
> I am not able to see any of my other drives, including DVD, HDD or USB sticks under any circumstances I can create?
Assuming you have already installed "Guest Additions" in the guest Ubuntu in the VM, let's address the USB first.

**USB:**
You can't 'Create' USB sticks, only associate the existing ones with a VM. Enabling USB 2 support requires installing VirtualBox Extension pack which you can download from their official website. But even without that, you should be able to enable USB support (in slower legacy USB mode) on a VM. If you already enabled that, the next thing you need to do is to add a "USB Filter" to the machine. This means adding a USB device that is already connected to the host currently (can be also done while the VM is in running state : right-click on the USB icon at the bottom of the VM window > select any of the USB devices listed in the menu). Once it is added, it should show up in Ubuntu running in the VM.

**DVD:** Nothing will show up until you have inserted a DVD or an ISO that is supported by the virtual drive. Although if you navigate to "Computer" (Go > Computer in 12.04), you should see all the connected optical drives, whether occupied or empty.

**HDD:** Nothing will show up until the HDD has been partitioned and/or formatted. Just adding a HDD is like adding a raw HDD that is brand new and doesn't have any partitions or filesystem on it yet.

The points regarding the DVD and HDD are equally applicable to both a physical machine and VMs.

So...

[LIST]
[*]Have you installed "Guest Additions" in the Guest Ubuntu in the VM? (not necessary for these, just recommended, and necessary for some other functions)
[*]Have you installed "VirtualBox Extension Pack" for your VirtualBox installation yet? (necessary for USB 2 support and some other functions)
[*]Have you tried inserting a physical CD/DVD in the physical drive while a "Host Drive.." was associated with the virtual drive? Or,
[*]Have you tried loading an ISO to the virtual drive?
[*]Have you partitioned/formatted the connected HDDs yet? If not, run Gparted in either live mode (available on the Ubuntu ISO) or after installing it > do the partitioning on the newly connected drives. After that, they will show up in the file manager as other existing partitions.
[/LIST]

**EDIT:**
Oops! Simultaneous posting with bashiergui. His links seem more loaded and more authentic. :)

---

### Post by shearer4 on 2014-02-03
Thanks both Varun and Bashiergui: 

I should have added certain details.  I am running Vbox 4.3.6. I have installed guest additions which allowed for settings I did not have available before.  
I completely missed the USB pane of the settings/ports module.  Thanks for pointing that out. I have added 1 USB filter, which allow me to see certain USB ports, but others are grayed out. I assume by adding a second, I can access those?  There are a lot of USB ports on this Mac, some are not required to he accessible, example;  my Fujitsu scanner is USB and AC powered. I can see the description but it is grayed.  Not a problem since I don't want to view  or access that device, other than if I could use it to scan, which is a different issue. 

I inserted a DVD that has Ubuntu-12.04.3-desktop-amd64.iso on it, at 742.2 MB.  I made this initially when I started to install Ubuntu into Vbox, but I was never able to boot from it.  I kept getting the error "no bootable media found" (sic).  

Anyway;  I now see that disk on my Ubuntu desktop and can open and see what is on it. 

But, I inserted an audio CD that has MP3's on it. These are not DRM protected. I burned this from my own CD's.  It works on Mac, but it does not show up at all in Ubuntu?   

As for HDD.  This is a little scary:  When I attempt to connect another HDD, which would be any one of the three drives in my system, Vbox asks me if I want to "create a new Virtual Hard Disk" or "Use an existing Virtual Disk" .  This happens on both Sata 1 and Sata 2.   This may be what it is supposed to do.  I unfortunately selected dynamic VDD when I installed and cannot figure out how to change these to fixed disks unless I completely remove and re-install Ubuntu.  

So;  thanks to your suggestions, I have USB access and I can at least see the Ubuntu DVD. I will try others.  

So; the reason I want to access my other drives, other than just to do it and know how to do it, is to back up. 

To answer your question Varun, I have not partitioned my HDD's yet, although I do have gparted on my installation.  Not sure why I would do this or what it would give me?  These drives are in use by the Mac Host and I don't want to format the actual drive?  > Still confused about this issue.  I'm a noob. 

Sorry to ramble.   Thanks so much again for your help, got me 3/4 of the way there.

---

### Post by varunendra on 2014-02-03
> ..Still confused about this issue.  **I'm a noob**.
What?? Who let you in? **[FONT=Comic Sans MS][COLOR="#A52A2A"]Securityyy..!![/COLOR][/FONT]**

I hope I don't have to tell you that most of us Linux users are born with keyboard in hand, registering with their 2-page long PGP signatures as soon as we come out, and our playgroup school course begins with "How to Hack into your neighbour's firewalled computer within two minutes".

But since I know you won't believe any of that, let's move onto answering your questions now that you are here anyway..

> **shearer4 said:**
> I have added 1 USB filter, which allow me to see certain USB ports, but others are grayed out. I assume by adding a second, I can access those?  There are a lot of USB ports on this Mac, some are not required to he accessible
You can't add 'Ports' in the filter, you add 'Devices' attached to them. Once you add a device filter, it gets attached to the VM regardless of which 'Physical' port it is connected to. From within the VM, it would appear to be connected to the same (virtual) port.

> example;  my Fujitsu scanner is USB and AC powered. I can see the description but it is grayed.
Was the scanner powered on? I'm not sure, but 'grayed' probably means it 'Was' detected by the system, but not currently active, so not available to the VM.

> I inserted a DVD **that has Ubuntu-12.04.3-desktop-amd64.iso on it**, at 742.2 MB.  I made this initially when I started to install Ubuntu into Vbox, but I was never able to boot from it.  I kept getting the error "no bootable media found" (sic).
Did you put the ISO itself as a 'File' on the DVD? An ISO is an image of an optical disc that needs to be treated as the 'Source' of contents that actually have to be written on the physical disc. Here's a CD/DVD burning HowTo :  [https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)

> Anyway;  I now see that disk on my Ubuntu desktop and can open and see what is on it.
What is on it? The ISO itself or its contents (various folders and a few files)?

> But, I inserted an audio CD that has MP3's on it. These are not DRM protected. I burned this from my own CD's.  It works on Mac, but it does not show up at all in Ubuntu?
Doesn't show up on Host Ubuntu (installed on your Mac) or Guest Ubuntu (installed on the VM)? If not appearing on the Host, it maybe Ubuntu specific problem. If not appearing in the VM, it maybe a VirtualBox problem. Both are possible and both may be fixable.

For directly using an ISO on VirtualBox instead of a physical CD/DVD, check out points 16 to 23 of this old thread of mine : [http://ubuntuforums.org/showthread.php?t=1711228](http://ubuntuforums.org/showthread.php?t=1711228)

> As for HDD.  This is a little scary:  When I attempt to connect another HDD, which would be any one of the three drives in my system, Vbox asks me if I want to "create a new Virtual Hard Disk" or "Use an existing Virtual Disk".
Well this is indeed scary. You seem to be confusing your Physical hard disks with Virtual Hard disks. The scary part is that you want to use your Physical hard disks when you don't seem to have a clear understanding of what it means and what are the risks while accessing them from a VM. Fortunately, it is a bit tricky to do in VirtualBox and so it is hard to make a mistake that can be disastrous for your physical harddisk data.

Let's try to make it clear it in a couple of lines, feel free to ask for details if don't already understand this -

[LIST]
[*]The Physical Hard Disks are those Real Hard Disks that you have in your machine.
[*]The Virtual Hard Disks are just 'Files' that the Virtual Machine 'See' as hard disks. Anything you do to these 'Virtual Hard Disks' is completely isolated from your physical hard disk/partitions and so is completely safe for your existing data on the actual drives.
[/LIST]

While it is possible (not easily) to attach the 'Physical' hard disk or its partitions to the Virtual Machine(s) so you can directly access their contents in the VM, it is highly risky unless you are fully aware of its implications and possible risks. The main risk is that both your Operating Systems (the Host and the Guest) may be (or rather would be) accessing these partitions simultaneously. There would be a high chance of both modifying the data (thus the filesystem) simultaneously in their own way. Writing to disk is something that is controlled by the OS kernel at the very basic level, and two kernels working simultaneously on the same disk/filesystem is almost a guaranty of data corruption - often very serious.

If you need to share the data between the Host and Guest, the 'Shared Folders' feature of VirtualBox is much easier and absolutely safe way to do that.

---

### Post by shearer4 on 2014-02-03
> [COLOR=#000000]What?? Who let you in? [/COLOR]**[FONT=Comic Sans MS][COLOR=#A52A2A]Securityyy..!![/COLOR][/FONT]**/QUOTE]   

Whoa! Not sure I can deal with all this information in one sitting!  Will you be my friend? Hah!

[QUOTE][COLOR=#000000]You can't add 'Ports' in the filter, you add 'Devices' attached to them. Once you add a device filter, it gets attached to the VM regardless of which 'Physical' port it is connected to. From within the VM, it would appear to be connected to the same (virtual) port.[/COLOR]/QUOTE] 
  
OK.  So, how do I get more Ports enabled?  I get what you're saying. So, I will go back and look at this in Vbox settings.

[QUOTE][COLOR=#000000]Was the scanner powered on? I'm not sure, but 'grayed' probably means it 'Was' detected by the system, but not currently active, so not available to the VM[/COLOR]

Yes, it is always on. So, the port this device is plugged into was not enabled, I'm guessing?  

[/QUOTE][COLOR=#000000]Did you put the ISO itself as a 'File' on the DVD? An ISO is an image of an optical disc that needs to be treated as the 'Source' of contents that actually have to be written on the physical disc. Here's a CD/DVD burning HowTo : [/COLOR][https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)[/QUOTE]

I will review this. I'm sure I can get this right.  I do see the .iso on the DVD in Linux, once I got my DVD drive recognized, thanks to you.  

> [COLOR=#000000]Well this is indeed scary. You seem to be confusing your Physical hard disks with Virtual Hard disks. The scary part is that you want to use your Physical hard disks when you don't seem to have a clear understanding of what it means and what are the risks while accessing them from a VM. Fortunately, it is a bit tricky to do in VirtualBox and so it is hard to make a mistake that can be disastrous for your physical harddisk data.[/COLOR]

This part, I get.  I think I was just hesitant based on the scary message (ooh!).  What I am actually trying to do is Clone my VDI to a second disk in my Mac Pro.  I've done this once, but now it seems I have conflicting UUID problem, which I will figure out at the terminal, after spending some time with the Vbox manual.   

More to come!  Stay tuned!

---

### Post by bashiergui on 2014-02-03
> So; the reason I want to access my other drives, other than just to do it and know how to do it, is to back up. OK woah. Couple of problems here. Firstly, you don't want to serve your HDD as a virtual drive on your VM. If you want to access the HDD from the VM you want to "share folders" you could share the whole /home directory if you like. Follow the directions in my first post to do that.

Second problem: you want to back up your computer onto a VM living on that same computer. You're better off just duplicating the folders you want to save. The whole purpose of backups is to recover from data loss. If your hard drive fails how will you recover the backup from a VM inside the failed hard drive? If your computer gets stolen what happens to the VM? Back up to an external hard drive or a cloud service, or a ton of DVDs.

edit: whoops just noticed the overlap with this post & varunendra's. Turnabout is fair play ;)

---

### Post by bashiergui on 2014-02-03
> What I am actually trying to do is Clone my VDI to a second disk in my Mac Pro. I've done this once, but now it seems I have conflicting UUID problem, which I will figure out at the terminal, after spending some time with the Vbox manual.  This part is pretty easy. You just choose 'export' and vbox will create a OVF that you can transfer to the Mac over the network or with a flash drive. Then you click 'import' on the Mac in virtualbox and the VM will show up.

---

### Post by shearer4 on 2014-02-03
I got you on that. But, why can't I use Clone, from the Vbox contextual menu (4.3.6)   I did this before and it worked, but now I don't get an option of what drive to clone to. So, the clone ends up on my main Mac HD.  

I have three actual hard drives in my box. The main (I call it) Mac HD is backed up to two different external drives.  My critical data files are backed up to a cloud service.  I'm somewhat paranoid. 

But, I know I cloned my Vdi before to another drive in my Mac Pro, and now I can't do that?  Not sure what happened. But, that is what I am trying to replicated.  

For example; I have Ubuntu 12.04 installed via Vbox on the second drive in my system. Virtual Box is, of course, on my Mac HD.  But, since I have a lot of free space on the second drive, I cloned Ubuntu to there, ran it from there then removed the original in Vbox GUI.  Now, I can't repeat that process with Mint?  Again, I cannot figure out why I did this once and can't do it again. 

The only thing I can think of is the UUID is somehow still stuck in my root somewhere and it won't duplicate itself? 

AS

---

### Post by bashiergui on 2014-02-03
Import/export works better to transfer from one host to another. Clone works when creating a duplicate on the same host. You probably got lucky previously that the cloned versin worked, not sure. Import/export ensures that all the virtual hardware is exactly the same for both VMs so you don't encounter hardware problems.

Don't take my word for it:

[https://www.virtualbox.org/manual/ch01.html#ovf](https://www.virtualbox.org/manual/ch01.html#ovf)

---

### Post by varunendra on 2014-02-04
> **bashiergui said:**
> edit: whoops just noticed the overlap with this post & varunendra's. Turnabout is fair play ;)
Yea yea, call it whatever you want to, I know it was a conspiracy for revenge.. :|

Anyway..
> **shearer4 said:**
> What I am actually trying to do is Clone my VDI to a second disk in my Mac Pro.  I've done this once, but now it seems I have conflicting UUID problem, which I will figure out at the terminal, after spending some time with the Vbox manual.
So what I understand from above, combined with whatever you posted previously and in posts later to the above one, you are trying to kinda 'Move' (or Copy) the instance of your Ubuntu installation onto your physical disk(s). And the one you are currently running on the physical machine was created the same way.

If this is right, I assume you already know how to attach physical disks to VBox VMs, because that's the most straightforward (albeit a bit risky and not the only one) way of achieving that.

The other way (much safer, albeit relatively cumbersome) I often suggest to simply use clonezilla to clone the Guest OS and put the cloned image in a folder shared between Guest and Host. Then use clonezilla again, on the Host this time, to restore this image on a desired partition.

To change the UUID of a partition, you can use "tune2fs" command. For example, if the target partition is, say, /dev/sdb2, then the command would be -
```
sudo tune2fs -U random /dev/sdb2
```
The argument "random" will generate a random UUID. You can also use a pre-generated UUID (like "c1b9d5a2-f162-11cf-9ece-0020afc76f16"), or "time" as arguments to "-U" option.

> **bashiergui said:**
> Import/export ensures that all the virtual hardware is exactly the same for both VMs so you don't encounter hardware problems.
I'd like to add that unless you are using any funny proprietary drivers, Linux is pretty good at 'Adapting' itself to hardware changes. So the above isn't really a problem since a VM has no 'Funny' drivers that may cause trouble later.

---

### Post by shearer4 on 2014-02-04
> [COLOR=#000000] Clone works when creating a duplicate on the same host.[/COLOR][COLOR=#000000]

Probably being dense here, but I'm not moving to a different host, just a different Volume on the same host. 

so: right now my installation of Vbox is  /Users/me/Applications/VirtualBox.app

my installation of Ubuntu is on Volumes/Tera_Drive/VirtualBoxVMS/Ubuntu

And it works fine. I got it from my Mac Disk to the second drive by cloning?  But I don't recall every step unfortunately. 

Now, I'm trying to do the same thing with Linux Mint;  that is currently   /Users/me/VirtualBox VMs/New_Mint

So, cloning is not doing what I expected, so I tried exporting the appliance to a folder on /Volumes/Tera_Drive/Mint

The .ova file is there. It took about a half hour, so I went to bed :=   

Now' when I try import, it seems like it is going to go right back into the Mac HD volume again.  There is no option or selections I see to open import in another volume.  




[/COLOR]

---

### Post by shearer4 on 2014-02-04
[QUOTE][COLOR=#000000]So what I understand from above, combined with whatever you posted previously and in posts later to the above one, you are trying to kinda 'Move' (or Copy) the instance of your Ubuntu installation onto your physical disk(s). And the one you are currently running on the physical machine was created the same way.[/COLOR]/QUOTE]

Exactly! 

I got one instance there already, that is Ubuntu 12.04.3, and it works fine.  See my response to bashiergui this morning. But, the behavior this time is different.  

This is not a problem as in something is broken. I just want to free up the space on my man Mac HD.

---

### Post by shearer4 on 2014-02-04
> [COLOR=#000000]Import/export works better to transfer from one host to another. Clone works when creating a duplicate on the same host. You probably got lucky previously that the cloned versin worked, not sure. Import/export ensures that all the virtual hardware is exactly the same for both VMs so you don't encounter hardware problems.[/COLOR]

First; please understand, I am just trying things that you're suggesting, not questioning your advice. OK, I really appreciate both you and Varun trying to help. 

I read the manual link you sent, and as it turns out, I had read that page before, because that's where I read about Clone.  So, then I imported the .ova file  and got a Mint-disk.vmdk   in my Users/me/VirtualBox/Vms folder.  Same as before. 

If I manually move this to the other Volume, I am fairly certain it won't open, but will try.

EDIT:  Nope.  No dice as I expected.  Just cannot figure?  I am going to go back and see if I can find previous information I had on Cloning.

---

