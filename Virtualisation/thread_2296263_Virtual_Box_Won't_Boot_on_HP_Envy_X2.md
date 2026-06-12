---
title: "Virtual Box Won't Boot on HP Envy X2"
date: 2015-09-24
forum: Virtualisation
---

### Post by Raymond Petit on 2015-09-24
THE PROBLEM:  I have an HP Envy X2 that I've been trying to run Linux from a USB key.  Unfortunately, laptop/tablet hybrid has a non-conforming version of UEFI that has no Legacy Boot option.  The hotkey to get into the UEFI menu at boot up is f9.  I've made a USB Key using LinuxLive choosing Ubuntu 15.04, which will not boot using either the required (f12) or f9.  However, if I load Windows and try running Ubuntu via Virtual Box, it will load but eventually will throw errors.  If I choose the 'Virtualize this Key" option, the process proceeds a little further and I can reach a screen where I can choose to Try or Install Ubuntu.  But, that also fails.  I have attached two logs of failure under both options.  Can anyone read and interpret these logs to shed light on why it fails?  Any help would be greatly appreciated.  I would be totally happy if I can get this working through Virtual Box or if someone can even shed some light of why this USB fails to boot.

HARDWARE:  HP Envy X2 with 2Gb of Ram, Intel(R) Atom(TM), CPU Z2760 1.80GHz, 64Gb SSD (Samsung MCG8GA), 32 bit operating system.

---

### Post by ajgreeny on 2015-09-24
Rather than use a Live USB with Ubuntu "burned" on it you can simply use the ubuntu.iso file you downloaded.

Use the New icon of the VBox window and go through the normal method of making a new VM.

Now when you start the new VM point it to the iso file and it should then go through the same boot process as the live USB though probably a lot quicker, and from the live system you can install the OS to the virtual disk that is now sitting empty in your new VM.  However, I suspect that your hardware spec is not really up to running Ubuntu with the unity desktop which is fairly resource hungry.

There is also an error which is worth dealing with:-
> VirtualBox\data\.VirtualBox\Machines\LinuxLive\HardDisks/LinuxLive.vmdk' has a logical size of 59GB but the file system the medium is located on seems to be FAT(32) which cannot handle files bigger than 4GB.
00:00:01.856283 We strongly recommend to put all your virtual disk images and the snapshot folder onto an NTFS partition"

I am not used to running VBox in Windows, only using Linux hosts, so there may be other problems in this that I have not picked up.
If you still get problems after dealing with this come back again and ask, and I or somebody else will try to help you more.

---

### Post by Raymond Petit on 2015-09-24
> **ajgreeny said:**
> Rather than use a Live USB with Ubuntu "burned" on it you can simply use the ubuntu.iso file you downloaded.

Use the New icon of the VBox window and go through the normal method of making a new VM.

Now when you start the new VM point it to the iso file and it should then go through the same boot process as the live USB though probably a lot quicker, and from the live system you can install the OS to the virtual disk that is now sitting empty in your new VM.  However, I suspect that your hardware spec is not really up to running Ubuntu with the unity desktop which is fairly resource hungry.

There is also an error which is worth dealing with:-


I am not used to running VBox in Windows, only using Linux hosts, so there may be other problems in this that I have not picked up.
If you still get problems after dealing with this come back again and ask, and I or somebody else will try to help you more.

Whoa, you already taught me quite a bit just from that one response!  I know nothing of running VB, but I realize it would be a more than acceptable option if I cannot get this USB to boot.  That error message you point out must refer to the SSD which is 64Gb minus the operating system.  The 4Gb partition which is formatted in fat32 which was recommended by Linux Live.  So, if I get what you're saying it's mismatch that's causing the error.  Making another key as we speak to test whether Ubuntu was too much for this system, another person suggested that, good call!  Will keep appraised.

EDIT:  Lubuntu actually reached the password screen, but I don't have a password.  I have to look up what to do.  I think you were right about the hardware not being able to run the Unity interface as the process was so much faster than when I had Ubuntu installed on the key.

---

### Post by ajgreeny on 2015-09-24
There is no need to make another USB key (memory stick) of another *ubuntu OS; just use the iso file for Lubuntu and point your virtual machine to that at the first screen when you start it the first time.

