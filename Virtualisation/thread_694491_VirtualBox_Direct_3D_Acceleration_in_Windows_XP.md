---
title: "VirtualBox: Direct 3D Acceleration in Windows XP"
date: 2008-02-12
forum: Virtualisation
---

### Post by lightnb on 2008-02-12
I've got an application that requires Direct 3D Acceleration.

It works with my hardware when Windows is running on it's own partition, but doesn't seem to function when Windows is a guest inside VirtualBox.

I need to install the driver for the graphics card, but can you do that? Or is there another way around the problem?

---

### Post by luisromangz on 2008-02-12
The graphics card that virtualization programs make visible to the guest operative system is fake. Instead, it is optimized to enhance the integration of the virtual machine with the host environment.

So I don't think that any virtual machine product provides 3D hardware acceleration.

---

### Post by roaldz on 2008-02-12
If we would have hardware acceleration on VM´s, we could play windows games in linux without the hassles.

---

### Post by bernied on 2008-02-12
I think vmware has a solution for this, but it's not in any of its free products yet.

---

### Post by mr_squall on 2008-11-19
Today VB do no support direct rendering like in parallels =(

---

### Post by Okar on 2009-06-30
the new release of virtualbox will have experimental direct3d and opengl support

---

### Post by EricBaenen on 2012-01-07
VirtualBox 4.1 supports Direct3D (experimental)

[http://www.virtualbox.org/manual/ch04.html#guestadd-3d](http://www.virtualbox.org/manual/ch04.html#guestadd-3d)

In windoze xp you have to install the VB guest extensions in safe mode.

You can force boot in safe mode by using msconfig:

Click on Start, then Run. In the Run dialog box type "msconfig" and press enter to start the msconfigutility.

Click on the Boot tab. Among the checkboxes at the bottom under Boot Options, click the checkbox next to Safe boot and select Minimal (if you really need network access while you are in safe mode you can select Network instead). Click OK.

Reboot, and the computer will boot into safe mode. Once you have completed the installation , you need to reopen msconfig as above and uncheck Safe boot, to boot next into normal Windows mode.

To run some games in windows xp you might need to disable directdraw

Open Start Menu
Open Run
Type DXDiag and press Run
Go to the tab "Display", and disable "DirectDraw"
Notice, that this will disable "Microsoft Direct3D Hardware Acceleration" and "AGP Texture Acceleration".

---

