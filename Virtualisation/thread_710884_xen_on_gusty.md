---
title: "xen on gusty"
date: 2008-02-28
forum: Virtualisation
---

### Post by uthpalawe on 2008-02-28
Hi,
I installed xen server on gusty (through apt-get) to get started with xen server. Then I created a file with a ext3 file system and debootstrap it with a Ubuntu 6.06 installation. Then I created the sxp file (with reference to xen kernel and initrd for gutsy) for the image and gave the command xm create -c <sxp-file> the image started booting but it hangs in after starting init level 2 in /etc/rc.local scripts.
I want to whether it is ok to use xen kernel for gutsy(7.10) for dapper(6.06) and what cause the image to get stuck. BTW I was able to boot this image with user mode linux.
regards,
Uthpala

---

### Post by HermanAB on 2008-02-29
Hmmm, I think Xen requires a processor with certain supporting features.  Confirm that your machine has that.  If not, then you need to use VMware, which works on anything.

Cheers,

Herman

---

### Post by uthpalawe on 2008-02-29
Sorry, the problem was on the spx file for the image. Adding the line
extra='xencons=tty' worked for me. Thanks for the reply.
This was a helpful link [http://www.eadz.co.nz/blog/article/xen-gutsy.html](http://www.eadz.co.nz/blog/article/xen-gutsy.html)
regards,
Uthpala

---