When you boot that iso file there should be no password needed and if you do get a request for one there must be something corrupt in the iso file; it should boot straight to the Lubuntu desktop from where you can use the install icon on the desktop.

---

### Post by Raymond Petit on 2015-09-24
> **ajgreeny said:**
> There is no need to make another USB key (memory stick) of another *ubuntu OS; just use the iso file for Lubuntu and point your virtual machine to that at the first screen when you start it the first time.

When you boot that iso file there should be no password needed and if you do get a request for one there must be something corrupt in the iso file; it should boot straight to the Lubuntu desktop from where you can use the install icon on the desktop.

Thanks, it was already being made when I read your previous post.  I have someone yacking my ear off right now, so I can't concentrate on this right now, lol!  I'll pick it up later when he is gone!

> **ajgreeny said:**
> There is no need to make another USB key (memory stick) of another *ubuntu OS; just use the iso file for Lubuntu and point your virtual machine to that at the first screen when you start it the first time.

When you boot that iso file there should be no password needed and if you do get a request for one there must be something corrupt in the iso file; it should boot straight to the Lubuntu desktop from where you can use the install icon on the desktop.

Following your instruction, I did the following.  I had no idea what to do with the second or third options.  When I chose the first option, this is the message I got.  I will Google it later, I'm out of time today.  I used both the Lubuntu and Ubuntu .iso images with the same results.

---

### Post by ajgreeny on 2015-09-25
I'll tell you what I always do when using an .iso file direct from hard disk, which is "create a virtual hard disk now" ie, the second option in the list, then at the next screen there will be an option for different file-types for the new VM, where I always use .vdi, the default for VBox as far as I'm aware.  I've never made a new VM using a live USB so I don't really know how different that might be.

It is now that the new hard disk will be made, and when that finishes and you start it in VBox you can point to the .Lubuntu or Ubuntu .iso file at the first screen that you see which will probably look much like my screenshot where I show the opened drop-down box; here is where you browse to the iso file.

Good luck.

---

### Post by Raymond Petit on 2015-09-25
> **ajgreeny said:**
> I'll tell you what I always do when using an .iso file direct from hard disk, which is "create a virtual hard disk now" ie, the second option in the list, then at the next screen there will be an option for different file-types for the new VM, where I always use .vdi, the default for VBox as far as I'm aware.  I've never made a new VM using a live USB so I don't really know how different that might be.

It is now that the new hard disk will be made, and when that finishes and you start it in VBox you can point to the .Lubuntu or Ubuntu .iso file at the first screen that you see which will probably look much like my screenshot where I show the opened drop-down box; here is where you browse to the iso file.

Good luck.
Sorry to have to do this with so much trial and error, but I really don't know anything about VBox.  Anyway, this is where I am at using the first option (with you clarification, I'll next try with the second option).  I did some Googling of yesterdays issue and found PAE/NX needs to be enabled in VM Settings, and I also found a toggle box for EFI and Enable I/O APIC.  Looks like a command line interface which to me is another brick wall, lol!  I get the same result if I try pointing it only at an .iso file on my PC or just try the image on the USB itself.

EDIT:  Followed your exact directions and wound up once again at the command line interface.  I did notice this time that there was an error message that flashed very quickly.  Posting logs soon.

---

### Post by sudodus on 2015-09-26
> **Raymond Petit said:**
> Sorry to have to do this with so much trial and error, but I really don't know anything about VBox.  Anyway, this is where I am at using the first option (with you clarification, I'll next try with the second option).  I did some Googling of yesterdays issue and found PAE/NX needs to be enabled in VM Settings, and I also found a toggle box for EFI and Enable I/O APIC.  Looks like a command line interface which to me is another brick wall, lol!  I get the same result if I try pointing it only at an .iso file on my PC or just try the image on the USB itself.

EDIT:  Followed your exact directions and wound up once again at the command line interface.  I did notice this time that there was an error message that flashed very quickly.  Posting logs soon.

You need PAE, but maybe you can avoid EFI inside VirtualBox.

---

### Post by ajgreeny on 2015-09-26
> **sudodus said:**
> You need PAE, but maybe you can avoid EFI inside VirtualBox.
Yes, definitely avoid EFI in VBox as it is still pretty experimental and as far as I can see not needed, even if the host is using a UEFI boot system, as mine is.

---

### Post by Raymond Petit on 2015-09-26
> **sudodus said:**
> You need PAE, but maybe you can avoid EFI inside VirtualBox.

