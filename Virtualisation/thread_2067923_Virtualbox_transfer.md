---
title: "Virtualbox transfer"
date: 2012-10-08
forum: Virtualisation
---

### Post by marcmeier on 2012-10-08
Hi, All

I'm running 12.04 as host, with MS XP as a VB guest.

I want to move my system to another HDD, possibly under 12.10.

Is there any way to move my existing VB installation, complete with the XP profile, on to the other drive?  Or, do I have to go through the whole XP into VB installation, with the subsequent authentication?

Cheers

---

### Post by cwsnyder on 2012-10-08
You should be able to backup the .vdi file from your /home/{username}/VirtualBox folder.  Make sure you fold in any snapshots, then backup the file.

When you install the new Ubuntu installation and VirtualBox, move your backed up copy of the .vdi virtual disk to the new ./VirtualBox folder, then start up VirtualBox, create a new virtual machine, but when asked to either create a new disk or use an existing disk, answer use existing and point to the old .vdi file.

---

### Post by afz12 on 2012-10-08
In the past I've used the "export appliance" from the pull down list under "files" in Virtualbox and send it to the destination drive. This has the VB appliance say XP as it was in Virtualbox. When you run Virtualbox on another drive/computer then "import appliance" will let you pull everything back in. One advantage is that you can save the appliance to another drive say a USB one for safe keeping and then import from that drive if anything goes wrong in future.

It can take some time to export and import especially if the file is large but having an identical backup copy might be useful later on.

The only hassle you might get is some s/w that Windows needs to register - say Office might loose this and you will need to add the licence key again. If you haven't exceeded the maximum amount then no worries - if you a telephone call and number entry will usually complete the process. Otherwise you may need to select the "call operator" option and they will do it for you. This is usually very straightforward but takes a few minutes.

The export/import approach saves all your files and programs and the OS and so far I've not seen it glitch or fail. Good luck.

---

### Post by marcmeier on 2012-10-09
@afz12 and @cwsnyder

Thank you for the help- it's appreciated.

This thread can be closed.

Cheers

---

