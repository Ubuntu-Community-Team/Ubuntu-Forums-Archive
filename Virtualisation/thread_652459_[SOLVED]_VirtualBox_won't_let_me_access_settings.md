---
title: "[SOLVED] VirtualBox won't let me access settings"
date: 2007-12-28
forum: Virtualisation
---

### Post by A-dogg on 2007-12-28
I'm running Gutsy 7.10 and downloaded "VirtualBox_1.5.2-25433_Ubuntu_Gutsy_i386.deb" from the VirtualBox website. I install the .deb by double-clicking on it, it installs fine and downloads the necessary dependencies.

I create an XP virtual box, create a 10GB virtual disk with 128MB ram.

I have a CD with Win XP on it in my CD drive.

According to the VirtualBox manual, I'm supposed to then click on settings to mount the CD and then install XP on the virtual drive. When I click settings, what I can only guess is the settings box "half-opens" on top of the virtualBox window (it fades in half-way, but there's nothing written inside it) and then my entire system freezes. I can move my mouse, but the CPU is stuck at 100% of 1.73MHz and nothing on the system responds.

My only option is to hold down the power button to restart. I've tried this numerous times, and even uninstalled VirtualBox and reinstalled. Oddly, it left the downloaded dependencies installed and also still saw the virtual drive I had created (I woulda figured it would uninstall all of that...).

I'm at a total loss. Before I first started VirtualBox, I added myself as a guest to the vboxusers group, but I haven't made any other adjustments.

Anyone have any advice?

---

### Post by empthollow on 2007-12-28
i use virtualbox and i have not had that problem.  the only difference is that i used the version in the synaptic repositories instead of getting the .deb from their web site.  i would try removing and re-installing from repositories to see if that makes a difference. good luck.

---

### Post by A-dogg on 2007-12-29
I may have to try this because even after win xp is up and running on the vbox, I still can't access the settings (to adjust audio, etc) without my whole computer freezing. 

The one in the repositories is the OSE version though. I thought it was a lot better to install the non-OSE version? The VirtualBox website says the non-OSE includes things the OSE one doesn't, like USB support, etc.

Thoughts?

EDIT: after uninstalling, adding the virtualbox repository to synaptic and reinstalling the latest non-OSE version through synaptic, I have XP up and running, but I still can't access the "settings" to turn on USB support and sound. When I click on settings, my entire computer freezes. :(

Is there a way to turn on these features through the command line rather than through the virtualbox GUI? :confused:

---

### Post by A-dogg on 2007-12-31
Can anyone give any thoughts? I really need to turn on USB support -- I have the non-OSE version 1.5.4, so it should be there. But when I click on "settings" or "USB in the right-hand window of the GUI, my computer freezes...

There's no way to just add settings through the terminal that will accomplish this?

Looks like I might have to try VMware server...

---

### Post by A-dogg on 2008-01-01
for whatever reason, it's now working... maybe because I changed the mountubsf.sh (or whatever it's called) to allow the magic access to usb? who knows...

---

