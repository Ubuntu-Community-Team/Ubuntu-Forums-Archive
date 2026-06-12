---
title: "Server 8.10 installed on Poweredge 2500, no boot"
date: 2008-12-04
forum: Server Platforms
---

### Post by sethtriggs on 2008-12-04
At work, I'm starting to try to practice with managing servers, so I started out with a heavy floor-model Dell Poweredge 2500. On this, I decided to install Ubuntu Server 8.10.

After figuring out how to get the RAID started (there are four Seagate Cheetah 36.5GB drives) and configured (it has one container with two clusters, making a usable size of 67GB), I was able to install Server with no problems. Or so I thought.

Once post-install reboot occurred, things seemed normal. First the regular Dell splash, then the Adaptect SCSI manager does its rounds with everything OK, then the Dell RAID system comes in, saying there's one container with the 67GB. Finally, it says "BIOS installed successfully!" The cursor jumps lines a few times like it's trying to get started. But it just hangs with the flashing cursor, and I know it should've started up by now.

I wonder what possible things I can do to see where I've gone wrong with this install. I wonder if I chose an option wrong. Is it possible that I messed up the system by using a "Set up RAID" option in Ubuntu Server? Does that make it impossible to get the system working?

Thanks in advance...

-Seth C Triggs

---

### Post by lykwydchykyn on 2008-12-04
Here's what I would try:

 - Boot to either an ubuntu liveCD or something like PartedMagic, and take a look at the partitions on the RAID.  Did the system files get put on them, or are they empty?
 - If that all looks right, use a partition editor like gparted or cfdisk to make sure the /boot (or /, if you don't have a separate /boot partition) is marked bootable. I've forgotten to do this before, and it's made the system behave like this.
 - If that's right, try reinstalling GRUB from the server CD.  I believe it's an option if you go into the "rescue a broken system" option.

---

### Post by sethtriggs on 2008-12-04
> **lykwydchykyn said:**
> Here's what I would try:

 - Boot to either an ubuntu liveCD or something like PartedMagic, and take a look at the partitions on the RAID.  Did the system files get put on them, or are they empty?
 - If that all looks right, use a partition editor like gparted or cfdisk to make sure the /boot (or /, if you don't have a separate /boot partition) is marked bootable. I've forgotten to do this before, and it's made the system behave like this.
 - If that's right, try reinstalling GRUB from the server CD.  I believe it's an option if you go into the "rescue a broken system" option.

Okay, I will give that a try tomorrow.

I should note that I was not able to use a regular Ubuntu (desktop) CD on this system, though that test was admittedly before I learned about the whole RAID container thing.

-Seth

---

### Post by sethtriggs on 2008-12-09
Just as I feared, the Ubuntu liveCD does not function properly; it simply goes to the BusyBox v 1.1.3 after I do the "Try Ubuntu without any changes..." option.

And the prompt is (initramfs)

What can I do about this?

Thanks in advance.

-Seth

---

### Post by lykwydchykyn on 2008-12-09
How is the CD connected to the system?  SCSI/SATA/IDE?

This usually happens when for whatever reason GRUB on the CD cannot find the CD drive to load up the actual OS (weird, I know, since it's on the CD itself.  Can't say I completely understand it).

Going back over your post, I don't think you needed to use the "set up RAID" option on the CD.  I think that's for setting up a software RAID, which you don't need because you've got a hardware RAID controller taking care of the RAID.  The drives should look like one big hard drive to the OS.

---

### Post by sethtriggs on 2008-12-09
> **lykwydchykyn said:**
> How is the CD connected to the system?  SCSI/SATA/IDE?

This usually happens when for whatever reason GRUB on the CD cannot find the CD drive to load up the actual OS (weird, I know, since it's on the CD itself.  Can't say I completely understand it).

Going back over your post, I don't think you needed to use the "set up RAID" option on the CD.  I think that's for setting up a software RAID, which you don't need because you've got a hardware RAID controller taking care of the RAID.  The drives should look like one big hard drive to the OS.

It appears to be a SCSI CD drive.

Should I rerun the Ubuntu Server installation without the software RAID install then?

-Seth

---

### Post by lykwydchykyn on 2008-12-09
That's what I'd do.

---

### Post by sethtriggs on 2008-12-10
> **lykwydchykyn said:**
> That's what I'd do.

Rats, it didn't work - I set it to not activate the RAID, it found the container OK, but it did not load the system at all.

Yet the LiveCD won't work either, which kinda sucks. I wonder what I can do now.

-Seth

----

I used the Rescue a broken system option in the Ubuntu Server CD, and installed the boot loader to (hd0). I also checked the shell on the bootable device and it showed the requisite /dev, /home, etc. folders.

Then I rebooted and it got me through GRUB (big progress from before), and then the "Loading, please wait..." comes up. 

Then it says:

"gave up waiting for root device. Common problems:"

After that, there was the issue of:

ALERT! /dev/disk/by-uuid/e7... does not exist. Dropping to a shell!

And then it gives me BusyBox.

So a little more progress, but still no joy. The *ls* command in initramfs does show that there are folders (though no home folder) like dev, lib, bin and others.

---

### Post by lykwydchykyn on 2008-12-10
Ok, what I think I know what is happening here, but the exact steps to fix are a bit hazy to me.  Basically, it sounds like the initrd doesn't have a driver for your SCSI controller. (if you're not familiar with it, the initrd is an initial ram driver that the kernel loads on boot so that it has drivers for the basic hardware to get booted).

You can regenerate a new initrd with the drivers added, but I am honestly not sure how.

Just as a side note, can you post the /boot/grub/menu.lst file, or at least the default entry in it?  I had an annoying problem once with Debian and a PE2950 that just required a quick edit to menu.lst, I wonder if your issue is similar.

---

### Post by sethtriggs on 2008-12-10
> **lykwydchykyn said:**
> Ok, what I think I know what is happening here, but the exact steps to fix are a bit hazy to me.  Basically, it sounds like the initrd doesn't have a driver for your SCSI controller. (if you're not familiar with it, the initrd is an initial ram driver that the kernel loads on boot so that it has drivers for the basic hardware to get booted).

