---
title: "How do I boot my virtual machine from a Live CD/DVD?"
date: 2016-10-22
forum: Virtualisation
---

### Post by caraj on 2016-10-22
I'm trying to expand the storage space on my VM, following the instructions on this page:[ https://www.linuxbabe.com/virtualbox/how-to-increase-virtualbox-disk-size-for-dynamically-allocated-disks]("https://www.linuxbabe.com/virtualbox/how-to-increase-virtualbox-disk-size-for-dynamically-allocated-disks")[URL="https://www.linuxbabe.com/virtualbox/how-to-increase-virtualbox-disk-size-for-dynamically-allocated-disks"]
[/URL]
At the point where it says 
> Although your virtual disk size is increased, your guest OS can’t use  all of them right now. So you need to boot your virtual machine from a  Live CD/DVD that contains Gparted to enlarge the file system of your  guest OS.

 To boot your virtual machine from a Live CD/DVD, follow these steps.
 Open you virtual machine settings and click **Storage** on the left pane.

Under storage tree, click **Controller: IDE** then click the optical drive icon to add a Live CD/DVD image file. I use the ubuntu live ISO file because it contains Gparted.
Now click System on the left pane, in Boot Order, make sure Optical is  first on the list. Save your settings and start your virtual machine.


The instructions stop working. I've put a live DVD into the optical drive, but the VM doesn't seem to register it, so I can't follow the last four steps.

---

### Post by &amp;KyT$0P# on 2016-10-22
Can you please post a screenshot of your VM's Storage settings?

What live DVD are you trying to use?

---

### Post by caraj on 2016-10-23
[ATTACH=CONFIG]271741[/ATTACH][ATTACH=CONFIG]271742[/ATTACH][ATTACH=CONFIG]271743[/ATTACH]
I'm trying to boot from an Ubuntu 16.04 DVD. But I can't figure out how to get the VM to boot from it. I also tried going to the F12 boot menu and selecting 'boot from CD', but it tells me there is no CD.

---

### Post by Habitual on 2016-10-23
I usually just boot the ISO, but not sure there is a BIOS to access honestly.

---

### Post by &amp;KyT$0P# on 2016-10-23
If you are using a physical CD, you don't choose an optical disk file.

At the bottom of your VM settings, it says "Invalid settings detected".  What does it say when you mouse over that icon?

---

### Post by caraj on 2016-10-23
> At the bottom of your VM settings, it says "Invalid settings detected".  What does it say when you mouse over that icon?
It just warns me that my guest OS has more than 50% of the computer's RAM.

> If you are using a physical CD, you don't choose an optical disk file.
My VHD was 25GB and now it's 100GB, but it won't let me access the new 75GB. How can I make it do this?

---

