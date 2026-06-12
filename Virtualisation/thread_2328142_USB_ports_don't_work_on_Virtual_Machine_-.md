---
title: "USB ports don't work on Virtual Machine :-?"
date: 2016-06-17
forum: Virtualisation
---

### Post by Pablo W on 2016-06-17
Hi,
In order to use Garmin Express, I have successfully installed a virtual machine (IE 11 on W7) on Ubuntu 14.04 following these instructions: [https://www.youtube.com/watch?v=hjdkWT033W0](https://www.youtube.com/watch?v=hjdkWT033W0)

Nevertheless, I am unable to get the usb ports to work on the virtual machine (VM). When I try to configure the USB port, I get the message "no devices available". This happens only to the VM. Otherwise, all my usb ports work fine on Ubuntu. So, despite the fact that the USB controller is enabled, it looks like the VM just cannot see those ports (see pic attached).

I know nothing about VMs. Any ideas about how to make the VM see my devices connected through USB? 

Thank you.

---

### Post by &amp;KyT$0P# on 2016-06-17
That looks like VirtualBox you're using, right?
If so, few things to check:
1) Have you installed Guest Additions inside the VM?  (with VM running: Devices > Insert guest additions CD; then inside the VM, select to run the program from the CD)
2) Is your Ubuntu (host) user account in the 'vboxusers' group?
3) Under "Sistema" in that settings window you took picture of, is anything disabled/greyed out in any of the 3 tabs there? (it shouldn't be)

---

### Post by QDR06VV9 on 2016-06-17
Thread Moved to Virtualisation seems a better fit.

---

### Post by Pablo W on 2016-06-17
Thank you for your quick reply, halogen2.
Yes, apologies, I forgot to mention that it is Virtual Box (version  5.0.20 r106931e).
The rest of the answers are as follows:

1) I have not installed Guest Additions inside the VM. I do not have a CD reader in my laptop (Samsung ATIV PRO 9 ssd). Should I download and install anything extra via usb from Ubuntu?

2) I am running Virtual Box from my only Ubuntu user. I do have root privileges when running Ubuntu, as long as I type "sudo" at the beginning of the commands line. I have not created any "vboxusers" group in Ubuntu. I have just followed the instructions from this tutorial [https://www.youtube.com/watch?v=hjdkWT033W0](https://www.youtube.com/watch?v=hjdkWT033W0). Should I create a group? I am not sure about how that works.

3) Under Sistema there is nothing greyed out. I have attached three more pics, showing the three tabs under System. I hope this helps. 

Thank you.

---

### Post by &amp;KyT$0P# on 2016-06-17
You're welcome!

1) No need to download or install anything else on your host, and no need for a physical CD.  The Guest Additions CD image should be part of your existing VirtualBox installation.
Just make sure your VM has a virtual optical drive, which it will by default (look under "Almacenamiento" to double-check).

2) VirtualBox should have created the vboxusers group.  Check if you're there by running this command in a terminal:
```
id
```
If its output doesn't mention vboxusers, just add yourself to it:
```
sudo adduser <yourusername> vboxusers
```
Then shut down any running VMs & quit VirtualBox, then log out & log back in.

3) Great, your BIOS/EFI settings should be OK for using VirtualBox :)

---

### Post by Pablo W on 2016-06-18
Thank you halogen2! That solved the issue. 

I will describe what I did so that others can benefit from it as well. Following your steps:

1) I checked and the VM had an optical drive.
2) I ran  ```
id
```  The outcome did not show any vboxusers group, so I ran  ```
sudo adduser <myusername> vboxusers
``` I restarted my laptop. The issue was solved! I could see my Garmin watch (and all devices connected through USB). This is just amazing, because I can update/sync my sports watch in Ubuntu.

Side note 1: My initial question is solved and I will mark this thread as such. Still, I have a final question: When I open Virtualbox, I am prompted to install a newer version (see pic). I have no experience with Virtualbox. For the Ubuntu releases, I always wait until the Long Term Support version is released, for stability reasons (this is my main computer). Would it be safe to install this new version of Virtualbox, or would I run the risk to break everything?

Side note 2: I am a permanent newbie since 2008. I have no words enough to express my gratitude to this forum. You people are just awesome!

---

### Post by &amp;KyT$0P# on 2016-06-18
You're welcome, and thanks for posting the solution! :D

