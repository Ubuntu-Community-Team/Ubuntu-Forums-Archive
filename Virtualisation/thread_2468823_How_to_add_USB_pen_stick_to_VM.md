---
title: "How to add USB pen stick to VM"
date: 2021-11-11
forum: Virtualisation
---

### Post by satimis on 2021-11-11
Hi all

I expect adding an USB pen stick to a VM

Host - Ubuntu 20.04 desktop
VM - Ubuntu 20.04 desktop
Oracl VirtualBox

On Host
USB pen stick - /media/satimis/6242079742076EDB
Files can be retrieved and added to the stick

I already have the extension-pack installed

On VirtualBox Manager
right-click VM -> Settings -> USB
popup screen-1

Please add how can I add the filter?  Thanks

Regards

---

### Post by westie457 on 2021-11-11
Hi maybe this tutorial will be of help to you. [https://forums.virtualbox.org/viewtopic.php?f=35&t=82639](https://forums.virtualbox.org/viewtopic.php?f=35&t=82639)

---

### Post by satimis on 2021-11-11
> **westie457 said:**
> Hi maybe this tutorial will be of help to you. [https://forums.virtualbox.org/viewtopic.php?f=35&t=82639](https://forums.virtualbox.org/viewtopic.php?f=35&t=82639)
Thanks for your link.  I read it before

On
**[COLOR="#FF0000"]#1: Sharing USB devices[/COLOR]**```

[COLOR="#FF0000"]**USB devices cannot be shared at the bus level**.[/COLOR] That means that two computers (a host and a guest) cannot share the same device. Think of it as having a USB stick, a printer, a webcam or a WiFi adapter hooked into two computers at the same time. You simply can't.

There are other means of sharing for some device categories. Such as: shared or network folders for mass storage devices, printer sharing for printer/scanners/fax devices. You simply cannot have direct resource sharing.

```
How can VM get data on the USB pen sticks?  Then the Host must copy all data on the USB pen sticks to the Transfer Folder?

Regards

---

### Post by satimis on 2021-11-11
Hi westie457,

Thanks for your link

Regards

---

### Post by satimis on 2021-11-11
Hi all,

There should be some magic happened here.

Just start the Ubuntu 20.04 VM

On Ubuntu 20.04 VM
-> Machine -> Settings -> USB
clicking the 2nd USB icon, it works now

USB SanDisk 3.2Gen1 [0100]
-> click [OK]

Again on Ubuntu 20.04 VM
-> Devices -> USB
select USB SanDisk 3.2Gen1 
-> OK

Now I can launch the USB pen stick on Ubuntu 20.04 VM, retrieving files and adding files.

I'll check another Linux VM later to see whether God-Of-Luck still standing by me.  Finally I'll work on sharing USB pen stick with Win 10 VM

[B][COLOR="#FF0000"]Edit
==
Remark:[/COLOR][/B]
VM Guest Addition needs following packages to work:
[B][COLOR="#FF0000"]make
gcc
perl[/COLOR][/B]

Regards

---

### Post by satimis on 2021-11-11
Hi all,

Have tried another Ubuntu20.04 VM. USB pen stick can be added.

Coming to adding USB pen stick to Win 10, I found following problem on PC2 Win10
Please see attached photos

PC1 - Windows 10 having top menu, File Machine View etc
PC2 - Windows 10 without top menu

Please advise how to get top menu back on PC2 Win 10

Thanks

[B]Edit
==
Problem solved[/B]

**[COLOR="#FF0000"]Right-Ctrl + C[/COLOR]**
to get the top menu back

After adding Guest Addition

-> Devices -> USB
select USB pen stick

Now I can add USB pen stick to Win 10, browsing the files there

Regards

---

