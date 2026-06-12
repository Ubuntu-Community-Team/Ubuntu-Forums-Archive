---
title: "VirtualBox can't start virtual machines"
date: 2010-07-02
forum: Virtualisation
---

### Post by GeoMX on 2010-07-02
I have a new Lucid installation, remembering the OS edition of VirtualBox does not include USB support I added the required repositories and installed virtualbox-3.2, I created a virtual machine and installed Windows XP as guest, the installation took a lot of time, I didn't know why until I tried to start the VM, it freezed every now and then, without aparent reason. I tried some solutions I found on the web (adding a nohz to the kernel command line and forcing async_tsc), none of them worked.

I had another machine with the OS edition of VirtualBox and a guest Windows XP working without problems, so I removed virtualbox-3.2 and installed virtualbox-ose, but now I can't even start a virtual machine, I get error messages (I attach images).

I don't seem to find info about these problems, have you experienced similar problems?

Any help is appreciated.

---

### Post by sh1ny on 2010-07-02
/etc/init.d/vboxdrv setup

---

### Post by scrooge_74 on 2010-07-02
Permissions to the VM file?
Hard drive errors? <-- I had this issue once

---

### Post by gdonwallace on 2010-07-02
I had some similar problems my self.

It could be a hard drive problem (the virtual hard drive or your actual hard drive.)  Might suggest deleting that VM you installed and starting over.

Also, if you have Ubuntu installed on ext4, that can cause some odd issues with the VM.  Go into the settings for the for storage.  The first option, IDE Controller, there is an option there "Use Host I/O cache"  Make sure that there is a check in that box.  

Hope it helps.

---

### Post by GeoMX on 2010-07-02
It seems my hard drive is the problem :(.

After installing latest updates for Lucid, I could start the VM and runned very well, but every now and then my whole system fails to start correctly, and again I have problems with the VM.
I've checked and my disk (my actual "physical" drive) has some erroneous sectors :frown:, thanks a lot for your help, I didn't imagine it could be the problem :p.

---

