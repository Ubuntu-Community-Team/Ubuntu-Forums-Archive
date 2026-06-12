---
title: "Choosing installation type when installing through VirtualBox"
date: 2013-02-24
forum: Virtualisation
---

### Post by ruthie84 on 2013-02-24
I have set up Ubuntu as a VM and am now just going through the installation process. The current window wants me to choose an installation type, either "Erase disk and install Ubuntu" or "Something Else". It is also says that the computer does not have any detected operating systems. I have Windows 7 on my computer so I am assuming that this warning pertains just to the virtual server.

My question is whether this assumption is correct and if choosing to erase the disk and install Ubuntu will only erase the virtual drive or will it erase Windows 7 off of my physical drive.

Ruthie

---

### Post by howefield on 2013-02-24
> **ruthie84 said:**
> My question is whether this assumption is correct and if choosing to erase the disk and install Ubuntu will only erase the virtual drive or will it erase Windows 7 off of my physical drive.

Ruthie

You assume correctly, it only sees the virtual drive, hence it saying there is no other operating system ect.

For piece of mind, you should be able to check that on the next screen by looking at the size of the virtual drive.

---

### Post by QIII on 2013-02-24
The installation is only concerned with the virtual disk you have created.  There being no other OS, you should get that message.

However, to reassure yourself, look at the size of the disk being installed to and make sure it is the size you specified when setting up the machine.

If it is, say, 50GB and your physical drive is, say, 1TB, then you are installing only to the virtual disk.

Best wishes!

---

### Post by ruthie84 on 2013-02-24
Thanks for the help! As soon as I clicked on "Install" it showed that it was being installed on the VBox Hardrive. Better safe than sorry though. I would have freaked if I had erased Windows.

Ruthie

---

### Post by Schnappi1989 on 2013-02-25
> **ruthie84 said:**
> Thanks for the help! As soon as I clicked on "Install" it showed that it was being installed on the VBox Hardrive. Better safe than sorry though. I would have freaked if I had erased Windows.

Ruthie

Fortunately you have not freaked!

---

