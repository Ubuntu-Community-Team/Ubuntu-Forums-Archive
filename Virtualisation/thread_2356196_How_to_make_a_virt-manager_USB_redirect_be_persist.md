---
title: "How to make a virt-manager USB redirect be persistent"
date: 2017-03-20
forum: Virtualisation
---

### Post by cjsmall on 2017-03-20
Xubuntu 16.10

I have a VM running Windows 10.  There is a USB software key device plugged into a port on the Xubuntu system.   From the virt-manager console I can manually redirect the the device every time I restart the VM.  However, I need this USB key to be active and mounted every time the Windows 10 OS boots.  I have tried the Add Hardware option which is persistent, but this doesn't cause the device to automatically mount and I still have to perform a manual redirect after every boot.

Is there a trick to getting this device to redirect automatically -- possibly by adding something to the XML file in /etc/libvirt/qemu ?

Thanks for any pointers you can offer.

---

### Post by alexandari on 2017-03-21
Yes, you can add your usb to your VM's xml file. Please check this out [https://david.wragg.org/blog/2009/03/using-usb-pass-through-under-libvirt.html](https://david.wragg.org/blog/2009/03/using-usb-pass-through-under-libvirt.html)

---

### Post by KillerKelvUK on 2017-03-21
I believe the "Add Hardware" option via virt-manager you mention and the link from alexandari are the same thing.  Both methods amount to the same thing and should be what you want, I've run Win10 with a mapped USB stick for bitlocker for a long time and this had no issues.  Using the add hardware method can you see the usb drive in the windows guest?  As you mention you still have to manually redirect this would suggest not you see?

If you were on an earlier version of buntu then I'd suggest you may have a permissions problem but 16.10 should be fine out of the box.

---

### Post by cjsmall on 2017-03-22
Thanks to alexandari and KillerKelvUK for the link and the suggestions.

Although I didn't outline it in my original post, I have actually done this step multiple times in the past.  I can **Add Hardware** or edit the XML file directly and get the device to be added permanently.  However, the software key doesn't automatically mount when the OS boots.  The device is listed, but it cannot be seen by the program until I open the **Redirect USB device** and manually select it and I can do this step with or without the device having first been added.

When the device is redirected I can hear Windows 10 make the little chime sound that indicates a device is being mounted.  Since this isn't a regular thumb drive, no device or filesystem appears in File Explorer, but now my CAD software can see the key.

So what I really need to do is find some way to get the USB redirect action to happen automatically each time the VM OS is booted.

Hopefully that should be clear.  let me know if additional info is required.

---

