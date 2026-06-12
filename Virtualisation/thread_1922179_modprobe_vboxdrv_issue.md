---
title: "modprobe vboxdrv issue"
date: 2012-02-08
forum: Virtualisation
---

### Post by sdarnok on 2012-02-08
I've been playing with Vagrant ([http://vagrantup.com/](http://vagrantup.com/)) and upon hitting a wall with incompatible VBox Additions versions - I foolhardy followed these instruction ([http://cisight.com/solve-vagrant-the-guest-additions-do-not-match-the-install-version-of-virtualbox](http://cisight.com/solve-vagrant-the-guest-additions-do-not-match-the-install-version-of-virtualbox)) on the host:
wget -c [http://download.virtualbox.org/virtualbox/4.1.8/VBoxGuestAdditions_4.1.8.iso](http://download.virtualbox.org/virtualbox/4.1.8/VBoxGuestAdditions_4.1.8.iso)
sudo umount /mnt
sudo mount VBoxGuestAdditions_4.1.8.iso -o loop /mnt
sudo sh /mnt/VBoxLinuxAdditions.run

I'm guessing these should have been done on the guest VM, as now the host won't even boot, hanging on the last line of:
 * modprobe vboxdrv failed. Please use dmesg to find out why
 * Starting bluetooth
Starting VirtualBox Guest Additions ...fail!
(modprobe vboxguest failed)
Starting VirtualBox Guest Addition service VirtualBox Additions module not loaded!
 * PulseAudio configured for per-user sessions
saned disabled; edit /etc/default/saned
 * Checking battery state...

In recovery mode, I tried removing "modprobe -r" and "rmmod" on anything that resembles *vbox* - but it just won't go away...  Dmesg does not give me anything meaningful to work with.  Any suggestions?  Is there a global kernel reset I could do?

---

### Post by japzone on 2012-02-08
Yeah, basically you hosed your Graphics, Networking, and a bunch of other stuff by replacing them with the drivers needed in Virtualbox, except your Host Machine isn't running in Virtualbox. Fixing this will require you to somehow reinstall the drivers needed for your PC. I'm not familiar with such a process so you'll need to attract the attention of someone who is. Try renaming the Topic to something like "Screwed up Host while Installing VB" to attract the right people as your current title is abit cryptic.

What I can tell you is that the easiest and quickest fix is to ReInstall Ubuntu. You're files should still be intact so Boot into a LiveCD of Ubuntu and copy your Home Folder and any other Important files to a Safe Location like an External Harddrive just in case they don't servive the ReInstall. Now boot into the Ubuntu installer and Reinstall Ubuntu.

PS: To use the alternative VBGuestAdditions ISO you could of simply booted your VM and in "Devices-->CD/DVD" select the ISO and it'd be mounted into the VM.

---

### Post by CharlesA on 2012-02-08
Try removing the guest additions:

[https://forums.virtualbox.org/viewtopic.php?t=7839](https://forums.virtualbox.org/viewtopic.php?t=7839)

Last post.

It only adds some kernel modules, but that can cause problems if the machine you install them on isn't running in virtualbox.

---

