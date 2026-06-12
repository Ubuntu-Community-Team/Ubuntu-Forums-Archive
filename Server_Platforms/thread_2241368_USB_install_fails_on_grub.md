---
title: "USB install fails on grub"
date: 2014-08-25
forum: Server Platforms
---

### Post by m0rph3us0306 on 2014-08-25
I am trying to do a simple USB install (14.04).   I am booting off a USB and the grub-install part fails.  The USB is mounted as /dev/sda and the only hard-drive is /dev/sdb.

It's partitioned with;
/dev/sda1 - boot, flagged bootable
/dev/sda2 - swap
/dev/sda3 - / root filesystem

I get the error (and you see if flash) it's trying to install to /dev/sda.   In the installed you can jump to a shell, but there is no grub-install, just grub-installer and the device command doesn't help, so is there such a command to force it to /dev/sdb as I will be removing the usb!

Thanks.

---

### Post by oldfred on 2014-08-25
Auto installs default to install to sda. If your system is one that promotes flash drive to sda, then it installs grub to flash drive and you then cannot reboot flash drive to repair system. :( 

In that case the best way to install is something Else and on the partitioning screen where it says drive to install boot loader change to the hard drive. If hard drive is sdb then that is where you want boot loader.

       Install 14.04 Something Else explanation and screenshots (note boot load to VM, most may install to MBR of drive sda, or sdb)
[http://www.tecmint.com/ubuntu-14-04-installation-guide/](http://www.tecmint.com/ubuntu-14-04-installation-guide/)

 Lots of detail, screenshots and essential info.14.04  Something Else example
[http://www.dedoimedo.com/computers/ubuntu-14-04-install-guide.html](http://www.dedoimedo.com/computers/ubuntu-14-04-install-guide.html)

   Any install with Something Else which is required with  external drives or any second drive or any install with separate /home
Also shows combo box with location of grub2 boot loader
[https://help.ubuntu.com/community/Grub2/Installing](https://help.ubuntu.com/community/Grub2/Installing)

---

### Post by m0rph3us0306 on 2014-08-25
Thanks oldfred.

The all 3 links show what looks like a desktop OS install (this is a server install) so the installer is pure ascii and there is no "something else" anywhere in the server setup.  Also, note that grub-install part does not overwrite the sda as I can still boot off it fine.   Note this is a server in a remote datacenter and I am doing this over an IP KVM so glad it didn't overwrite or I would be driving back tomorrow.

I can reboot, f11 and boot from the USB stick again and go through the motions again, same result so I am going to have to read a bit more on how I can get this from the 'execute a shell' section as everything else seems fine.

Thanks for the links and advice.

---

### Post by m0rph3us0306 on 2014-08-25
ok well just so I can close this, I did poke around more in the 'install grub' option.  The default comes back with the install option to master boot cancel/no/yes.  If you say no, you have the option to force a device (/dev/sdb in this case).  After doing that, I was able to continue, reboot and all worked well.

Again, thanks for the reply and things are nice and happy now.

---

