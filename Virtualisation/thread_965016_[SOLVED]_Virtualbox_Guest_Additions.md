---
title: "[SOLVED] Virtualbox Guest Additions"
date: 2008-10-31
forum: Virtualisation
---

### Post by nathand28 on 2008-10-31
After I have mounted the Additions.iso file in the VB menu, I can't run it in Ubuntu , and whenever I type in the command for it in a terminal:
Sudo sh ./VBoxLinuxAdditions.run , and this doesn't seem to work, I get the error:
Sh: Can't open ./VBox"".

If I try to run it I get:
This program must be run with administrator privileges aborting.

Am I missing something obvious, such as an error in code?
I have read chapter 4 of the manual, and the code their doesn't seem to work.

Any help is appreciated.

---

### Post by nathand28 on 2008-10-31
Ok I fixed it:
First, you need to install VirtualBox guest extensions:
- In the VirtualBox menu, Devices -> "Install Guest Additions"
- Then, mount them: Devices -> Mount CD/DVD-ROM -> CD/DVD-ROM Image
- Select VBoxGuestAdditions.iso

Open a terminal (Applications -> Accessories -> Terminal)
- sudo apt-get install linux-headers-generic
- mount /media/cdrom (If you get an error that it's already mounted, ignore the error)
- sudo /media/cdrom/VBoxLinuxAdditions-x86.run
(wait)
- Reboot the virtual machine.
[https://answers.launchpad.net/ubuntu/+question/47938](https://answers.launchpad.net/ubuntu/+question/47938)

---

### Post by Brian FitzGerald on 2009-12-30
Thanks a lot for posting this.  Came in very handy for me.

---

### Post by boxterduke on 2010-03-29
I just want to thank the OP for posting this. Helped me a lot while installing guest additions.

---

