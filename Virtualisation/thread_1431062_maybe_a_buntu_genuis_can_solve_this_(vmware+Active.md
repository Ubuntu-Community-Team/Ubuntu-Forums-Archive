---
title: "maybe a *buntu genuis can solve this: (vmware+Activesync)"
date: 2010-03-16
forum: Virtualisation
---

### Post by Andre-D on 2010-03-16
I am using latest VmWare Workstation for Linux. (on Ubuntu)

and when running XP in Vmware, Activesync cannot connect, mainly because the PocketPC gets detected as an RNDIS device - and a phone-icon appears in Vmware - while Ubunto seems to be unable to release it ?

Anyway: this is pretty much what happens:[http://communities.vmware.com/thread/213565](http://communities.vmware.com/thread/213565)

I'm hoping for a genius is reading this...

---

### Post by VeeDubb on 2010-03-16
I know that this is probably not what you want to hear, since too out of practice to give you any specific direction, but the necessary tools for running activesync already exist in ubuntu.

I believe that [this thread]("http://ubuntuforums.org/showpost.php?p=6258719&postcount=6/") has all the info you're looking for.  Granted, the last time I had to set this up was right after 8.10 came out, so it may be a little outdated now, but it did work.

The one word of caution I will give you, is to pay VERY close attention to what packages you install for this.  I'd recommend writing down each package name, including automatically installed dependencies.

There are a number of different tutorials out there, and if you find that one doesn't work, you'll want to completely wipe everything you've done before trying the next one, because many of them will set up unintended conflicts.


Also, while I hate to steer people away from ubuntu, Mandriva has had automatic setup and configuration of all the necessary software to sync Windows Mobile and PocketPC devices for quite some time.  I was so compelled by their WONDERFUL automatic configuration (which also works with blackbery devices, and several other embedded systems) that I switched to Mandriva for a while when they first came out with it.

Unfortunately, that was the same release where they introduced KDE 4.0, which was a nightmare for me.

Now I have a Palm Pre, which makes syncing with the desktop redundant and useless.  The joys of modern, non-MS technologies.  :D



Edit:  When I say the tools necessary for running active sync, what I mean is "the tools necessary for syncing your PocketPC/Windows Mobile device with your preferred desktop apps on linux."  The actual ActiveSync program remains, "windows only."

---

### Post by Andre-D on 2010-03-16
Hi.
actually, I do not need activesync for syncing (that's done over the internet), it's just to simply explain the kind of connectivity I need to work.

The main reasons is to use a pc-based registry editor (for compare/backup) and flash the device with new ROM.

---

### Post by VeeDubb on 2010-03-16
The kind of connectivity you need, is to pass control of your USB directly to your VM.  I 'think' this possible with a commercial solution like VMware, but I have no idea how to do it.

---

### Post by Andre-D on 2010-03-16
> **VeeDubb said:**
> The kind of connectivity you need, is to pass control of your USB directly to your VM.  I 'think' this possible with a commercial solution like VMware, but I have no idea how to do it.

That's right, I have a licensed VMware, but no support..
the link I provided shows something the OS does, I was hoping this could be prevented somehow..
(a virtual machine with activesync works in VmWare Workstation on windows, but not on Linux.)

---

