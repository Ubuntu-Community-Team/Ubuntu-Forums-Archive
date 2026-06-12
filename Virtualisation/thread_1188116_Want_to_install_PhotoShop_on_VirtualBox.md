---
title: "Want to install PhotoShop on VirtualBox"
date: 2009-06-15
forum: Virtualisation
---

### Post by felinoel on 2009-06-15
I want to use VirtualBox to run Adobe programs like PhotoShop, but it is not installing? Do other people have problems with PhotoShop on VirtualBox? It isn't the discs because I tried it on another computer and it worked fine.

It says it is either running in Safe Mode or the Windows Installer is not installed, any thoughts as to why it says that?

---

### Post by lukeiamyourfather on 2009-06-15
As far as the Adobe installer is concerned it shouldn't even know its in a virtual machine. What version of Windows is the guest and what version of Photoshop is being installed? Make sure the guest operating system is supported with the version of Photoshop. Cheers!

---

### Post by felinoel on 2009-06-20
> **lukeiamyourfather said:**
> As far as the Adobe installer is concerned it shouldn't even know its in a virtual machine. What version of Windows is the guest and what version of Photoshop is being installed? Make sure the guest operating system is supported with the version of Photoshop. Cheers!

XP and CS2... so I shouldn't be having this problem?

---

### Post by juancarlospaco on 2009-06-20
I have Photoshop CS2 on Ubuntu.

---

### Post by felinoel on 2009-06-24
> **juancarlospaco said:**
> I have Photoshop CS2 on Ubuntu.How did you get it to install?

---

### Post by Marlonsm on 2009-06-24
There is a program called Wine (you can find it on Add/Remove) that runs programs for Windows inside Ubuntu. It's not perfect yet, but runs Photoshop CS2 very well.

After Wine is installed, just right click > "Open with Wine" the Photoshop installer.

---

### Post by konqueror7 on 2009-06-24
[HowTo: Installing PS CS2 on Wine]("http://appdb.winehq.org/objectManager.php?sClass=version&iId=2631")

---

### Post by juancarlospaco on 2009-06-24
Because i have Adobe Photoshop CS2 on .deb  :)
Double click to install it

---

### Post by munishvit on 2009-06-25
Does anybody know how to share clipboard from Host (using Ubuntu 9.04) to Guest (Windows XP) on Virtual Machine 2.1.4_OSE?
I have already set General>Advanced>Shared Clipboard Settings to "Bidirectioal". Still its not working??

---

### Post by felinoel on 2009-06-25
> **Marlonsm said:**
> There is a program called Wine (you can find it on Add/Remove) that runs programs for Windows inside Ubuntu. It's not perfect yet, but runs Photoshop CS2 very well.

After Wine is installed, just right click > "Open with Wine" the Photoshop installer.

I tried Wine, I will try Konqueror's link

---

### Post by philcamlin on 2009-06-25
yeah even cs3 installs in wine :popcorn::popcorn:

---

### Post by fjgaude on 2009-06-25
> **munishvit said:**
> Does anybody know how to share clipboard from Host (using Ubuntu 9.04) to Guest (Windows XP) on Virtual Machine 2.1.4_OSE?
I have already set General>Advanced>Shared Clipboard Settings to "Bidirectioal". Still its not working??

That's why I stopped using VBox years ago... and now after years of successful clipbaord exchanges between WinXP and Ubuntu up to 8.10, 8.04 doesn't quite work... it does until you use other than Ubuntu to WinXP. <sigh>

Well, at the same time going to 9.04 I updated from VMware 1.06 to 1.08, I wonder if its the 1.08 that's at issue. Don't know!

---

### Post by munishvit on 2009-06-27
> **fjgaude said:**
> That's why I stopped using VBox years ago... and now after years of successful clipbaord exchanges between WinXP and Ubuntu up to 8.10, 8.04 doesn't quite work... it does until you use other than Ubuntu to WinXP. <sigh>

Well, at the same time going to 9.04 I updated from VMware 1.06 to 1.08, I wonder if its the 1.08 that's at issue. Don't know!

Well, synchronizing clipboard is not that much necessary. It seems, with VirtualBox you got some others issues too..

---

