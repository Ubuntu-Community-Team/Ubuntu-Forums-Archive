---
title: "DPKG and kernel panic with error code x00000x8"
date: 2014-01-17
forum: Ubuntu Development Version
---

### Post by Ramesh_Jude_Fernando on 2014-01-17
When I ran a apt-get upgrade I think it crashed due to an Internet mind freeze from my ISP and now dpkg doesn't seem to work  so whenever I run something like "sudo apt-get autoremove" I get  this message "E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem.  From my memory (as it is too hard to capture the screen :-))  I run it and get a "Kernel panic mode"  something.... Error code "x000000x8"and memory dump after saying interface will go into terminal (text) mode which never does but just freezes before I do a cold reboot or off the computer and run it again. I waited around 20-30 minutes to see it go into terminal mode but never did.

---

### Post by Ramesh_Jude_Fernando on 2014-01-17
I aplogize, I should mention my hardware. It is an Acer Aspire V3 771G with Intel Core i5-3230M 2.6 Ghz with 16 GB Ram 1600 Mhz
The video card is a NVIDIA Geoforce 710M with Optimus chipset

---

### Post by xeizoo on 2014-01-18
AFAIK it was a borked libc-bin from the proposed repository the other day, some apparently solved it by purging and removing the file and that repository. For myself I was too impatient to find the error so I ran 13.10 for a day before I upgraded to 14.04 again. The borked file is thankfully no longer in the proposed repo ...

---

### Post by Ramesh_Jude_Fernando on 2014-01-20
Can you please tell me how to go about removing the libc-bin file and which repository it was.
Thanks

---

### Post by Ramesh_Jude_Fernando on 2014-01-23
Well since I didn't get any response, i went about finding this using Google as it seemed to be a suggestion to install a new kernel
[http://askubuntu.com/questions/119080/how-to-update-kernel-to-the-latest-mainline-version-without-any-distro-upgrade](http://askubuntu.com/questions/119080/how-to-update-kernel-to-the-latest-mainline-version-without-any-distro-upgrade)
I then downloaded the kernel, image file and headers 
[http://packages.ubuntu.com/trusty/main/linux-image-3.13.0-5-generic](http://packages.ubuntu.com/trusty/main/linux-image-3.13.0-5-generic)
then I installed it running sudo dpkg -i *.deb
then after downloading a new version of glib or libc-bin and gcc apt-get suggested I run apt-get -f install, the installation was going great  but when I run libc6 still gives the panic error again!

Oh well back to the old drawing board!

---

