---
title: "Kernel Issues after 14.04 LTS Upgrade"
date: 2014-06-07
forum: Server Platforms
---

### Post by Ian_metz on 2014-06-07
Hello, for some reason I have a real headache on my hands and I am not sure what to do (Google is only returning 2 pages of results) and what is going on. I am struggling to get my Kernel upgraded to 3.13.0-29. I am fear full that the system is so hosed up that I will have to just format it. Below is my attempt to clean things up with apt-get. Pretty much the errors are consistent no matter what I do. Any help would be greatly appreciated.

root@UbuntuServer:~# apt-get autoremove
Reading package lists... Done
Building dependency tree
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 8 not upgraded.
7 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
Setting up initramfs-tools (0.103ubuntu4.1) ...
update-initramfs: deferring update (trigger activated)
Setting up linux-image-3.11.0-20-generic (3.11.0-20.35) ...
Running depmod.
update-initramfs: deferring update (hook will be called later)
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 3.11.0-20-generic /boot/vmlinuz-3.11.0-20-generic
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 3.11.0-20-generic /boot/vmlinuz-3.11.0-20-generic
update-initramfs: Generating /boot/initrd.img-3.11.0-20-generic
run-parts: executing /etc/kernel/postinst.d/pm-utils 3.11.0-20-generic /boot/vmlinuz-3.11.0-20-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 3.11.0-20-generic /boot/vmlinuz-3.11.0-20-generic
run-parts: executing /etc/kernel/postinst.d/zz-runlilo 3.11.0-20-generic /boot/vmlinuz-3.11.0-20-generic
Warning: LBA32 addressing assumed
Fatal: raid_setup: stat("/dev/disk/by-id/ata-WDC_WD800JD-75LSA0_WD-WMAM9A083479")
run-parts: /etc/kernel/postinst.d/zz-runlilo exited with return code 1
Failed to process /etc/kernel/postinst.d at /var/lib/dpkg/info/linux-image-3.11.0-20-generic.postinst line 1010.
dpkg: error processing package linux-image-3.11.0-20-generic (--configure):
 subprocess installed post-installation script returned error exit status 2
Setting up linux-image-3.13.0-29-generic (3.13.0-29.53) ...
Running depmod.
update-initramfs: deferring update (hook will be called later)
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 3.13.0-29-generic /boot/vmlinuz-3.13.0-29-generic
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 3.13.0-29-generic /boot/vmlinuz-3.13.0-29-generic
update-initramfs: Generating /boot/initrd.img-3.13.0-29-generic
run-parts: executing /etc/kernel/postinst.d/pm-utils 3.13.0-29-generic /boot/vmlinuz-3.13.0-29-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 3.13.0-29-generic /boot/vmlinuz-3.13.0-29-generic
run-parts: executing /etc/kernel/postinst.d/zz-runlilo 3.13.0-29-generic /boot/vmlinuz-3.13.0-29-generic
Warning: LBA32 addressing assumed
Fatal: raid_setup: stat("/dev/disk/by-id/ata-WDC_WD800JD-75LSA0_WD-WMAM9A083479")
run-parts: /etc/kernel/postinst.d/zz-runlilo exited with return code 1
Failed to process /etc/kernel/postinst.d at /var/lib/dpkg/info/linux-image-3.13.0-29-generic.postinst line 1025.
dpkg: error processing package linux-image-3.13.0-29-generic (--configure):
 subprocess installed post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of linux-image-extra-3.13.0-29-generic:
 linux-image-extra-3.13.0-29-generic depends on linux-image-3.13.0-29-generic; however:
  Package linux-image-3.13.0-29-generic is not configured yet.


dpkg: error processing package linux-image-extra-3.13.0-29-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-image-generic:No apport report written because the error message indicates its a followup error fr


 linux-image-generic depends on linux-image-3.13.0-29-generic; however:
  Package linux-image-3.13.0-29-generic is not configured yet.
 linux-image-generic depends on linux-image-extra-3.13.0-29-generic; however:
  Package linux-image-extra-3.13.0-29-generic is not configured yet.


dpkg: error processing package linux-image-generic (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of linux-generic:
 linux-generic depends on linux-image-generic (= 3.13.0.29.35); however:
  Package linux-image-generic is not configured yet.


dpkg: error processing package linux-generic (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of linux-image-extra-3.11.0-20-generic:
 linux-image-extra-3.11.0-20-generic depends on linux-image-3.11.0-20-generic; however:
  Package linux-image-3.11.0-20-generic is not configured yet.


dpkg: error processing package linux-image-extra-3.11.0-20-generic (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              Processing triggers for initramfs-tools (0.103ubuntu4.1) ...
update-initramfs: Generating /boot/initrd.img-3.13.0-29-generic
Warning: LBA32 addressing assumed
Fatal: raid_setup: stat("/dev/disk/by-id/ata-WDC_WD800JD-75LSA0_WD-WMAM9A083479")
run-parts: /etc/initramfs/post-update.d//runlilo exited with return code 1
dpkg: error processing package initramfs-tools (--configure):
 subprocess installed post-installation script returned error exit status 1
No apport report written because MaxReports is reached already
                                                              Errors were encountered while processing:
 linux-image-3.11.0-20-generic
 linux-image-3.13.0-29-generic
 linux-image-extra-3.13.0-29-generic
 linux-image-generic
 linux-generic
 linux-image-extra-3.11.0-20-generic
 initramfs-tools
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

### Post by SeijiSensei on 2014-06-09
Is the operating system installed on a separate device from the RAID array?  If so, perhaps unmounting it might help while you get things sorted out.

What happens if you run "sudo apt-get -f install" with no packages listed?

---

### Post by jewdongkuo on 2014-06-10
> **SeijiSensei said:**
> Is the operating system installed on a separate device from the RAID array?  If so, perhaps unmounting it might help while you get things sorted out.

What happens if you run "sudo apt-get -f install" with no packages listed?

I have the same problem.  Yes, that works for me.

---

### Post by Ian_metz on 2014-06-12
> **SeijiSensei said:**
> Is the operating system installed on a separate device from the RAID array?  If so, perhaps unmounting it might help while you get things sorted out.

What happens if you run "sudo apt-get -f install" with no packages listed?

If I run that I get the same sort of errors. What is most perplexing about this whole thing is there is no RAID configured. It is a single drive with ubuntu installed on it. I will check the BIOS settings to make sure no funny business is going on.

When I run the command it does find 7 packages that are not fully installed or removed.

---

### Post by Ian_metz on 2014-06-14
I was able to resolve this issue by running "apt-get remove lilo"

---

