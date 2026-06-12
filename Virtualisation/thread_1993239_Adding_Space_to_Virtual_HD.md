---
title: "Adding Space to Virtual HD"
date: 2012-06-01
forum: Virtualisation
---

### Post by teejay17 on 2012-06-01
Can I add "virtual" space to my virtual drive? I'm using VirtualBox, running Windows XP virtually, and I made the mistake of setting up the HD too small, and I will need to expand it soon ...

---

### Post by haqking on 2012-06-01
> **teejay17 said:**
> Can I add "virtual" space to my virtual drive? I'm using VirtualBox, running Windows XP virtually, and I made the mistake of setting up the HD too small, and I will need to expand it soon ...

you can or add and attach another drive.

If that ever happens to me i create another drive, attach it, boot the to a clonezilla disk and clone it to the new disk then unattach the original

there are conversion tools though

---

### Post by deadflowr on 2012-06-01
I don't know if you can expand a drive but you can add drives.
In virtualbox go to settings, then storage, click the add hard drive icon in the top right of the box(IDE contollers), choose create disk drive make a new drive, done, it would probably be added as a D,E, or F drive.

---

### Post by CharlesA on 2012-06-01
I've tried increasing the size of the VHD but I wasn't able to get Windows to see it as a larger drive.

It was easier to just reinstall.

---

### Post by haqking on 2012-06-02
> **CharlesA said:**
> I've tried increasing the size of the VHD but I wasn't able to get Windows to see it as a larger drive.

It was easier to just reinstall.

just do as i said above, create a larger one, attach it, clone existing to new attachment.

Works a like a treat

Peace

---

### Post by CharlesA on 2012-06-02
> **haqking said:**
> just do as i said above, create a larger one, attach it, clone existing to new attachment.

Works a like a treat

Peace
Thanks for that. :)

---

### Post by teejay17 on 2012-06-02
> **deadflowr said:**
> I don't know if you can expand a drive but you can add drives.
In virtualbox go to settings, then storage, click the add hard drive icon in the top right of the box(IDE contollers), choose create disk drive make a new drive, done, it would probably be added as a D,E, or F drive.

Virtual Windows XP doesn't seem to detect the new drive I created. Is there something else I must do in order for the new drive to be detected?

---

### Post by inashdeen on 2012-06-02
just make a new drive :)

---

### Post by Cheesemill on 2012-06-02
You don't have to create a new drive, you can increase the size of the existing on using VBoxManage. For example:
```
VBoxManage modifyhd --resize 15000 filename.vdi
```will increase the size of filename.vdi to 15GB (15000MB).

This will only increase the size of the disk and not the partition size, so you then need to boot the VM from a Live CD and use Gparted to resize your partition to take up the free space on the disk (or use Windows' built in disk management tools).

---

### Post by inashdeen on 2012-06-02
that's a nice tip. thanks cheesemill

---

### Post by haqking on 2012-06-02
> **Cheesemill said:**
> You don't have to create a new drive, you can increase the size of the existing on using VBoxManage. For example:
```
VBoxManage modifyhd --resize 15000 filename.vdi
```will increase the size of filename.vdi to 15GB (15000MB).

This will only increase the size of the disk and not the partition size, so you then need to boot the VM from a Live CD and use Gparted to resize your partition to take up the free space on the disk.


Just a tip on that, i have used that before and it does work but as CharlesA said above depending on the OS (for me it was with certain XP VM's) it wont always see the new size of the drive, booting to gparted did see the new drive size however as you say.

It was due to this which made me start creating new disks and then cloning them instead, of course this may have been an older vbox issue as its been over a year since i did this and had any issues.

Peace

---

### Post by teejay17 on 2012-06-02
> **inashdeen said:**
> just make a new drive :)

I did. I just need to get XP to somehow detect it as a SATA drive. Right now it is detecting the new drive, but when it tries to install the driver for it, I get the message "cannot find driver, try installing from internet, etc."

---

### Post by deadflowr on 2012-06-02
In the virtual XP, open the control panel, go to performance and maintenance,go to administrative tools, go to computer management, click on disk management, you should see your original disk and the new one you set up. The  new disk will be unallocated and uninitialized. Initialize the disk and then create a new partition.

---

### Post by deadflowr on 2012-06-02
> **teejay17 said:**
> I did. I just need to get XP to somehow detect it as a SATA drive. Right now it is detecting the new drive, but when it tries to install the driver for it, I get the message "cannot find driver, try installing from internet, etc."

Have you perused this page, it might help.

[https://forums.virtualbox.org/viewtopic.php?t=42829]("https://forums.virtualbox.org/viewtopic.php?t=42829")

---

### Post by CharlesA on 2012-06-02
> **haqking said:**
> Just a tip on that, i have used that before and it does work but as CharlesA said above depending on the OS (for me it was with certain XP VM's) it wont always see the new size of the drive, booting to gparted did see the new drive size however as you say.

It was due to this which made me start creating new disks and then cloning them instead, of course this may have been an older vbox issue as its been over a year since i did this and had any issues.

Peace
Yeah, that's what I did, but neither Gparted nor XP saw the drive as larger as it originally was.

That was on VBox 4.x as well.

---

### Post by teejay17 on 2012-06-03
> **deadflowr said:**
> In the virtual XP, open the control panel, go to performance and maintenance,go to administrative tools, go to computer management, click on disk management, you should see your original disk and the new one you set up. The  new disk will be unallocated and uninitialized. Initialize the disk and then create a new partition.
Thanks. That did the trick.

---

