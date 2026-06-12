---
title: "Need help with a Virtual Box Install"
date: 2016-11-05
forum: Virtualisation
---

### Post by jaredmooretafe on 2016-11-05
Hello

I am trying to install ubuntu-14.04.4-desktop-i386 on a Oracle VM Virtual Box 5.1.8 with little success it worked fine on my desktop but I needed on my study laptop for tech for technical college. I can't seem to get it to work on my laptop below are screenshots of the errors. I am using latest of VB and have to use that version of Ubuntu for my course. Please help as I really need this for my laptop thank you in advance. Jared

[IMG]https://s5.postimg.org/9enzoqwbb/Oracle_VM_Virtual_Box_5_1_8.png[/IMG]

[IMG]https://s5.postimg.org/nz52jkr9z/ubuntu_14_04_4_desktop_i386.png[/IMG]

---

### Post by &amp;KyT$0P# on 2016-11-05
Have you tried just copying your working VM from your desktop machine?  (Copy its entire folder into the laptop's VMs folder, then double-click the .vbox file inside.)

What version of VirtualBox is on the working desktop?

---

### Post by deadflowr on 2016-11-05
*Thread moved to **Virtualisation**.*

---

### Post by Bucky Ball on 2016-11-06
Welcome Bit hard to give much support as you haven't actually told us what the issues are that you are seeing and experiencing in practice, just 'it didn't work'. How doesn't it work? You have not included the full output in the terminal you posted and that might not throw any light, but should be there if you're going to post it.

How didn't it work, what have you tried to fix it, if anything. What is the host OS? Windows? Mac? Another Ubuntu?

---

### Post by jaredmooretafe on 2016-11-06
its exactly the same software version, everything is the same. That's why I stumped it hasn't worked and I have no idea how to do what your suggesting I guess you get it from the app-data folder. I have Win 7 on my Laptop and Win 10 on my Desktop those are the only differences. Will see if I can find that folder and copy it to a portable and await a reply to see where to put it Thanks.

---

### Post by &amp;KyT$0P# on 2016-11-06
> **jaredmooretafe said:**
>  await a reply to see where to put it Thanks.
Same directory as the failed attempt at a VM.  If you don't know - in VirtualBox go to File > Preferences > General.  See where it shows the default machine folder?  Open that folder path in Windows, you likely want to paste the VM folder in there.

Assuming, of course, that the failed attempt at a VM doesn't have the same name.  If it does, delete that from within VirtualBox **before** copying in your working VM.

---

### Post by jaredmooretafe on 2016-11-06
ok I did that and get further then before but now I get this error when I try and start from the vdi when I boot up.

Failed to open the disk image file **C:\Users\jared\VirtualBox VMs\My Ubuntu Machine\My Ubuntu Machine.vdi**.
The medium **'C:\Users\jared\VirtualBox VMs\My Ubuntu Machine\My Ubuntu Machine.vdi'** can't be used as the requested device type.
[TABLE="width: 100%"]
[TR]
[TD]Result Code: [/TD]
[TD]E_FAIL (0x80004005)[/TD]
[/TR]
[TR]
[TD]Component: [/TD]
[TD]MediumWrap[/TD]
[/TR]
[TR]
[TD]Interface: [/TD]
[TD]IMedium {4afe423b-43e0-e9d0-82e8-ceb307940dda}[/TD]
[/TR]
[TR]
[TD]Callee: [/TD]
[TD]IVirtualBox {0169423f-46b4-cde9-91af-1e9d5b6cd945}[/TD]
[/TR]
[TR]
[TD]Callee RC: [/TD]
[TD]VBOX_E_OBJECT_NOT_FOUND (0x80BB0001)[/TD]
[/TR]
[/TABLE]

---

### Post by jaredmooretafe on 2016-11-06
I tried copying over and that didn't work, I followed what you said exactly did it a few times.

Below are my Laptop specs

and the virtual box log file.

[IMG]https://s5.postimg.org/4rr4egnpz/Laptopspecs.png[/IMG]

---

### Post by jaredmooretafe on 2016-11-06
I've zipped up my log files if someone can please have a look for me and tell me as I have no idea what I am doing. Thank you.

---

