---
title: "[Virtualbox] Access created hard disk on Ubuntu"
date: 2015-02-21
forum: Virtualisation
---

### Post by marques.andre.lm on 2015-02-21
Hi!
I created a second hard disk in my virtual machine (virtualbox is running on windows), and i want to know how can i access and mount it on Ubuntu (My virtual Machine).

Thanks!

---

### Post by SeijiSensei on 2015-02-21
Do you mean you have an Ubuntu "guest" running in a Windows "host"?  Where is the second hard disk, on the Windows machine? If so, install the VirtualBox [Extension Pack]("https://www.virtualbox.org/manual/ch04.html") (formerly called the "Guest Additions") in the Ubuntu VM, then shut the VM down.  In the Settings for the VM in the VirtualBox Manager, you'll see a "[Shared Folders]("https://www.virtualbox.org/manual/ch04.html#sharedfolders")" entry.  That gives you a way to share folders from the Windows drive that can be mounted in the Ubuntu VM.

---

