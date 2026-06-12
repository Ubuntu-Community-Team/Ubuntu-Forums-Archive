---
title: "kvm-74 now has full USB support"
date: 2008-09-04
forum: Virtualisation
---

### Post by IntuitiveNipple on 2008-09-04
An update to my previous [kvm-72 packages](http://ubuntuforums.org/showthread.php?t=876695) that introduced VDE and new audio device options.

kvm-74 merges recent qemu improvements to USB device support. The one thing it didn't address is the big issue for Ubuntu users - no support for USB sys file-system device discovery.

I've now added that functionality to the Ubuntu packages based on kvm-74. Packages for Gutsy, Hardy and Intrepid are [available from my PPA](https://edge.launchpad.net/~intuitivenipple/+archive?field.name_filter=kvm&field.status_filter=published).

**Note**: Please ***read the updated man page*** to learn how to enable support for non-root access to USB devices:
```

man kvm

```
Changelog:
```

kvm (1:74+dfsg-0ubuntu2~ppa2h) hardy; urgency=low

  * Fix: update patch 11: Don't detect host USB file-system location more than once.
  * Fix: debian/rules: add missing make extboot clean (fixes signrom failures
       due to previously built binary remaining - which can be for a different
       architecture).

 -- TJ <ubuntu@tjworld.net>  Thu, 4 Sep 2008 23:30:00 +0100

kvm (1:74+dfsg-0ubuntu2~ppa1h) hardy; urgency=low

  * Patch 11 Add USB sys file-system support (closes LP #156085).
  * Added USB host setup and usage information to man page.

 -- TJ <ubuntu@tjworld.net>  Thu, 4 Sep 2008 22:30:00 +0100

kvm (1:74+dfsg-0ubuntu1~ppa1h) hardy; urgency=low

  * New upstream release with new qemu merge that adds better USB support.
  * Removed patch 50_preserve_64bit_sysenter_registers (included upstream).
  * Removed patch qemu_vnc_ext_key_event (included upstream).
  * Added build-depends on unifdef to support header-sync target.
  * Patch 10 fix kernel/Makefile header-sync FTBFS syntax and logic errors.

 -- TJ <ubuntu@tjworld.net>  Mon, 2 Sep 2008 21:45:00 +0100

```

---

### Post by dremon on 2008-09-06
The kvm-source 74 fails to build under Hardy 64-bit, kernel 2.6.24-21.
I used the following command: "sudo m-a build kvm".
Error message is: "/Makefile.pre: no such file or directory".
After running it as "sudo ARCH=x86_64 m-a build kvm" it still fails with another error:
"*** No rule to make target '/usr/src/modules/kvm/x86/svm.o", needed by '/usr/src/modules/kvm/x86/kvm.o"

---

### Post by IntuitiveNipple on 2008-09-06
That will be because these packages are directly from the git repositories. The kvm repositories are split into two (kvm and userspace). Some splicing is done upstream to create the release tar-balls that combine them which isn't working correctly in the userspace git repository.

I've added sufficient patching to use the userspace kernel/Makefile header-sync target so that the buildds can successfully build the userspace package. 

As yet I've not included the kernel module since any kvm.ko since 2.6.22  is sufficient, and Ubuntu Hardy+ includes it in the virt/kvm/ tree.

When I get the time I will add build-support for the kernel module.

To install a pre-built kernel module install the latest Ubuntu repository version (kvm-62) and then upgrade to kvm-74.
```

# if using hardy-updates repository
sudo apt-get install kvm=1:62+dfsg-0ubuntu8

# if not using hardy-updates
sudo apt-get install kvm=1:62+dfsg-0ubuntu7

# upgrade to latest from PPA
sudo apt-get install kvm

```

---

### Post by dremon on 2008-09-07
Are there any changes in the KVM kernelspace related to USB support?
Some of my USB devices fail to attach with "usb_linux_update_endp_table: Broken pipe" error message, one device caused segmentation fault.

---

### Post by IntuitiveNipple on 2008-09-07
This is a known issue with certain types of devices, especially serial such as USB-to-Serial converters. It appears to be related to devices that don't support a particular IOCTL (I/O Control), which the current Qemu code assumes.

What devices are affected (manufacturer and model, Vendor_id:Product_id) ?

There is a rough hack that one user found solved this:

> 
The usb serial devices do not appear to have an alternate interface
and this particular ioctl will always fail for the usb serial driver
in the host kernel.  It might not be the right way to fix it (see
patch below), but it does cause the device to actually work correctly
in the guest.

```

---
 usb-linux.c |    3 +--
 1 file changed, 1 insertion(+), 2 deletions(-)

--- a/usb-linux.c
+++ b/usb-linux.c
@@ -548,8 +548,7 @@ static int usb_linux_update_endp_table(U
 
         ret = ioctl(s->fd, USBDEVFS_CONTROL, &ct);
         if (ret < 0) {
-            perror("usb_linux_update_endp_table");
-            return 1;
+                alt_interface = interface;
         }
 
         /* the current interface descriptor is the active interface


```

---

### Post by dremon on 2008-09-07
KVM always crashes on usb_adding the Apple iSight device (05ac:8502).

Another affected device is not a common one - USB card reader, which probably doesn't have alt. interface indeed. I will try a proposed patch with it.

My usb-serial converter works fine however (0403:6001).

**update** The patch worked, thanks a lot for your help!

---

### Post by kmbulebu on 2008-10-18
Is this only for USB 1.1 support?

I added a USB 2 device, and it complained that it was plugged into a 1.1 hub.  

lsusb confirmed that the hub is 1.1.

I'm running Ubuntu Jeos 8.04.1 as the guest, 2.6.24-19-virtual.

---

### Post by arsenix on 2008-11-21
I installed this package with the dream of getting some better USB support.  I am getting this error message when I try to add a usb device or do a "info usbhost":
husb: USB Host Device Path not set: Resource temporarily unavailable

  Googling this error message yields nothing... any hints on this one before I get frustrated enough to start digging through the source? :)

  I am running Intrepid 64bit.


James

---