> **ajgreeny said:**
> Yes, definitely avoid EFI in VBox as it is still pretty experimental and as far as I can see not needed, even if the host is using a UEFI boot system, as mine is.

OK, I'll try without toggling EFI.  However, what does either of you think about that graphical interface?  Was that something to be happy about?

EDIT:  :p:p;);):D:D:o:o!!!!!!!!!!!!!!!

---

### Post by Raymond Petit on 2015-09-26
> **Raymond Petit said:**
> OK, I'll try without toggling EFI.  However, what does either of you think about that graphical interface?  Was that something to be happy about?

EDIT:  :p:p;);):D:D:o:o!!!!!!!!!!!!!!!
Previous post disappeared.  Anyway, it's slow as molasses (both loading and running), no icons on the Desktop except Trash Can and Install, but it does run!!!

---

### Post by ajgreeny on 2015-09-27
Your first screenshot is obviously of Lubuntu running as a live system, not yet actually installed.  Is that live system booted direct from the .iso file or are you still using a live CD or USB, both of which will be slower that from the .iso file?

---

### Post by Raymond Petit on 2015-09-27
> **ajgreeny said:**
> Your first screenshot is obviously of Lubuntu running as a live system, not yet actually installed.  Is that live system booted direct from the .iso file or are you still using a live CD or USB, both of which will be slower that from the .iso file?

It is running as a live system.  I've tried both not creating a virtual machine and creating a virtual machine (like you suggested).  They both run slowly, but your suggested method is less slow.  I was even able to get Ubuntu running last night using your method of creating a virtual machine and then pointing it at the Ubuntu .iso.  It's glacial compared to Lubuntu, lol.  I'm now looking at manually renaming bootmgfw.efi to BOOTX32 or 64.EFI and copying it to the flash drive.  I think I have found all the commands, but my talkative friend has found me, so I can't focus right now.  I have no plans yet of installing anything unless or until the boot problem gets solved.  Running directly form the flash drive still results in a Username/Password screen that is unpassable since there is no previously set password.

---

### Post by sudodus on 2015-09-28
If you run live it should bring you to the desktop directly, you should need no login and no password. But if your system for some (yet unknown) reason stays at the login screen, try with the username **lubuntu** and with no password (just press the Enter key).

---

### Post by Raymond Petit on 2015-09-28
> **sudodus said:**
> If you run live it should bring you to the desktop directly, you should need no login and no password. But if your system for some (yet unknown) reason stays at the login screen, try with the username **lubuntu** and with no password (just press the Enter key).
You are correct, it's up and running and this is why I think for your average user, details are important!  This time I noticed something I hadn't seen before, "Persistence Mode" in the top spot of choices.  It's been so long since I've used Linux, I'd forgotten that you can tap any key to get away from that list of languages that obscures the screen when it's loading.  I discovered that little gem of info during my search a few days ago and that's how I finally was able to see the full list of choices.  Now, I'm wondering if I can edit the boot file from here?  I have obtained a modified Grub2 file that can boot on any system with this hardware if I can copy it to the right place on the flash drive.  Will keep you appraised.

Edit:  I'm wondering if editing the mount point could possibly have any effect of how Windows views the USB and mounts it?

---

### Post by sudodus on 2015-09-29
If you edit files in a normal live session it will be gone after reboot, but if will survive if you are running a persistent live session. See this link and links from it for more details.