You can regenerate a new initrd with the drivers added, but I am honestly not sure how.

Just as a side note, can you post the /boot/grub/menu.lst file, or at least the default entry in it?  I had an annoying problem once with Debian and a PE2950 that just required a quick edit to menu.lst, I wonder if your issue is similar.

Now there's something puzzling:

On a lark, I decide to just type "exit" in the shell since I have no idea of what else I can do at this point.

The shell drops and all the services (Samba, MySQL, etc.) start for the server.

What appears to be a normal startup goes all the way through, getting me to the $ prompt.

So apparently I get a successful boot by doing things this way.

When restarting after this, Boot does go normally, and then it hangs a while on Loading, please wait...

Then it dumps me to Busy Box again. Typing in (exit) gives me the normal boot process and then it loads.

Interestingly, if I hit ESC during the GRUB prompt and select the first image, I don't get dumped into BusyBox and the system boots normally. Curiouser and curiouser.

-Seth

---

### Post by Linc1 on 2008-12-10
I need a solution to this problem. I am running a Dell PE2650 and get the same error. It drops out of the boot and into the busybox and initramfs prompt. This machine has an adaptec SCSI card so why wouldn't that be supported out of the box. I need to get this running on THIS machine.  Any help would be great

[email]Linc@QuickLinc.com[/email]

Linc

---

### Post by lykwydchykyn on 2008-12-10
> **sethtriggs said:**
> 
Interestingly, if I hit ESC during the GRUB prompt and select the first image, I don't get dumped into BusyBox and the system boots normally. Curiouser and curiouser.

-Seth

Now that's odd... maybe the drives just aren't ready?  Try increasing the timeout value in /boot/grub/menu.lst.

---

### Post by lykwydchykyn on 2008-12-10
By the way, while I'm thinking of it, I will recommend to both of you to download the latest BIOS and SCSI firmware updates from Dell for these machines.  I've had numerous instances with Dell hardware where Linux compatibility issues are fixed by BIOS updates.

---

### Post by Linc1 on 2008-12-10
I have already done the BIOS update but not the SCSI so I will get on that one right away.   I am confused about you hitting esc. At what point during the boot did you do that?

Linc

---

### Post by sethtriggs on 2008-12-11
> **Linc1 said:**
> I have already done the BIOS update but not the SCSI so I will get on that one right away.   I am confused about you hitting esc. At what point during the boot did you do that?

Linc


You hit ESC once the GRUB Loading... message shows up. It'll have the countdown from 3, so you'll need to be quick.

Then select the first option with Enter and it should work right away.

Also I've been able to get into the system from initramfs by typing exit at the prompt. The system continued on to normal boot.

