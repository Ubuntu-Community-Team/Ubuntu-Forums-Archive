---
title: "Cannot access USB through VirtualBox"
date: 2012-09-29
forum: Virtualisation
---

### Post by Harvey M on 2012-09-29
So I'm running Ubuntu 12.4. I have a VirtualBox setup running Windows XP SP3. I want to be able to transfer files onto that OS through USB. At the moment, Windows will not recognise any USB when I plug it into one of my USB ports.

What is the issue here?

---

### Post by jerrrys on 2012-09-29
Have you installed the "extension pack"?  Its needed for USB support.
[B]
[https://www.virtualbox.org/manual/ch01.html#intro-installing](https://www.virtualbox.org/manual/ch01.html#intro-installing)
[/B]

---

### Post by leclerc65 on 2012-09-29
You have to add your usrid to group 'vboxusers', also create a group named 'usb' then add your usrid to that group too.

---

### Post by blueshead on 2012-10-10
> The vboxusers group

The Linux installers create the system user group vboxusers during installation. Any system user who is going to use USB devices from VirtualBox guests must be a member of that group. A user can be made a member of the group vboxusers through the GUI user/group management or at the command line with

sudo usermod -a -G vboxusers username

Note that adding an active user to that group will require that user to log out and back in again. This should be done manually after successful installation of the package.

This is after you have installed the extensions.

---