[Try Ubuntu (Kubuntu, Lubuntu, Xubuntu, ...) before installing it](http://ubuntuforums.org/showthread.php?t=2230389)

I don't know if editing the mount point has any influence (except changing the name). Avoid special characters (spaces, asterisks etc).

---

### Post by Raymond Petit on 2015-09-29
> **sudodus said:**
> If you edit files in a normal live session it will be gone after reboot, but if will survive if you are running a persistent live session. See this link and links from it for more details.

[Try Ubuntu (Kubuntu, Lubuntu, Xubuntu, ...) before installing it](http://ubuntuforums.org/showthread.php?t=2230389)

I don't know if editing the mount point has any influence (except changing the name). Avoid special characters (spaces, asterisks etc).

Persistence mode doesn't work, remember, it takes me to that screen with the sign in.  Actually, let me stop right there, I forgot to take your suggestion of the work-around to that.

EDIT:  It's loading in Persistence Mode right now.  Yesterday I went back to the other USB I made with a Windows utility for making bootable USB's.  This was after I found out how to view the interior file structure on the one made with LILI (it doesn't have the proper file system for booting EFI, but the one made with the Windows utility does).  So I copied that boot32 file I got off the internet and that got me to a command line interface.  Have not found the proper code to actually boot, however, after quite a bit of searching.

EDIT:  Using "Lubuntu" "lubuntu" after loading in persistence mode does not work.

EDIT:  I copied the Windows bootmgfw.efi to the flash drive naming it BOOTX64.efi.  Gave boot error!

EDIT:  The good news is that I have two separate USB drives that boot directly into Linux, no need to press f9!  The bad news is it boots into a Command line interface which does me absolutely no good!  I've been searching for commands all over the internet to not avail.  I've gotten the message 'no kernel loaded' several times, but can find no way to load it because I just don't know anything about command code.  I'm at a loss!  What I've learned is that the best option was using that Windows utility to create the bootable drive because it creates the proper file system that has /boot/efi.  If that is not present there is no way to boot this thing.  Another thing I've learned is that bootia32.efi file I found online works albeit, taking you to the Command prompt.  The third thing I've learned is that someone made 2 separate Debian .iso files that can boot in the same way.  I made that bootable drive using Rufus and it installed the correct file structure unlike the other files I was using.  I'm putting this down for now and will seek help in the HP Forums where someone with this unit might be able to make use of the information I've stumbled upon.  At the least I can use virtual box to run Linux on this thing although it's tremendously slow.

I did a little more searching last night and I simply do not know enough to get any commands codes working.  I think what I will have to do is have someone with that knowledge look at this machine in person to see if they can boot the kernel.  That is just too much for me.  I'm guessing that since the computer now boots directly into the Linux command line without the need to press f9, it is just a matter of getting it to boot the kernel via commands.  I am troubled, however, that I still don't see any type graphical interface offering options for booting like it should.  So, now with the USB installed prior to boot, instead of booting into Windows every time with no options, it now boots into Linux with no options.  Thanks for your help!

---

### Post by sudodus on 2015-10-01
'It boots into linux with no options'.

Is this a success? What works, and what does not work? Are you booting linux directly or inside VirtualBox?

---

### Post by Raymond Petit on 2015-10-01
> **sudodus said:**
> 'It boots into linux with no options'.

Is this a success? What works, and what does not work? Are you booting linux directly or inside VirtualBox?

Like I said, it boots from the flash drive directly, into a command prompt 'grub>_' and that's it!  If I knew command code, it would be short work at this point, but I don't.  Booting from VirtualBox (that is configured properly) will take me to the Lubuntu or Ubuntu desktop depending upon which flash drive I'm using.  I can also boot using VirtualBox without having any flash drive connection at all by just pointing it to the Lubuntu or Ubuntu files.

---

### Post by sudodus on 2015-10-02
It is good that Lubuntu and Ubuntu work via VirtualBox. What about the speed and stability: Is it working well enough to be useful?

It is too bad, that it still does not work when booted directly. I am not sure that it is enough to know the available commands in grub, because the computer's UEFI system is different from the standard, and the Lubuntu and Ubuntu iso files may not fit for your computer. Anyway, the grub commands can be found at the following links (and links from them)

[gnu: grub commands](https://www.gnu.org/software/grub/manual/html_node/Commands.html#Commands)

[herman546: grub2 commands](http://members.iinet.net/~herman546/p20/GRUB2%20CLI%20Mode%20Commands.html)

---

### Post by Raymond Petit on 2015-10-03
> **sudodus said:**
> It is good that Lubuntu and Ubuntu work via VirtualBox. What about the speed and stability: Is it working well enough to be useful?

It is too bad, that it still does not work when booted directly. I am not sure that it is enough to know the available commands in grub, because the computer's UEFI system is different from the standard, and the Lubuntu and Ubuntu iso files may not fit for your computer. Anyway, the grub commands can be found at the following links (and links from them)

[gnu: grub commands](https://www.gnu.org/software/grub/manual/html_node/Commands.html#Commands)

[herman546: grub2 commands](http://members.iinet.net/~herman546/p20/GRUB2%20CLI%20Mode%20Commands.html)

Looking over the commands.

---

