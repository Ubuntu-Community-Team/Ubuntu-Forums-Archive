---
title: "Error trying to load Ubuntu 10.04 into VirtualBox"
date: 2010-05-18
forum: Virtualisation
---

### Post by asharpham on 2010-05-18
I want to try Ubuntu 10.04 before upgrading from Karmic so I downloaded the iso file and burned it to a disc. After adding "New" to VirtualBox and selecting all the defaults, I loaded the disc with 10.04 on it. But I got the error "FATAL: No bootable medium found! System halted."

What is wrong? The CD/DVD device is ticked in Devices.

---

### Post by TJRC on 2010-05-18
I installed VirtualBox and Lucid over the weekend, with no problems, following the step-by-step instructions at [http://www.psychocats.net/ubuntu/virtualbox](http://www.psychocats.net/ubuntu/virtualbox) .

Give that a try.

Note that this process does not require making a physical disc from which to boot; you can tell VirtualBox to associate the ISO image file with your virtual CD/DVD.  That worked just fine for me:[INDENT]"The next thing to do to make the (currently blank) virtual hard drive  useful is to add the downloaded Ubuntu disk image (the .iso) boot on  your virtual machine. Click on  **Settings **and **Storage**. Then,  under *CD/DVD Device*, next to *Empty*, you'll see a little  folder icon. Click that, and you can select the Ubuntu .iso you  downloaded earlier." [/INDENT]The tutorial doesn't mention it, but you should also the Guest Additions for Linux.  Otherwise, you'll be frustrated by the small (800x600, I think) screen size.  One of the benefits of the guest additions is the ability to get the full screen.  See installation instructions at [http://www.virtualbox.org/manual/ch04.html#id2885517](http://www.virtualbox.org/manual/ch04.html#id2885517) .  Good luck.

---

### Post by TJRC on 2010-05-18
By the way, since you've already made the physical disc, maybe the quick fix for you is to configure your Lucid VM to associate that VM's virtual CD/DVD with the machine's physical device.

I think that would be to select the Lucid VM, go to **Settings** / **Storage**, and set *CD/DVD Device *to *Host drive*.

---

### Post by asharpham on 2010-05-20
I'm currently running Ubuntu 9.10. I installed VirtualBox quite a while ago and have Win XP running in it. Now I want to add 10.04 as a second virtual system.

I've followed the instructions implicitly but every time I try to add 10.04 as a new OS I end up getting an error that says it can't complete the process because Ubuntu 10.04 is already in the .Virtualbox folder.

So I go to the folder and move the 10.04 entry to the garbage bin. Then I empty the garbage bin and restart the computer. Before proceeding, I go back to the .Virtualbox folder and HarDisks sub-folder to make sure the 10.04 entry is gone. And I confirm that it has.

I start the procedure once more to add 10.04 as a new virtual drive but end up with the same error. I don't know what to do next.

---

### Post by asharpham on 2010-05-20
To avoid the error I mentioned above, I called the new virtual system by a different name and got a bit further. When it got to the point of asking for the installation file, I put the disk into the player and off it went. However, when it accessed the disk, an error message came up which said "FATAL: No bootable medium found! System halted."

By the way, the CD/DVD player is set to Host Drive. I'm beginning to wonder of the iso file on the disk is properly burned. There doesn't seem to be an option to load from a file. Virtualbox only gives CD/DVD or floppy as options to source the file from.

---

### Post by TJRC on 2010-05-20
> **asharpham said:**
>  There doesn't seem to be an option to load from a file. Virtualbox only gives CD/DVD or floppy as options to source the file from.


It's not a separate an option to load from a file.  You associate the virtual CD/DVD with the ISO file, and then boot from the virtual CD/DVD.

---

### Post by TheFu on 2010-05-20
Is there a reason you just don't point the OS settings inside virtualbox for that specific machine to boot from the ISO file directly?  There's no need to actually burn a physical disk.  Then be certain you set the image file to be "bootable" and you should be golden.

---

### Post by asharpham on 2010-05-21
I'm pretty new at all this. I have no idea how to do what you're suggesting. Is there any chance you could give me a step by step procedure?

---

### Post by TJRC on 2010-05-21
> **asharpham said:**
> I'm pretty new at all this. I have no idea how to do what you're suggesting. Is there any chance you could give me a step by step procedure?

See the step-by-step procedure I posted above:  [http://www.psychocats.net/ubuntu/virtualbox](http://www.psychocats.net/ubuntu/virtualbox)  .  With no prior VirtualBox experience, I followed this Sunday morning while drinking a cup of coffee and watching my kids, and it just plain worked.  The whole process: installing VirtualBox, setting up the Ubuntu VM, and installing Lucid, took about an hour.  Highly recommended.

---

### Post by asharpham on 2010-05-21
Okay, well I tried it when you posted that url but it didn't work for me. It presumes you're using Windows as the host which I'm not. Now I realise it shouldn't make any difference so I'll put that one aside.

The instructions start by explaining how to install Virtualbox which I already have done. I have successfully installed Virtualbox and Windows inside it (My host OS is Ubuntu 9.10). That all works fine.

When I'm told "point the OS settings inside virtualbox for that specific machine to boot from the ISO file directly", I have no idea how to do this as I don't understand what I'm being asked to do. I've tried to work it out but nothing I did worked. I always get the same "FATAL" error message.

Nevertheless, I'll go back to that url and have another look, and try to pick it up at the step where I need to start.

---

### Post by asharpham on 2010-05-21
No, I've tried it every way and it just isn't working. I had no such trouble loading Windows. Every time it either errors out by telling me the file in .Virtualbox already exists or it gives me the "FATAL" error I've mentioned before. I give up.

---

### Post by asharpham on 2010-05-21
Okay. After I spat the dummy in my last message, I tried again and found a way through past the error messages. I now get a black screen with a line of copyright text followed by "boot:". I was expecting to use the iso file from my shared folder so the CD I created isn't loaded.

Do I need to load the CD or do I enter something next to "boot:"? If the latter, what do I type in there?

---

### Post by SVEN1 on 2010-05-21
Now what version of VB are you using?
I had to switch to the newer version before I got 9.10 and 10.04 to work with guest editions.
Once I switched 10.04 runs excellent. I downloaded the 10.04 as a iso file to my deskstop and used it to install 9.10 and 10.04 it's easy once you figure it out.

[http://ubuntuforums.org/showthread.php?t=1459007]("http://ubuntuforums.org/showthread.php?t=1459007")

---

### Post by TJRC on 2010-05-21
> **SVEN1 said:**
> I had to switch to the newer version before I got 9.10 and 10.04 to work with guest editions.  Once I switched 10.04 runs excellent.

I'll bet that's the problem.  I, too, am running a very recent version of VirtualBox.  I'd never used it before, so I downloaded and installed the then-current release 3.1.8 (PUEL) last week.  That would explain what asharpham may not be seeing the same stuff as I.

I notice that they just released 3.2 a few days ago: [http://www.virtualbox.org/wiki/News](http://www.virtualbox.org/wiki/News)

asharpham, what release are you running?  Also, are you running the Open Source Edition (OSE), or the  Personal Use and Evaluation License (PUEL) version?

---

### Post by TheFu on 2010-05-22
> **asharpham said:**
> Okay. After I spat the dummy in my last message, I tried again and found a way through past the error messages. I now get a black screen with a line of copyright text followed by &quot;boot:&quot;. I was expecting to use the iso file from my shared folder so the CD I created isn't loaded.

Do I need to load the CD or do I enter something next to &quot;boot:&quot;? If the latter, what do I type in there?

Did you add the CDROM device or the ISO to your VM settings under "Storage"? See attached.

It appears the "boot from device" setting is not part of 3.1.8 VBox. I know I've used it, but I don't know when it was removed.

---

### Post by asharpham on 2010-05-23
I'm using version 3.1.8. If 3.2 is available I'll load it and try again.

---

### Post by mkvnmtr on 2010-05-23
On 3.1.8 when you open virtual box look on the right and you will see storage. Click on it. when the window opens click on the + beside the IDE controller. In your case it might be sata. That will add your cd drive. Then look around the other optionsuntil you find the boot order. Set it to boot from the cd first.
You might find it a help to download the instruction manual from the same sight that you found Virtual Box on.

---

### Post by asharpham on 2010-05-24
I followed instructions from the last message (even though I now have VB 3.2 which appears to work the same way), but I'm getting the same error message:

 p, li { white-space: pre-wrap; }  "Failed to open a session for the virtual machine Ubuntu 10.04.
 Could not open the medium '/home/alan/.VirtualBox/HardDisks/Ubuntu 10.04.vdi'.
 VD: error VERR_FILE_NOT_FOUND opening image file '/home/alan/.VirtualBox/HardDisks/Ubuntu 10.04.vdi' (VERR_FILE_NOT_FOUND)."

I've been through this so many times, deleting the .vdi file but it keeps coming back and I can't get passed it. I did it once but can't remember what i did. So what's my next step?

---

### Post by asharpham on 2010-05-26
When I press "Start" on my Ubuntu 10.04 entry in VB I get a dos-like window with the prompt "boot:". What do I enter here?

---

### Post by TheFu on 2010-05-26
> **asharpham said:**
> I followed instructions from the last message (even though I now have VB 3.2 which appears to work the same way), but I'm getting the same error message:

 p, li { white-space: pre-wrap; }  "Failed to open a session for the virtual machine Ubuntu 10.04.
 Could not open the medium '/home/alan/.VirtualBox/HardDisks/Ubuntu 10.04.vdi'.
 VD: error VERR_FILE_NOT_FOUND opening image file '/home/alan/.VirtualBox/HardDisks/Ubuntu 10.04.vdi' (VERR_FILE_NOT_FOUND)."

I've been through this so many times, deleting the .vdi file but it keeps coming back and I can't get passed it. I did it once but can't remember what i did. So what's my next step?

So your issues got me to install VirtualBox 3.1.8 on my 10.04 x64 system. There were more than a few errors with the installation for me too. I was able to determine that most of them happened due to the vboxusers group not being created during the installation and my UID wasn't added to the non-existent group.  I was getting **[B]NS_ERROR_FAILURE -38 and Permission Denied errors due to the group issue even though I owned the files and had full authority over them.**[/B] Seems that VirtualBox REALLY wants, no, it DEMANDS, the vboxusers group exist and that any operator be in it.

So, if this was your issue too, I'd recommend that you uninstall the virtualbox packages, remove all the directories like ~/.VirtualBox/ and virtualbox packages, manually create the vboxusers group, add your ID to the group, then reinstall the virtualbox packages.  There's also the /dev/vboxdrv that I fixed permissions on, but after a reboot, I see it is back to root.root and 600 - AND virtualbox is still working fine.

Lastly, I didn't have to do anything related to networking for either NAT or bridge networking to work. That could be because I setup a bridge already for KVM and didn't remove it, or it could be that VirtualBox on Linux handles all networking concerns internally.

I don't think I've forgotten anything important, but here's a blog entry with more specifics. [http://jdpfu.com:82/2010/05/23/installation-of-virtualbox-ose-3-1-x-on-ubuntu-10-04-lucid](http://jdpfu.com:82/2010/05/23/installation-of-virtualbox-ose-3-1-x-on-ubuntu-10-04-lucid)

I just booted a WinXP Home VM and still saw a "Press F12 to select boot device" before WinXP was booted. If you aren't seeing that and have the IDE Primary Master VDI setup (from the VM creation wizard) ... I'm sorry, but I'm at a loss.

Unless it is something stupid, like you have special characters or a space inside your VM name? I can't imagine that is an issue, but I go out of my way to never have spaces in filenames that I control.

---

### Post by asharpham on 2010-05-29
Thanks for the reply. I'll look a bit more closely at this when I have more time but in the meantime, I really don't want to uninstall VB as Win XP is working fine and I don't want to disturb that.

I do get the F12 message when VB  opens and I did have a space in the 10.04 installation filename. Although I also tried to add the same installation just as "Ubuntu" but with the same result. When I set up Windows in VB I did the virtualboxusers thing. Do I have to do it again for each OS in VB or is once enough?

The idea of adding Ubuntu 10.04 to VB was just to try it out to see if I should upgrade or keep what I have. In view of the extraordinary effort to get it working (and ultimately failing) I don't think it's worthwhile persisting.

---

### Post by thelastquincy on 2010-05-30
> **asharpham said:**
> Thanks for the reply. I'll look a bit more closely at this when I have more time but in the meantime, I really don't want to uninstall VB as Win XP is working fine and I don't want to disturb that.

I do get the F12 message when VB  opens and I did have a space in the 10.04 installation filename. Although I also tried to add the same installation just as "Ubuntu" but with the same result. When I set up Windows in VB I did the virtualboxusers thing. Do I have to do it again for each OS in VB or is once enough?

The idea of adding Ubuntu 10.04 to VB was just to try it out to see if I should upgrade or keep what I have. In view of the extraordinary effort to get it working (and ultimately failing) I don't think it's worthwhile persisting.


Is your cd live? You can just try it like that. By rebooting if you have your bios configured right. No need to go virtual.

---

### Post by asharpham on 2010-05-30
Yes of course. Good thinking. Why didn't I think of that! Nevertheless, I would still love to know what I've been doing wrong. But despite many efforts to guide me through it, I don't seem to be able to grasp it. The fact I loaded Windows fine - and it works wonderfully well - I can't work out why it's so difficult for me to load a version of Ubuntu.

Anyway, maybe one day I'll master it - probably when I don't need to any more. And in the meantime I'll run 10.04 from the disk.

---

### Post by TheFu on 2010-05-30
I hate to say this, but sometimes I find that just clicking "next" is the best answer when I'm having issues with any install or configuration. Sometimes I'm too smart for my own good - or smarter than the guy who wrote the installation program in some way. ;)

---

