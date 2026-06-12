---
title: "Transfering VirtualBox installed Guest OS to ther partition"
date: 2009-10-13
forum: Virtualisation
---

### Post by ubfu on 2009-10-13
Currently using VirtualBox.I had install a Guest window XP on ubuntu.The file and Guest os is at home folder ".VirtualBox/Machines"

I plan to move it to other partition rather than the same partition ext3 which ubuntu is installed after listening to someone's advice.
[http://ubuntuforums.org/showpost.php?p=8031156&postcount=10](http://ubuntuforums.org/showpost.php?p=8031156&postcount=10)
I didn't have a separate hard disk but will test on another partition first.

Thank you.

---

### Post by ubfu on 2009-10-15
How to transfer guest os to other partition ? Any help please ?

---

### Post by ubfu on 2009-10-16
PLease anyone know how to transfer guest os to other partition ?

---

### Post by howefield on 2009-10-16
Use the "Export Appliance" function within Virtualbox. You'll find it in the File menu.

You can also use the clonevdi option, eg

VBoxManage clonevdi source destination

---

### Post by xebian on 2009-10-16
> **ubfu said:**
> How to transfer guest os to other partition ? Any help please ?

Just move the xp_name.vdi to your desired partition and VBox will complain about not finding it.  Then you can add it in the HD setup.

---

### Post by ubfu on 2009-10-17
I manage to find out that my hard disk is just 1.6 GB but the snapshot take about 7GB of space.

Is it dangerous to move the snapshot to other location ? I just wanted to free some space.

There are 3 snapshots with different size.3.4GB , 2.4GB and 700mb .Is it find to remove one of it to other partition ?

---

### Post by howefield on 2009-10-17
See the last post in this thread.

[http://forums.virtualbox.org/viewtopic.php?t=791](http://forums.virtualbox.org/viewtopic.php?t=791)

---

### Post by ubfu on 2009-10-20
I am confuse with the cloning instruction .
Let say , if I change my hardware like motherboard and processor will I able to boot the guest os on other partition ?

---

### Post by ubfu on 2009-12-15
Really need help , anyone kind enough to guide me ? Thank you

---

### Post by b0b138 on 2009-12-15
There is no point in moving it to another partition if its still the same disk.

---

### Post by ubfu on 2009-12-16
I allocated 20GB for ubuntu installation and virtualbox guest os (window xp) size keep increasing which I run out of space .

I had other partition 30GB free that I which to transfer it to the partition.

It maybe simple for virtualbox user , but as for me newbie , I know nothing on transfering.The only way I know is cut the folder and paste on the partition which I am surely know it doesn't work.

Hope someone kind enough giving me a guide on transfering to other partition.Been stuck with it for months with just 300mb left on my ubuntu partition.

Thank you

---

### Post by ubfu on 2009-12-18
Please I really need help transferring my current guest OS to other partition :(

---

### Post by ubfu on 2009-12-21
Any help or guide ? still waiting :(

---

### Post by SecretCode on 2009-12-21
The VirtualBox forums are very helpful - forums.virtualbox.org. You are much more likely to find answers to this problem there.

> **ubfu said:**
> There are 3 snapshots with different size.3.4GB , 2.4GB and 700mb .Is it find to remove one of it to other partition ?
Why do you have snapshots? If you are a beginner in vbox you shouldn't really be using them.

---

