---
title: "VirtualBox and Symantec Ghost"
date: 2009-01-13
forum: Virtualisation
---

### Post by Keith_Beef on 2009-01-13
I have been trying to explain to my engineers scattered around the world how to use a bootable Ghost CD to restore Windows XP to computers.

The CDs are prepared by the software team, and I write the documentation...

Now it seems that the engineers really, really want to see some screenshots of the ghost software in action...

I had the idea of using a virtual machine within a host OS so that an app under the host os would be able to take screenshots during the "installation" carried out by Ghost.

So here I am, with VirtualBox, trying to boot from the bootable CD.

I've removed the default kvm drivers from the kernel, created my disc space for the VM and I even get as far as seeing a window containing the string "Startng PC DOS..." which is what I see when booting on cold metal.

But then it hangs :(

I thought for a moment that I would need to check "Enable passthrough" for the  CD/DVD drive, but that prevents me from even getting to "Startng PC DOS...".

I'm puzzled... and I don't understand the entries in the log file well enough for them to help me.


```
00:00:06.128 Display::handleDisplayResize(): uScreenId = 0, pvVRAM=0000000000000000 w=720 h=400 bpp=0 cbLine=0x0
00:00:06.128 Guest Log: BIOS: Booting from CD-ROM...
00:00:06.131 Guest Log: BIOS: int13_cdemu function AH=42 unsupported, returns fail
[repeated thirty or forty times]
00:00:06.182 Guest Log: BIOS: int13_cdemu function AH=48 unsupported, returns fail
00:00:13.849 Changing the VM state from 'RUNNING' to 'SUSPENDED'.
00:00:15.699 Console::powerDown(): A request to power off the VM has been issued (mMachineState=8, InUninit=0)
00:00:15.708 vboxClipboardDestroy: shutting down host clipboard
00:00:15.709 Shared clipboard: host clipboard thread terminated successfully
00:00:15.842 ****************** Guest state at power off ******************
```

What's going on here?

---

### Post by lumitoro on 2009-03-11
> **Keith_Beef said:**
> I have been trying to explain to my engineers scattered around the world how to use a bootable Ghost CD to restore Windows XP to computers.

The CDs are prepared by the software team, and I write the documentation...

Now it seems that the engineers really, really want to see some screenshots of the ghost software in action...

I had the idea of using a virtual machine within a host OS so that an app under the host os would be able to take screenshots during the "installation" carried out by Ghost.

So here I am, with VirtualBox, trying to boot from the bootable CD.

I've removed the default kvm drivers from the kernel, created my disc space for the VM and I even get as far as seeing a window containing the string "Startng PC DOS..." which is what I see when booting on cold metal.

But then it hangs :(

I thought for a moment that I would need to check "Enable passthrough" for the  CD/DVD drive, but that prevents me from even getting to "Startng PC DOS...".

I'm puzzled... and I don't understand the entries in the log file well enough for them to help me.


```
00:00:06.128 Display::handleDisplayResize(): uScreenId = 0, pvVRAM=0000000000000000 w=720 h=400 bpp=0 cbLine=0x0
00:00:06.128 Guest Log: BIOS: Booting from CD-ROM...
00:00:06.131 Guest Log: BIOS: int13_cdemu function AH=42 unsupported, returns fail
[repeated thirty or forty times]
00:00:06.182 Guest Log: BIOS: int13_cdemu function AH=48 unsupported, returns fail
00:00:13.849 Changing the VM state from 'RUNNING' to 'SUSPENDED'.
00:00:15.699 Console::powerDown(): A request to power off the VM has been issued (mMachineState=8, InUninit=0)
00:00:15.708 vboxClipboardDestroy: shutting down host clipboard
00:00:15.709 Shared clipboard: host clipboard thread terminated successfully
00:00:15.842 ****************** Guest state at power off ******************
```

What's going on here?

Odd?!?!? No boot from cd on Sun VirtualBox?!?! Is this right?
If so, are you using the nonfree version or the free one? Are you using a admin account or a power user? For what i see in your post you are not a newbie, so by your report the boot from your disk is not supported (this is a very bad way to help you because boot is standard :S). Have you tried setting up an image of your disk (maybe it as errors) or booting from a original xp disk??? I'm not a master in this matters but i'd never had ploblems in booting from Virtualbox VM, using ISO images or the real cd in the cd drive. Passthrough just enables you to use burn apps.

---

### Post by ergosteur on 2009-09-01
Any news on this? I get the same int13_cdemu problem...

---

### Post by Keith_Beef on 2011-10-15
I let this go cold for a long time, but I'm using VirtualBox again for the same task.

This is VirtualBox 4.1.4-74291~Ubuntu~natty.

I can set up a VM, boot from the DVD, PC-DOS starts up and Symantec Ghost runs. As far as I can tell, the process works smoothly, and I can do all the screenshots I want.

But then when I try to boot the Windows XP that this installs, it fails. I get the screen shown in the attached image.

Whatever I choose, I get a very brief glimps of a Windows logo, as if booting has worked, but then this quickly becomes a blue screen with some white text at the top that disappears too quickly for me to read (and I haven't managed to pause it at just the right moment), then it returns to the screen shown in the attached image.


I suspect that this is a mismatch between the hardware for which the disc image was prepared, and the hardware that VirtualBox is emulating.

But any hints of clues that anybody could give me would be very helpful.

---

### Post by CharlesA on 2011-10-15
Have you tried clonezilla instead of ghost?

---

### Post by Keith_Beef on 2011-10-15
> **CharlesA said:**
> Have you tried clonezilla instead of ghost?

Eh? did you not read my post?
Two points:
[LIST=1]
[*]The disc images are made using Symantec Ghost by another team... I have to document their work, but I cannot oblige them to change tools.
[*]The problem is not with Ghost. Virtual Box boots the ghost disc and seems to install just fine, but then won't boot the Windows XP VM.
[/LIST]

---

### Post by CharlesA on 2011-10-15
It's likely giving you a BSOD since it can't access the hard drive. Did the original image come from a VM?

Try using an IDE controller instead of SATA if the hard drive controller is set for that.

---

### Post by Keith_Beef on 2011-10-16
> **CharlesA said:**
> It's likely giving you a BSOD since it can't access the hard drive. Did the original image come from a VM?

Try using an IDE controller instead of SATA if the hard drive controller is set for that.

I had been through the settings to try to match the known target hardware, so it is PIIX3 chipset, IDE controller for the hard drive and CD-ROM drive.

I made a video capture of the virtual machine, and decomposed it into individual frames to catch the BSOD error message, which is in the attached file.

---

### Post by CharlesA on 2011-10-17
That stop error usually means that it's having problems accessing the hard drive. I know that can happen if you clone an XP back onto a VM, since XP expects different hardware and doesn't have the correct drivers.

I checked my XP VM and had the system chipset set to PIIX3 and the IDE chipset set to PIIX4.

---

### Post by Keith_Beef on 2011-10-17
> **CharlesA said:**
> That stop error usually means that it's having problems accessing the hard drive. I know that can happen if you clone an XP back onto a VM, since XP expects different hardware and doesn't have the correct drivers.

I checked my XP VM and had the system chipset set to PIIX3 and the IDE chipset set to PIIX4.

Thanks for your help, Charles.

I'm coming to the conclusion that neither VirtualBox nor qemu-kvm suits my needs in this instance.

Both seem to be limited in the choice of emulated hardware to either PIIX3 or ICH9 chipset and either PIIX3, PIIX4 or ICH9 IDE controller.

I need to emulate
[LIST]
[*]an845GV with some IDE controller (I'm at home, so can't check right now) for one machine,
[*]a Q965 with a some SATA controller for the other machine.
[/LIST]

---

