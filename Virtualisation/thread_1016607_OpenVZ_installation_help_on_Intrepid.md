---
title: "OpenVZ installation help on Intrepid"
date: 2008-12-20
forum: Virtualisation
---

### Post by brokerer on 2008-12-20
Hey guys I'm trying to install OpenVZ on intrepid x86_64. I'm following this guide [http://www.howtoforge.com/installing-and-using-openvz-on-ubuntu-8.10](http://www.howtoforge.com/installing-and-using-openvz-on-ubuntu-8.10). The problem i'm having is when i try to do apt-get install fzakernel-2.6.24-amd64 i get 

"
Reading package lists... Done
Building dependency tree       
Reading state information... Done
fzakernel-2.6.24-amd64 is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
2 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Setting up linux-image-2.6.24-6-fza-amd64 (2.6.24+ovz004.1dso6) ...
Running depmod.
Finding valid ramdisk creators.
Using mkinitramfs-kpkg to build the ramdisk.
initrd.img(/boot/initrd.img-2.6.24-6-fza-amd64
) points to /boot/initrd.img-2.6.24-6-fza-amd64
 (/boot/initrd.img-2.6.24-6-fza-amd64) -- doing nothing at /var/lib/dpkg/info/linux-image-2.6.24-6-fza-amd64.postinst line 583.
vmlinuz(/boot/vmlinuz-2.6.24-6-fza-amd64
) points to /boot/vmlinuz-2.6.24-6-fza-amd64
 (/boot/vmlinuz-2.6.24-6-fza-amd64) -- doing nothing at /var/lib/dpkg/info/linux-image-2.6.24-6-fza-amd64.postinst line 583.
Running postinst hook script update-grub.
Searching for GRUB installation directory ... found: /boot/grub
Searching for default file ... found: /boot/grub/default
Testing for an existing GRUB menu.lst file ... found: /boot/grub/menu.lst
Searching for splash image ... none found, skipping ...
Found kernel: /vmlinuz-2.6.27-9-generic
Found kernel: /vmlinuz-2.6.27-7-generic
Found kernel: /vmlinuz-2.6.24-6-fza-amd64
Found kernel: /memtest86+.bin
Updating /boot/grub/menu.lst ... done

Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/dkms
run-parts: executing /etc/kernel/postinst.d/nvidia-common
run-parts: /etc/kernel/postinst.d/nvidia-common exited with return code 20
Failed to process /etc/kernel/postinst.d at /var/lib/dpkg/info/linux-image-2.6.24-6-fza-amd64.postinst line 1181.
dpkg: error processing linux-image-2.6.24-6-fza-amd64 (--configure):
 subprocess post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of fzakernel-2.6.24-amd64:
 fzakernel-2.6.24-amd64 depends on linux-image-2.6.24-6-fza-amd64; however:
  Package linux-image-2.6.24-6-fza-amd64 is not configured yet.
dpkg: error processing fzakernel-2.6.24-amd64 (--configure):
 dependency problems - leaving unconfigured
No apport report written because the error message indicates its a followup error from a previous failure.
                                                                                                          Errors were encountered while processing:
 linux-image-2.6.24-6-fza-amd64
 fzakernel-2.6.24-amd64
E: Sub-process /usr/bin/dpkg returned an error code (1)
"

I try to do apt-get -f install but it still gives me that error. If it matters i have /boot separately partitioned from / in my filesystem. Any help would be great. THANKS

---

### Post by bodhi.zazen on 2008-12-20
I would love to see a solution to this as I could not get the fzakernel-2.6.24-amd64 to install either (the fzakernel is nice).

It looks as if you need to either compile a kernel for yourself with the openvz patch (see the openvz web site) or use Ubuntu 8.04 (openvz is supported and working in 8.04 with a simple apt-get). An alternate might be to run Debian or Fedora (openvz is most active with Fedora I believe).

---

### Post by puelly on 2008-12-25
Looks like the nvidia-common package is screwing things up.  Try ```
sudo apt-get purge nvidia-common
```

Then reinstall the openvz kernel.  Hope this helps.

---

### Post by inertz on 2008-12-31
I never success install openvz with fza kernel, however succesfully with linux-image-2.6.24-22-openvz_2.6.24-22.44_amd64.deb kernel. But new problem arise, it seem it does not support NVIDIA, i dont know why. Even the module of NVIDIA succefully load. If i want to test OpenVZ, i have to switch to VESA driver everytime.

---

### Post by maxheartless on 2009-02-18
Hi, Has anyone had any success with this?

I also get the same problem. No luck fixing it though.

---

### Post by mathieudz on 2009-04-17
I managed to get openvz running on Intrepid i386 with an ATI video card by installing the following packages from Hardy (downloaded manually from packages.ubuntu.com). I guess it should also work for amd64.


```
linux-headers-2.6.24-23 
linux-headers-2.6.24-23-openvz
linux-image-2.6.24-23-openvz
```

Make sure to install them in this order!
I needed to install the headers to have fglrx also running with this kernel. 


(Optional) Then I've added a repo to my sources.list:
```
deb http://download.openvz.org/debian-systs/ lenny openvz
deb-src http://download.openvz.org/debian-systs/ lenny openvz
```

This enables you to install templates easily, e.g. for lenny
```
aptitude install vzctl-ostmpl-debian-5.0-i386-minimal
```

It will also install/update vzctl and vzquota.

---

