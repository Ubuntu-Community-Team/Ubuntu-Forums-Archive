---
title: "Hell and Bliss with VMS"
date: 2008-04-24
forum: Virtualisation
---

### Post by 0xdeadc0de on 2008-04-24
This is a documentary post of my experiences with VM's. Since all the latest distro's are consumed by them, I figured I'd see what all the buzz is about. I was under the dillusion I could run directx at first, like many people new to VM's. I quickly found out this is not the case. I _can_ get DX to work however in vmware, although, with the bugs they mention in their documentation. KVM, Qemu, VirtualBox, VMWare

First I started with kvm. My first mistake was to try to boot an existing windows xp install on the hard drive, while linux had it mounted with ntfs-3g. It booted, loaded the boot loader located on my mbr (grub), I selected windows and booted. It worked a couple times, but it was asking me to re-activate. So I try, but the network connection didn't seem to work, as such I couldn't activate it. 

After a couple tries with different command lines, windows started to refuse to boot, missing or corrupt files in system32/ .. I check with Yakuake (Quake like konsole), the files are there still.. funny.. I extract the compressed files from the backups hp left on the hard drive, 1 by 1 getting rid of the missing/corrupt errors, only to find the registry was corrupted as well. Great. I tried the hp system restore utility (in "non-destructive" mode), all it ended up fixing was grub, so I could no longer boot into linux.
I ended up using the Ubuntu 7.10 live cd, running sudo grub /dev/sd0, root (hd0,4), setup(hd). to restore grub (Although, now that it's restored it reports as being 7.10 Gutsy intead of 8.04 Hardy, oh well)
(On a side note, I was able to boot up the same copy of 8.04 Hardy in the VM that the host was; So the guest and host were the same OS on the same partition, and the host still works after reboots)

The original copy of windows on my laptop is no longer use-able. I'll probably end up using the "destructive recovery" provided by the utility left on another partition by hp (Which is actually a hibernated copy of winxp with the utility running), after I get all my media and documents backed up and off the partition.

So my next move was to find another copy of windows. 

Finally get my hands on a copy after a couple hours, and start back up. KVM at first. I created a 5gb vmware image, and used kvm to install winxp on it. The install goes fine - once I figure out how to change the cdrom image and or "refresh" the device (ctrl+alt+2, info block, find cdrom block, eject it, change it to (ex: info block, eject ide1-cd0, change ide1-cd0 winxp/disk2.iso ) -But, after the eject command switch back to the vm window(ctrl+alt+1), let it run for a second, to recognize the eject has occurred (It didn't always work for me otherwise)

In the Guest winxp I set the machine to standard pc instead of acpi multiprocessor to help improve guest performance, and disabled windows xp's graphical enhancements.

The only problem, KVM keeps locking up my host machine - but only(bite my tongue) does so if it's going to when I launch it. While it's running it seems to have no problems. The last KVM launcher script I used ended up as: kvm -no-acpi -smp 2 -boot c -usb -m 512 -hda /media/bighome/windows -cdrom /dev/cdrom1 -net nic,model=ne2k_pci -net user

So I now tried the next hotly talked about VM, VirtualBox. Wow, I love it. So easy to set up the machine using the existing image. Then I tried the virtualbox add-on tools. Very nice. My windows music (and flash videos/veoh tv etc) all was being pumped through PulseAudio, Flash Videos play smoothly (as a small window, when fullscreened the flash videos begin to tear - Unless I fullscreen using the compiz zoom plugin ;))

The one thing lacking, the only thing missing, any kind of DirectX support. This is understandable as it's probably the single most daunting task in writing a VM that requires more interpretation and communication in the software than probably any other part of the system (Translating directx calls to opengl calls, maintaining some kind of pipe between the guest os and the actual video card - without interfering with xorg, whatever has to be done I don't know I don't write VM's... )
Which I heard VMWare can do.

I got VMWare, used the any-any wifi patch 116 (Ended up having to modify a #define in the patch by hand to let it compile as well, yeesh)
Finally get VMWare up and running, try to boot up the KVM/VirtualBox winxp, it's in the vmware format after all. Yay, it starts to boot but then, crash. Blue screen error every time it tries to boot. (It still works in virtualbox, maybe it was the vbox addons?)

So I created yet another image, installed windows again in vmware.
The first problem, vmware uses OSS for audio. No big deal right? Pulseaudio has their utility padsp to wrap up OSS apps and pump it through PA. Wrong. padsp doesn't seem to work "right(tm)". I'm not sure what it's doing, but it allows VMWare to play sound - but not through pulseaudio. It comes out the laptop speakers directly - and only if they're not already in use. (Better than vmware's default setup which never allows sound to play..). 

Before I forget, I tried vmwareesd for the audio problem, which only created a new problem - Lag. When playing audio the VM would nearly come to a halt, which made watching flash videos impossible. This "lag" isn't seen when using padsp to play it through .. whatever it ends up sending it through (alsa perhaps?)

Then I tried DirectX, and, well, it works, but there are all those bugs they mentioned. Vmware tools are cool too once installed.


In the end, I'm probably going to stick with VirtualBox, seamless mode is very cool although quirky, and it's fast enough for the most part (Although VMWare starts windows MUCH faster every time. I've defragmented the VBox one, not the vmware one, the vmware one still boots way faster). But the largest selling point on VirtualBox for me was PulseAudio support in the end, Second largest is the easy graphical setup, and the less work to get things done (no typing to change cd's for example). Good sound is very important to me when all I have to play sound by default are these tiny laptop speakers! Although, VMPlayer recognized my built-in usb camera and was able to activate it in windows.
:guitar::popcorn:

**Edit: One huge reason VBox could be booting much slower than VMware - which makes absolute sense, the image is located on an sshfs mount and not local, whereas the vmware image is on the local hard drive.

---

### Post by Mic_Droz on 2008-07-25
Good post mate, I think I'll be heading in this direction soon... just have to work out if there actually is any way to boot straight off the recovery partition, seeing as my laptop came with no discs... Hope I can work out how to do it!

---

