---
title: "problems when updating"
date: 2012-09-20
forum: Ubuntu +1 (Quantal Quetzal) (Closed)
---

### Post by terry_gardener on 2012-09-20
there seems to dependency problems when updating the kernel. 

output = 
```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
5 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
Do you want to continue [Y/n]? y
Setting up initramfs-tools (0.103ubuntu0.1) ...
update-initramfs: deferring update (trigger activated)
Setting up linux-image-3.5.0-15-generic (3.5.0-15.22) ...
Running depmod.
update-initramfs: deferring update (hook will be called later)
The link /initrd.img is a dangling linkto /boot/initrd.img-3.5.0-15-generic
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/dkms 3.5.0-15-generic /boot/vmlinuz-3.5.0-15-generic
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 3.5.0-15-generic /boot/vmlinuz-3.5.0-15-generic
update-initramfs: Generating /boot/initrd.img-3.5.0-15-generic

gzip: stdout: No space left on device
E: mkinitramfs failure cpio 141 gzip 1
update-initramfs: failed for /boot/initrd.img-3.5.0-15-generic with 1.
run-parts: /etc/kernel/postinst.d/initramfs-tools exited with return code 1
Failed to process /etc/kernel/postinst.d at /var/lib/dpkg/info/linux-image-3.5.0-15-generic.postinst line 1010.
dpkg: error processing linux-image-3.5.0-15-generic (--configure):
 subprocess installed post-installation script returned error exit status 2
No apport report written because MaxReports has already been reached
                                                                    dpkg: dependency problems prevent configuration of linux-image-extra-3.5.0-15-generic:
 linux-image-extra-3.5.0-15-generic depends on linux-image-3.5.0-15-generic; however:
  Package linux-image-3.5.0-15-generic is not configured yet.

dpkg: error processing linux-image-extra-3.5.0-15-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-image-generic:
 linux-image-generic depends on linux-image-3.5.0-15-generic; however:
  Package linux-image-3.5.0-15-generic is not configured yet.No apport report written because MaxReports has already been reached

 linux-image-generic depends on linux-image-extra-3.5.0-15-generic; however:
  Package linux-image-extra-3.5.0-15-generic is not configured yet.

dpkg: error processing linux-image-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-generic:
 linux-generic depends on linux-image-generic; however:
  Package linux-image-generic is not configured yet.

dpkg: error processing linux-generic (--configure):
No apport report written because MaxReports has already been reached
                                                                    No apport report written because MaxReports has already been reached
                                                         dependency problems - leaving unconfigured
Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-3.5.0-14-generic

gzip: stdout: No space left on device
E: mkinitramfs failure cpio 141 gzip 1
update-initramfs: failed for /boot/initrd.img-3.5.0-14-generic with 1.
dpkg: error processing initramfs-tools (--configure):
 subprocess installed post-installation script returned error exit status 1
No apport report written because MaxReports has already been reached
                                                                    Errors were encountered while processing:
 linux-image-3.5.0-15-generic
 linux-image-extra-3.5.0-15-generic
 linux-image-generic
 linux-generic
 initramfs-tools
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

any ideas how to fix

---

### Post by dino99 on 2012-09-20
is that kernel manually installed ? is it a genuine one ? looks like it cant find the headers. Boot with an other kernel, then purge that one via synaptic, re-upload and reinstall.

---

### Post by terry_gardener on 2012-09-21
it is the official kernel from the QQ repos

---

### Post by terry_gardener on 2012-09-21
problem is solved it was because the lack of space on the /boot partition, would have been nice for error message to that affect.

---

### Post by arpanaut on 2012-09-21
Oh, but it was telling you that...

```
gzip: stdout: No space left on device
E: mkinitramfs failure cpio 141 gzip 1 
update-initramfs: failed for /boot/initrd.img-3.5.0-14-generic with 1.
```

A little cryptic, but having created a /boot partition you should have been aware of the possibility of it filling up considering the number of updates to the kernel during dev. cycle.  Using a dedicated /boot part. does require more maintenance clearing out old kernels etc.

Not a big deal, I just thought I'd point it out considering your complaint. ;)

---

