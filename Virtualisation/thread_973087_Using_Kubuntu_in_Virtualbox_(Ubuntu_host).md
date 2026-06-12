---
title: "Using Kubuntu in Virtualbox (Ubuntu host)"
date: 2008-11-06
forum: Virtualisation
---

### Post by zoomy942 on 2008-11-06
My host machine is Ubuntu 8.10, and I wanted to try out Kubuntu, so I tossed it into a VirtualBox.  Everything went fine, but I dont know how to get the equivilant of guest additions set up.  I have an XP VM, and the screen work/resize just fine and the mouse moves between the host and guest fine, but i dont know how to enable this in Kubuntu.

---

### Post by the yawner on 2008-11-06
If you're running the virtual machine, either click Devices > Install Guest Additions, or just mount the VBox Guest Additions ISO. Then in Kubuntu, open up a terminal and type the following

```

cd /cdrom
ls

```

You should see the contents of the ISO. If you're using Virtualbox 2.0, lookup for the file VBoxLinuxAdditions-x86.run (for 32-bit) or VBoxLinuxAdditions-amd64.run (for 64-bit). To install guest additions type:

```

sudo ./VBoxLinuxAdditions-x86.run
or
sudo ./VBoxLinuxAdditions-amd64.run

```
These are the installation scripts for Linux OS equivalent to the exe file.

---

### Post by zoomy942 on 2008-11-06
Thanks!

that worked great!  i had trouble finding it because i kept googling the word "seamless" and thats totally something different.

---