As for updating a BIOS I must admit I'm a bit scared to do that.


-Seth

---

### Post by Linc1 on 2008-12-11
When hitting ESC I am given three options. The first one drops back to the same failure. The second one (repair) eventually hangs and I can type exit and get a login prompt. I am then able to login but no GUI On reboot I end up where I started.   I have tried the other option of the exit and gotten no where. 

About to give up and call it a windoz box, that installs everytime without issue. Sadly. I have five of these servers and each of them gives the very same response when I try to install this OS.

Linc:confused:

---

### Post by lykwydchykyn on 2008-12-11
> **sethtriggs said:**
> 
As for updating a BIOS I must admit I'm a bit scared to do that.


-Seth

It's not scary, not with Dell usually.  I don't know about the 2500, but with the 2850s and 2950s they have a boot disc image you can download that does it all automagically.

Most BIOSes in the last 5-6 years have a sort of "safe-mode" they revert to if something goes wrong with the update, so that you don't totally brick the motherboard.

---

### Post by Linc1 on 2008-12-11
Well I tried using the information found here:

[http://forums.scotsnewsletter.com/index.php?act=ST&f=14&t=5025](http://forums.scotsnewsletter.com/index.php?act=ST&f=14&t=5025)

and when I did it shows me two partitions, 0 and 4. But there were no kernels found on either of the partitions. This is really buggy.

Linc :mad:

---

### Post by sethtriggs on 2008-12-12
> **lykwydchykyn said:**
> It's not scary, not with Dell usually.  I don't know about the 2500, but with the 2850s and 2950s they have a boot disc image you can download that does it all automagically.

Most BIOSes in the last 5-6 years have a sort of "safe-mode" they revert to if something goes wrong with the update, so that you don't totally brick the motherboard.


Okay, I'll give it a try. What text editor do you recommend, by the way, for the Bash for editing the Boot.LST?

-Seth

---

### Post by lykwydchykyn on 2008-12-12
> **sethtriggs said:**
> Okay, I'll give it a try. What text editor do you recommend, by the way, for the Bash for editing the Boot.LST?

-Seth

Whatever you're comfortable with.  I've gotten used to vim, but most people find that nano is more like what they're used to.  Nano's a good deal faster, too, though on a poweredge you shouldn't notice.  They'll all work for the task.

---

### Post by sethtriggs on 2008-12-12
Setting the timeout to 30 worked! Now the system boots properly without any interaction. So it was as you suspected; the disks were not ready.

I found a USB floppy so I can make the BIOS upgrade image. Do wish me luck.

Thank you so very much, thank you! I am very grateful to you for your assistance, lykwydchykyn!

-Seth

On edit: Turns out this server already had the latest BIOS (A07, as I downloaded from the website) - so everything is OK.

---

### Post by vordude on 2009-01-22
Okay, I'm having a similar issue with a PowerEdge 2500.

Here's my abridged startup process (I was typing as it was booting.


> -"Dell" Startup screen,
-embedded server management and primary system backplane controller firmware information

-Processor information 

-Raid Controller
-Press Ctrl A for the raid config util
-Booting controller kernel....Controller Started

-Waiting for Controller to start, controller started.

-Controller Post operation successful
-Controller memory sixe 128MB

-Container #0 - Mirror 68.35 GB Optimal
-1 Container(s) Found

-Bios Installed Successfully! 



And then Nothing. 
(well a flashing cursor)

Esc doesn't do anything... I don't know where to go.



I have latest Bios. and Latest SCSI Firmware... 

I'd like to edit the   /boot/grub/menu.lst  but cant seem to.  how do I edit the file?  When I do a "Rescue a Broken System" with the disk in, I get to a shell, but can't find the file--

Thanks,

---

### Post by lykwydchykyn on 2009-01-22
Sounds like grub did not install.  Did you get any errors during installation?

---

### Post by vordude on 2009-01-22
No Errors, The install went smoothly.

---

### Post by vordude on 2009-01-22
Then again, I'm not sure...

while in rescue mode, I try to reinstall grub--

and get a 

> Executing 'grub-install /dev/sda1/' failed.

This is a fatal error.

---

### Post by vordude on 2009-01-22
I installed LILO via the "rescue a broken system" and it appears to work.

Am I down the right path?

---

### Post by lykwydchykyn on 2009-01-22
If it's booting, then yes.  I can't immediately think of any reason not to run LILO on a server, with any luck you'll rarely be seeing the bootloader.

---