> Still, I have a final question: When I open Virtualbox, I am prompted to install a newer version (see pic). I have no experience with Virtualbox. For the Ubuntu releases, I always wait until the Long Term Support version is released, for stability reasons (this is my main computer). Would it be safe to install this new version of Virtualbox, or would I run the risk to break everything?
First step is to decide if you care about the update: [https://www.virtualbox.org/wiki/Changelog]("https://www.virtualbox.org/wiki/Changelog")
If so, or if you're experiencing a VirtualBox related issue you think a VirtualBox update might resolve, then try updating VirtualBox, but be prepared for in case the update doesn't work out:
 - Make sure you have an installer (.deb or whatever you used) for your current VirtualBox version on hand
 - **Backup your system, including VMs, before updating.  This is very important!**

After updating VirtualBox, if all seems well then install the new Guest Additions in any VMs you've installed Guest Additions.

(Another note, I personally have uninstalled the existing VirtualBox before installing a newer version.  I don't know how necessary that is, but something to maybe keep in mind.  If you do this too, make the backup before uninstalling.)

---

### Post by MAFoElffen on 2016-06-18
Guest additions? Did you mean the appropriate Extension Pack? (current method from version 4,3 on)

Linux version of Virtualbox-- unistall, then install new. Dos not affect VM Guests, as they are in the user's home directories... or in a shared storage space. (not in the program directory).

---

### Post by Pablo W on 2016-06-18
Thank you, halogen2. I appreciate your advice.
 I have just installed VirtualBox for syncing my sports watch. And now that things are working fine, I guess there is no reason for me to update.

Maybe in the future I will find other uses for VirtualBox in Ubuntu.
Thanks again for helping me solve this issue. I love Ubuntuforums. It would be impossible for me to use Ubuntu as my main OS without you.

All the best and until the next time.
Cheers.

---

### Post by &amp;KyT$0P# on 2016-06-18
> **MAFoElffen said:**
> Guest additions? Did you mean the appropriate Extension Pack? (current method from version 4,3 on)
Thanks, actually I mean both but I keep forgetting the Extension Pack is there :oops:
Guest Additions and Extension Pack have both existed since I started using VirtualBox (version 4.1.x I think?), and both provide different sets of functionality.

@Pablo W: for faster USB and other virtual hardware enhancements, get the version 5.0.20 extension pack from [here]("https://www.virtualbox.org/wiki/Download_Old_Builds_5_0") if you haven't already.  (Extension Pack version must match VirtualBox version in order to be stable.)
More explanation about Extension Pack is found [here]("https://www.virtualbox.org/manual/ch01.html#intro-installing")

---

### Post by Pablo W on 2016-06-19
@MAFoElffen: Thanks for pointing me to the Extension Pack. 
@halogen2: Thanks for the link to the manual. I will read it so that I understand what  VirtualBox actually is. 

For the rest, the extension Pack is installed.
I have solved my initial problem (getting my Garmin watch to sync in Ubuntu) and learned something new (there is something out there called VirtualBox which seems to expand the range of things I can do in Ubuntu). Double win for me. I'm very grateful, guys.

---

### Post by &amp;KyT$0P# on 2016-06-19
You're welcome! :KS

---

### Post by pwabrahams on 2016-12-25
I still can't get USB to work, even though I think I've done all the necessary things:

1. I installed V 5.1.12 r112440 (Qt5.6.1) from the VirtualBox website.

2. I installed the Extension Pack from that same website (not the one for 5.0.30).

3. I made sure that my user ID is included in vboxusers.

4. I started up VirtualBox and installed the Guest Additions by (virtually) installing the CD.

But I still can't see my USB devices.  (I right-clicked in the empty box in the USB settings and got the message No Devices Available.)

The virtual machine is Windows 7.  In Kubuntu I can see the memory stick that I inserted into the USB port.

What more can I do?

---

### Post by &amp;KyT$0P# on 2016-12-25
Eject the device from Kubuntu and try again.

---

### Post by Kevin McCready on 2017-07-04
**Youtube vid skipped over Step 4. I have no idea how to "import" the image. I am  now stuck with a zip file and don't know what to do. Please help.**

---

### Post by &amp;KyT$0P# on 2017-07-04
> **Kevin McCready said:**
> **Youtube vid skipped over Step 4. I have no idea how to "import" the image. I am  now stuck with a zip file and don't know what to do. Please help.**
What's inside the zip file?

---

### Post by Kevin McCready on 2017-07-06
Inside the zip is "IE8 - Win7.ova"

But when I go back to virtualbox and click on import, it seems to want an OFV file, not an ova file.

---

### Post by &amp;KyT$0P# on 2017-07-06
.ova files should work fine.  When you try to import the .ova, what error are you getting?

---

### Post by Kevin McCready on 2017-07-07
Failed to open a session for the virtual machine IE8 - Win7.

The virtual machine 'IE8 - Win7' has terminated unexpectedly during startup with exit code 1 (0x1).

Result Code: NS_ERROR_FAILURE (0x80004005)
Component: MachineWrap
Interface: IMachine {b2547866-a0a1-4391-8b86-6952d82efaa0}


[https://twitter.com/kmccready/status/883203801368338433](https://twitter.com/kmccready/status/883203801368338433)

---

### Post by &amp;KyT$0P# on 2017-07-07
So import works, but you can't boot the VM.  Try adjusting the VM settings.

Since I haven't had that specific error before, I don't have any more specific suggestion than that, sorry.

---

### Post by spiv13 on 2017-11-20
Hello there,
thank you for being patient with me.....

I have a laptop running Ubuntu 10.04.
I run Win10 inside VB V5.1.30
I have installed the correct Guest addition.

I Ubuntu files, I can see all my USB attached devices (GoFlex HD, Android Phone etc)
In Windows explorer I cannot see any USB devices.

Can someone tell me what I am doing wrong, please?

---

### Post by &amp;KyT$0P# on 2017-11-20
> **spiv13 said:**
> I have a laptop running Ubuntu 10.04.
Ubuntu 10.04 has been dead for several years now and is no longer safe to use.  Please upgrade to a supported Ubuntu version.

---

### Post by spiv13 on 2017-11-21
> **halogen2 said:**
> Ubuntu 10.04 has been dead for several years now and is no longer safe to use.  Please upgrade to a supported Ubuntu version.

Hoops, sorry, mistype 16.04.

However, I probably found a solution:
[LIST=1]
[*]Start VM 
[*]before starting Win, go 'Settings"  --> "USB" 
[*]select "USB 3.0 (xHCI) Controller 
[*]on the right click the + icon (add USB) 
[*]select the USB hard drive connected. 
[*]repeat for telephone etc. 
[*]restart VM 
[*]Start Windows 
[/LIST]

Now Windows see all my USB and my phone Sync program sees my phone!!!

However, I guess that I would have to "add" a USB device filter every time I plug a different USB device.
Is there a better, permanent solution?

Keep Smiling
Spiv

---

