---
title: "Help, dx won't work!!!"
date: 2008-06-01
forum: Windows
---

### Post by crazyfuturamanoob on 2008-06-01
I got windows xp on my virtual machine and ubuntu as my
main os. All I do with windows is to play games. But now
I'm wondering, why the games wont work. What I did, is:

1. I downloaded dx9 installer with ubuntu.
2. I packed it into .iso with Brasero.
3. I mounted the .iso with VirtualBox.
4. I extracted the stuff from the dx9 installer to
c:/programfiles/dx9
5. I ran the dx9 installer in that folder, and booted
the computer (the virtual one).

But for some reason direct3d is missing, along with hardware 
acceleration. Did that installer install _anything_???
And how to get it working?? HELP!

---

### Post by fiddledd on 2008-06-01
Last time I checked VirtualBox didn't support Direct3D and it won't for a couple of years, if at all. Apologies if I'm not up to date on this.

---

### Post by crazyfuturamanoob on 2008-06-01
Huh!? WTF!? Why is that???? :confused::confused::confused:

---

### Post by jrusso2 on 2008-06-02
Because a virtual machine is just that a virtual computer with virtual hardware.  For DX to work it needs direct access to the hardware.

But breakthrough's are being made and the pay for Parallels and Vmware has some Direct X support.

---

### Post by crazyfuturamanoob on 2008-06-02
so virtual computers are useless

---

### Post by rickyjones on 2008-06-02
> **crazyfuturamanoob said:**
> so virtual computers are useless

Virtual machines are very far from useless. They were not created or meant to be a high performance replacement for 3D graphical computers.

VMs are great for virtualizing servers and workstations applications.

Try VMWare Workstation - I thought that I heard that they were close to 3D acceleration in the VM.

-Richard

---

