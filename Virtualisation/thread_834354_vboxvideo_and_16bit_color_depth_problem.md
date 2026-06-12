---
title: "vboxvideo and 16bit color depth problem"
date: 2008-06-19
forum: Virtualisation
---

### Post by Virtualpower on 2008-06-19
Hello

I have currently installed Ubuntu 8.04 on my hard drive and would like to run it as a guest OS in XP mostly. I installed guest additions for ubuntu and set VirtualBox to run Ubuntu via raw disk. When I start the VM, an information dialog pops up and says the virtual display is set to 16bit and 32bit is required and thereafter I am thrown into a shell prompt. I am aware to install guest additions but it still doesn't work. I configured in my xorg.conf to set my device driver to "vboxvideo" but to no avail.  

I have a nVidia Quadro NVS 120M graphics card and 1680x1050 wide screen resolution.
 
One other thing, can one run Ubuntu outside the VM with vboxvideo as the graphics driver? I am new to VM and VirtualBox so please excuse my inexperience.

Thanks for any help.

---

### Post by JeyPeyy on 2008-09-30
Hi, I have the same problem. Did you manage to get it right? if so, tell me what you did

---

### Post by marc_hav on 2008-10-24
Press ALT-F2 and enter "gnome-terminal" then click on Run

Use an editor like nano then just type as root: # sudo nano /etc/X11/xorg.conf
Enter your password when asked

Then add the Driver vboxvideo like below, then reboot


Section "Device"
        Identifier      "Configured Video Device"
        Driver          "vboxvideo"
EndSection

---

