---
title: "Blank screen w/ Flashing Cursor after Fresh Install (Grub Not Running)"
date: 2017-05-22
forum: Ubuntu/Debian BASED
---

### Post by ciscoengin33r on 2017-05-22
Hi All,

Firstly, let me preface this by saying I am a Network Engineer; I speak in TCP/IP, so this is not my wheelhouse.  I am trying to use Elementary OS, which is basically Ubuntu. I have an ASUS KF52 laptop that used to have Windows 7 on it. I loaded up the Elementary OS liveCD and installed it to the entire drive so that the laptop is a single boot machine, wiping out Windows.  There are no problems with the install, and it tells me to remove the live CD and reboot, so I do.  However, once the laptop restarts, it goes to a blank screen with a white blinking cursor that doesn't take any input. 

I did about 13 hours of research and trial and error in trying to fix this and have gotten nowhere.  The problem is 95% of the available self help in correcting this problem assumes you can get to the terminal to edit files, and you are running a dual boot scenario.  See below:

1. **_sudo gedit /etc/default/grub and add nomodeset before/after quiet splash_** - Theory here is that graphics card is to blame and nomodeset will fix it. But I can't get to the terminal. If I could get to the terminal, that would mean I can get to the GUI, which would mean grub is running correctly, which would mean I wouldn't be having this problem. That said, if you put the live CD in and press the down arrow, it will go to the Elementary OS install page and if you press F6, it gives you the option to append additional parameters to the install, one such parameter option is to add nomodeset. There are 5 other parameters you can use as well.  I have tried multiple combinations of these parameters on about 6 fresh installs to no avail.

2. **_Press shift, or cntl+alt+f1, or cntl+e or <insert keystroke here> to bring up the grub boot menu and make necessary changes:_** This doesn't work because it is a single boot environment. I do not receive a boot selection menu like you would if you have a dual boot laptop, asking you which OS you want to boot. It automatically goes straight to the blank screen with the white cursor after the "ASUS" hardware information comes up once the power button is pressed. No keystroke works, when I mash them or hold them.

3. **_Perform remounting:_** Shouldn't need to be done because I am using the entire disk, not a partition, and I can't get to the terminal to do this anyway.

4. **_Change the boot order in the BIOS and/or disable UEFI:_** Can't specifically tell the BIOS to boot grub/linux. I can only tell it to boot from MATSHITADVD, HDD, USB or LAN. Disabling UEFI doesn't make a difference. 

I spoke with a colleague and without him seeing the laptop himself, he suspects that the BIOS boot needs to be pointed at grub and not at the Windows instance that no longer exists. However, I have no idea how I can do that if my system BIOS doesn't give me an option beyond HDD, CDROM, USB and LAN, and if I cannot bring up the boot loader with <insert keystroke here>.

Any help would be most appreciated.

Thanks.

---

### Post by QIII on 2017-05-22
*Moved to **Ubuntu/Debian BASED***

---