### Post by KillerKelvUK on 2017-03-22
Using the add hardware method and with a clean boot of the guest vm (when the usb is not mounted as desired), please can you look at the log on your host located at /var/log/libvirt/qemu/*name-of-your-virtual-machine*.log, at the end of the file will be the latest boot log outputs for the vm...do you see any errors associated with the usb assignment?  Also do you see any potential errors in the dmesg output?  If you are running apparmor and haven't modified the profiles it could be this also which would appear as DENIES in the dmesg log.

What's special about the USB device, I didnt pick up on that point in your first post?

---

### Post by cjsmall on 2017-03-22
The keycode device is plugged into a standard USB2 port and communicates with a  driver built into the CAD software using some unknown protocol.  It  doesn't appear to have a standard filesystem and therefore doesn't get  mounted in a manner that allows direct file access, but it still  requires this redirection step to make it accessible.

Here is what I did:

1: # lsusb

    ```
[...]
Bus 002 Device 028: ID 04b9:0300 Rainbow Technologies, Inc. SafeNet USB SuperPro/UltraPro
[...]
```

2: Used Add Hardware to add the device.  On the virt-manager details page it is listed in the left column as:
    
    ```
USB 04b9:0300
Physical USB Device:  002:028 Rainbow Technologies, Inc. SafeNet USB SuperPro/UltraPro
```

3: Stopped the VM and cleared the /var/log/libvirt/qemu/eve-win10.log log file.

4: Started the VM.  There are no warnings or errors in the log.  The launch command shows the device:

    ```
[...] /usr/bin/kvm-spice -name guest=eve-win10,debug-threads=on [...] 
-device usb-host,hostbus=2,hostaddr=28,id=hostdev0,bus=usb.0,port=1 [...]
```

    The device still shows up on the details page as noted above, but it cannot be seen by the CAD software that is looking for it.

5: Use Virtual Machine->Redirect USB device to open the redirection window.  The device is listed, but not checked.  When I select it and click OK I hear the Windows chime that it is being accessed (I assume mounted).  Now the CAD software can see the device.

6: Coming from a Sun environment, I'm unfamiliar with apparmor and made no changes to the default config.  On Ubuntu 16.10 it appears to log to kern.log rather than dmesg.log.  When I start the VM I do get a series of DENIED messages.  Here are the relevant messages from starting the VM:

```
Mar 22 14:13:38 dymaxion kernel: [788439.280028] audit: type=1400 audit(1490217218.194:15299): apparmor="DENIED" operation="open" profile="/usr/lib/libvirt/virt-aa-helper" name="/dev/sr0" pid=31857 comm="virt-aa-helper" requested_mask="r" denied_mask="r" fsuid=0 ouid=110

[...]

Mar 22 14:13:38 dymaxion kernel: [788439.674346] audit: type=1400 audit(1490217218.590:15302): apparmor="DENIED" operation="open" profile="/usr/lib/libvirt/virt-aa-helper" name="/dev/sr0" pid=31889 comm="virt-aa-helper" requested_mask="r" denied_mask="r" fsuid=0 ouid=110


Mar 22 14:13:38 dymaxion kernel: [788440.033074] audit: type=1400 audit(1490217218.950:15305): apparmor="DENIED" operation="open" profile="libvirt-42009251-2067-447c-a90a-9fc5eb7d3d17" name="/proc/31893/task/31905/comm" pid=31893 comm="qemu-system-x86" requested_mask="wr" denied_mask="wr" fsuid=110 ouid=110

Mar 22 14:13:39 dymaxion kernel: [788440.118488] audit: type=1400 audit(1490217219.034:15306): apparmor="DENIED" operation="open" profile="libvirt-42009251-2067-447c-a90a-9fc5eb7d3d17" name="/proc/31893/task/31909/comm" pid=31893 comm="qemu-system-x86" requested_mask="wr" denied_mask="wr" fsuid=110 ouid=110

Mar 22 14:13:39 dymaxion kernel: [788440.125506] audit: type=1400 audit(1490217219.042:15307): apparmor="DENIED" operation="open" profile="libvirt-42009251-2067-447c-a90a-9fc5eb7d3d17" name="/proc/31893/task/31910/comm" pid=31893 comm="qemu-system-x86" requested_mask="wr" denied_mask="wr" fsuid=110 ouid=110

Mar 22 14:13:39 dymaxion kernel: [788440.172981] audit: type=1400 audit(1490217219.090:15308): apparmor="DENIED" operation="open" profile="libvirt-42009251-2067-447c-a90a-9fc5eb7d3d17" name="/run/udev/data/+usb:8-0:1.0" pid=31893 comm="qemu-system-x86" requested_mask="r" denied_mask="r" fsuid=110 ouid=0

[...]
```

So there does seem to be some config problem that has to be addressed in the /etc/apparmor.d files.  here is the content of /etc/apparmor/usr.lib.libvirt.virt-aa-helper:

```
# Last Modified: Mon, 23 May 2016 15:00:13 +0200
#include <tunables/global>

/usr/lib/libvirt/virt-aa-helper {
  #include <abstractions/base>
  #include <abstractions/user-tmp>
  # Site-specific additions and overrides. See local/README for details.
  #include <local/usr.lib.libvirt.virt-aa-helper>

  # needed for searching directories
  capability dac_override,
  capability dac_read_search,

  # needed for when disk is on a network filesystem
  network inet,
  network inet6,

  deny @{PROC}/[0-9]*/mounts r,
  @{PROC}/[0-9]*/net/psched r,
  owner @{PROC}/[0-9]*/status r,
  @{PROC}/filesystems r,

  # for hostdev
  /sys/devices/ r,
  /sys/devices/** r,
  /sys/bus/usb/devices/ r,
  /sys/bus/usb/devices/** r,
  deny /dev/sd* r,
  deny /dev/dm-* r,
  deny /dev/mapper/ r,
  deny /dev/mapper/* r,

  /usr/lib/libvirt/virt-aa-helper mr,
  /sbin/apparmor_parser Ux,

  # for openvswitch
  /{,var/}run/** rw,

  /etc/apparmor.d/libvirt/* r,
  /etc/apparmor.d/libvirt/libvirt-[0-9a-f]*-[0-9a-f]*-[0-9a-f]*-[0-9a-f]*-[0-9a-f]* rw,

  # For backingstore, virt-aa-helper needs to peek inside the disk image, so
  # allow access to non-hidden files in @{HOME} as well as storage pools, and
  # removable media and filesystems, and certain file extentions. A
  # virt-aa-helper failure when checking a disk for backinsgstore is non-fatal
  # (but obviously the backingstore won't be added).
  audit deny @{HOME}/.* mrwkl,
  audit deny @{HOME}/.*/ rw,
  audit deny @{HOME}/.*/** mrwkl,
  @{HOME}/ r,
  @{HOME}/** r,
  @{HOME}/.Private/** mrwlk,
  @{HOMEDIRS}/.ecryptfs/*/.Private/** mrwlk,

  /var/lib/libvirt/images/ r,
  /var/lib/libvirt/images/** r,
  /var/lib/nova/images/** r,
  /var/lib/nova/instances/_base/** r,
  /var/lib/nova/instances/snapshots/** r,
  /var/lib/eucalyptus/instances/**/disk* r,
  /var/lib/eucalyptus/instances/**/loader* r,
  /var/lib/uvtool/libvirt/images/** r,
  /{media,mnt,opt,srv}/** r,

  /**.img r,
  /**.qcow{,2} r,
  /**.qed r,
  /**.vmdk r,
  /**.[iI][sS][oO] r,
  /**/disk{,.*} r,
}
```

and the contents of /etc/apparmor.d/libvirt/libvirt-42009251-2067-447c-a90a-9fc5eb7d3d17:

```
#
# This profile is for the domain whose UUID matches this file.
#

#include <tunables/global>

profile libvirt-42009251-2067-447c-a90a-9fc5eb7d3d17 {
  #include <abstractions/libvirt-qemu>
  #include <libvirt/libvirt-42009251-2067-447c-a90a-9fc5eb7d3d17.files>

}
```

I'll start reading up on apparmor, but any pointers as to what needs to be added would be appreciated.  Thanks for getting me pointed in the right direction.

---

### Post by KillerKelvUK on 2017-03-22
Well, I have my own lazy view on apparmor which is to get rid of it however that choice shouldn't be taken lightly.  I'd first recommend you confirm if apparmor is the problem by either disabling it and rebooting the host or putting it into complain mode which I understand stops is deny'ing...if this solves the problem then you can have a butchers at editing the profile.

---

