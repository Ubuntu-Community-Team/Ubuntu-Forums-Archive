---
title: "will upgrading to Hardy Heron mess up VBox?"
date: 2008-06-26
forum: Virtualisation
---

### Post by A-dogg on 2008-06-26
So I've been told that it's pretty safe to just use update manager to upgrade to Hardy Heron (as opposed to a clean install from LiveCD). If I do this, will it screw up my current VBox install (non-ose), which is currently working perfectly?

If so, I guess I could use Norton Ghost to make a backup of my XP box and then reinstall, but I wanted to check first...

Thanks!

---

### Post by Twintop on 2008-06-27
Hi A-dogg,

    I upgraded my laptop to Hardy from Gutsy (which was upgraded from Feisty) using the upgrade manager with no problems, and I also use the non-OSE VirtualBox. The only problem you might encounter is that you will need to reinstall the .deb for VirtualBox. Just go to VirtualBox's homepage and grab the Hardy .deb (or even a Gutsy .deb, doesn't matter that much if the latest Ubuntu version isn't available) and install it. As you've probably already figured out, you have to do this for pretty much every kernel upgrade anyway, so the process is exactly the same.

---

### Post by A-dogg on 2008-06-30
Thanks! Do you know if reinstalling the .deb will mess up my XP box that's installed in virtualbox? 

I don't care about having to download and reinstall the .deb, I just want to make sure the XP box I spent so much time setting up remains intact.

---

### Post by Twintop on 2008-06-30
Nope, A-dogg, your VM should still work just the same as before. You will probably have to install a new set of the VirtualBox tools software inside of the virtual machine, though. This being said, backups are ALWAYS a good thing! :)

---

### Post by A-dogg on 2008-06-30
yeah, I'm trying to do a backup, but having trouble. I have norton ghost installed in the xp box, have "pass-through" enabled in settings, and have DVD+-RW drive in the laptop and an external one. But I can't get virtualbox (the XP box) to recognize those drives. It recognizes the interal drive as a DVD-ROM, and doesn't even see the external one.

Do you have any advice on how to fix this, or how you made your back-up?

:confused:

---

### Post by Twintop on 2008-06-30
A-dogg,

I usually just make a backup of the configuration file and the harddisk file for the virtual machine and stick it on another partition or on an external hard drive.

This way if the VM or configuration gets hosed you can just copy over it from your backup. If the new version of VirtualBox doesn't work for you, grab an older .deb release and install from that. Again though, I don't think you'll have any problems with 1.6.2.

As for the DVD burners, the external one is probably USB, correct? You need to bridge it from the VM window to be able to talk to it, and, have USB sharing enabled in the VM's configuration. Not sure why your internal DVD Drive isn't being detected as a burner, though. Is it in passthrough mode?

---

### Post by A-dogg on 2008-06-30
yeah, it is in pass-through mode, that's the weird thing.

I'll try that bridging thing and USB sharing. I'm not with my laptop now, so I'm not exactly clear what you're saying, but it sounds like I have to enable these things once the XP box is up and running (unlike pass-through, which I set up through Settings, which I can only access before the XP starts).

Thanks for all the help. I'll give it a whirl.

---

