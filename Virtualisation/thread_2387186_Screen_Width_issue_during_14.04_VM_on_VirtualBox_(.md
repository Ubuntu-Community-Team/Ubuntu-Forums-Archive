---
title: "Screen Width issue during 14.04 VM on VirtualBox (Windows 7 Host)"
date: 2018-03-15
forum: Virtualisation
---

### Post by jaraqui2 on 2018-03-15
I have a Windows 7 notebook and I installed VirtualBox 5.1.26 on it.


I tried to install Ubuntu 12.04 as a Virtual Machine on VirtualBox, but during the keyboard choosing/test phase I could not resize the screen!

When I dragged the window increasing its width, a blank space region was created, and Ubuntu did not enlarge its width to allow me to press the "Continue" button.


Here is the screen with the problem


[https://s13.postimg.org/junouh99j/teclado.jpg](https://s13.postimg.org/junouh99j/teclado.jpg)


Does anybody know how to solve this?

---

### Post by wildmanne39 on 2018-03-15
*Thread moved to **Virtualisation, a more appropriate forum**.*

Please use the attachment facility by clicking on the paperclip or use url's for images because apart from bandwidth issues for some, it makes it difficult for those using mobile devices to browse the forum.

Did you click on the maximize button to make the window larger? that might work instead of dragging it. I would try to install 16.04 LTS version, you said you are installing 12.04 in the post but 14.04 is listed in the title, 12.04 is no longer supported and 14.04 I believe will not be soon. I also recommend installing virtualbox 5.2.

---

### Post by &amp;KyT$0P# on 2018-03-15
> **jaraqui2 said:**
>  I could not resize the screen!

When I dragged the window increasing its width, a blank space region was created, and Ubuntu did not enlarge its width 
That feature requires Guest Additions installed in the VM.

---

### Post by jaraqui2 on 2018-03-16
> **halogen2 said:**
> That feature requires Guest Additions installed in the VM.

Thank you for your reply, but I tried to install guest additions and another problem appeared.
The "Device" menu option is not present.

Inspecting how to solve this problem, I found the following recommendation: "The Device menu option is presented when the virtual machine is running".
But, how can I run my virtual machine if I am still installing it?

I am supposing that Virtual Machine running corresponds to an already operating system installed.

Is the above recommendation correct? Is there another way to install guest additions?

---

### Post by cruzer001 on 2018-03-16
Alt + Left click

[https://ubuntuforums.org/showthread.php?t=2335603](https://ubuntuforums.org/showthread.php?t=2335603)

---

### Post by Habitual on 2018-03-19
I noticed this same behavior on my Vbox 5.2.8 on Mac High Serra.
I was forced to utilize the tab key and hope that a tab <enter> would proceed.
It did.
Re-sizing the guest window did not help. 
Believe I was installing a mini.iso for my Elastic Stack 6 "lab".

Just sayin'

---

