---
title: "Ubuntu server 13.10 installation hangs at language selection"
date: 2013-10-25
forum: Server Platforms
---

### Post by msandoy on 2013-10-25
Hi.

I have been trying to install Ubuntu server 13.10 on my Eee Box 1012, 1.6 dual core Atom CPU, nVidia ION chipset. It locks up the computer at the language selection screen during install.
This computer has been running Ubuntu server for 3 years now, just updating at every new release. I replaced the HD (for a larger and quicker one), hence the complete new install.
There is no CD drive, so it has to be done via USB.
I have been trying to make bootable USB drives from two different sticks, and with two different computers, (one running Xubuntu 13.04 64bit and one with Xubuntu 13.10 64bit) from three completely separate downloads of ubuntu server 13.10 iso files. I have tried using USB-CREATOR and UNetbootin, and they all hang. Even tried with --noacpi as a boot option from the boot menu.
The strange thing is, I can make the USB stick with Xubuntu 13.10 live cd iso, and do a install of this one without any problem at all.
Does anyone know how to make the server installation work?

---

### Post by chrisguk on 2013-10-25
I wouldnt bother using graphical software to burn your images to USB.  You can achieve it quite easily with the following:

```

sudo dd if=/the/file/location.iso of=/dev/sdX   (X being the drive.  This would normally be "b" if you have one physical disk and just one USB device plugged in)

```

Im not an Atom Guru but have you checked that the latest kernel shipped with 13.10 works correctly with your cpu and are you using the correct architecture, for example 32 bit or 64 bit

---

### Post by msandoy on 2013-10-29
I actually tried using dd also, with the same result. 
The Atom CPU in my box, is 32 bit, I used the i386 release of Ubuntu server. Seems to be a problem with the installer.
I managed to set up a Xubuntu 13.10 32 bit desktop system, removing the auto start of GUI. It performs the same way as the previous server distro that was installed on this machine.
Basically, I have given up on the server distro. Using tasksel in the desktop distro, I get the same basic software installed.

---

