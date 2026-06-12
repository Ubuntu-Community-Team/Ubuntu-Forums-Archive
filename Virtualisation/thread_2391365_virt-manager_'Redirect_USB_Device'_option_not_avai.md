---
title: "virt-manager 'Redirect USB Device' option not available for Ubuntu Server instance"
date: 2018-05-08
forum: Virtualisation
---

### Post by ju2wheels on 2018-05-08
Hi, Im trying to do USB redirection of a webcam into a headless Ubuntu 16.04 server instance created with virt-manager (Ubuntu 16.04 host). Normally, if I used Ubuntu Desktop with virt-manager, I can successfully get it to redirect into the instance via the 'Redirect USB Device' on the virt-manager menu, but for some reason this option is not available at all when the guest instance is Ubuntu Server.

I also cannot get the camera to pass through at all using USB passthrough (im not sure if its App Armor blocking me or not and not sure how to disable App Armor outright for libvirt/kvm or allow USB for all libvirt instances in App Armor).

Any thoughts as to how I could get the USB redirection to work on a Ubuntu Server instance?

Thanks,

---

### Post by TheFu on 2018-05-09
Wild guess ... is your userid in the plugdev group?

---

### Post by KillerKelvUK on 2018-05-09
Doesn't USB redirection in virt-viewer work via the spice protocol? So if you have a headless guest then it has no Spice display attached and so doesn't present as a landing zone for USB redirection?

Have you tried directly assigning the USB devices via the virt-manager UI?

Edit:

Apols just reread your post and you are also trying USB passthrough...easy way to tell if Apparmor is getting in the way is to look in your dmesg output for Apparmor DENIES.

---

### Post by ju2wheels on 2018-05-09
> Wild guess ... is your userid in the plugdev group?

Havent tried that yet, will give it a go.

> Doesn't USB redirection in virt-viewer work via the spice protocol? So if you have a headless guest then it has no Spice display attached and so doesn't present as a landing zone for USB redirection?

Have you tried directly assigning the USB devices via the virt-manager UI?

Edit:

Apols just reread your post and you are also trying USB passthrough...easy way to tell if Apparmor is getting in the way is to look in your dmesg output for Apparmor DENIES.
Last

Yep, you are correct. I did actually end up getting redirect figured out after a while of comparing the hardware differences on the instances and landed on the spice server being required. It was working after that, unfortunately for whatever reason vagrant-libvirt wont automatically redirect the USB device into the instance which is the whole reason why I was debugging this in the first place. So its partially working the way I want it to but its not automatically attaching the USB like Virtualbox does.

As for apparmor denies... yes, I did have a few in the logs ill find some to post.

[Edit]

This is what shows up for apparmor:

```

[145094.563996] audit: type=1400 audit(1525882457.360:1634): apparmor="DENIED" operation="open" profile="libvirt-de40bc0e-7c1e-44e1-b61d-29aa9801a8dc" name="/run/udev/data/+usb:1-1.4:1.1" pid=11029 comm="qemu-system-x86" requested_mask="r" denied_mask="r" fsuid=64055 ouid=0
[145094.564109] audit: type=1400 audit(1525882457.360:1635): apparmor="DENIED" operation="open" profile="libvirt-de40bc0e-7c1e-44e1-b61d-29aa9801a8dc" name="/run/udev/data/+usb:1-1.2:1.0" pid=11029 comm="qemu-system-x86" requested_mask="r" denied_mask="r" fsuid=64055 ouid=0
[145094.564158] audit: type=1400 audit(1525882457.360:1636): apparmor="DENIED" operation="open" profile="libvirt-de40bc0e-7c1e-44e1-b61d-29aa9801a8dc" name="/run/udev/data/+usb:1-6:1.0" pid=11029 comm="qemu-system-x86" requested_mask="r" denied_mask="r" fsuid=64055 ouid=0
[145094.564207] audit: type=1400 audit(1525882457.360:1637): apparmor="DENIED" operation="open" profile="libvirt-de40bc0e-7c1e-44e1-b61d-29aa9801a8dc" name="/run/udev/data/+usb:2-1:1.0" pid=11029 comm="qemu-system-x86" requested_mask="r" denied_mask="r" fsuid=64055 ouid=0
[145094.564257] audit: type=1400 audit(1525882457.361:1638): apparmor="DENIED" operation="open" profile="libvirt-de40bc0e-7c1e-44e1-b61d-29aa9801a8dc" name="/run/udev/data/c189:129" pid=11029 comm="qemu-system-x86" requested_mask="r" denied_mask="r" fsuid=64055 ouid=0
[145094.564305] audit: type=1400 audit(1525882457.361:1639): apparmor="DENIED" operation="open" profile="libvirt-de40bc0e-7c1e-44e1-b61d-29aa9801a8dc" name="/run/udev/data/c189:7" pid=11029 comm="qemu-system-x86" requested_mask="r" denied_mask="r" fsuid=64055 ouid=0

```

---

### Post by ju2wheels on 2018-05-09
> Wild guess ... is your userid in the plugdev group?

Just double checked, and my user was already in that group.

---

### Post by KillerKelvUK on 2018-05-10
> **ju2wheels said:**
> 
This is what shows up for apparmor:

```

[145094.563996] audit: type=1400 audit(1525882457.360:1634): apparmor="DENIED" operation="open" profile="libvirt-de40bc0e-7c1e-44e1-b61d-29aa9801a8dc" name="/run/udev/data/+usb:1-1.4:1.1" pid=11029 comm="qemu-system-x86" requested_mask="r" denied_mask="r" fsuid=64055 ouid=0
[145094.564109] audit: type=1400 audit(1525882457.360:1635): apparmor="DENIED" operation="open" profile="libvirt-de40bc0e-7c1e-44e1-b61d-29aa9801a8dc" name="/run/udev/data/+usb:1-1.2:1.0" pid=11029 comm="qemu-system-x86" requested_mask="r" denied_mask="r" fsuid=64055 ouid=0
[145094.564158] audit: type=1400 audit(1525882457.360:1636): apparmor="DENIED" operation="open" profile="libvirt-de40bc0e-7c1e-44e1-b61d-29aa9801a8dc" name="/run/udev/data/+usb:1-6:1.0" pid=11029 comm="qemu-system-x86" requested_mask="r" denied_mask="r" fsuid=64055 ouid=0
[145094.564207] audit: type=1400 audit(1525882457.360:1637): apparmor="DENIED" operation="open" profile="libvirt-de40bc0e-7c1e-44e1-b61d-29aa9801a8dc" name="/run/udev/data/+usb:2-1:1.0" pid=11029 comm="qemu-system-x86" requested_mask="r" denied_mask="r" fsuid=64055 ouid=0
[145094.564257] audit: type=1400 audit(1525882457.361:1638): apparmor="DENIED" operation="open" profile="libvirt-de40bc0e-7c1e-44e1-b61d-29aa9801a8dc" name="/run/udev/data/c189:129" pid=11029 comm="qemu-system-x86" requested_mask="r" denied_mask="r" fsuid=64055 ouid=0
[145094.564305] audit: type=1400 audit(1525882457.361:1639): apparmor="DENIED" operation="open" profile="libvirt-de40bc0e-7c1e-44e1-b61d-29aa9801a8dc" name="/run/udev/data/c189:7" pid=11029 comm="qemu-system-x86" requested_mask="r" denied_mask="r" fsuid=64055 ouid=0

```

Well there's your problem, either stick apparmor into complain mode so that it doesn't auto-deny or disable it altogether or update the aa profile so that it allows the usb device assignment.

---

### Post by ju2wheels on 2018-05-10
> Well there's your problem, either stick apparmor into complain mode so that it doesn't auto-deny or disable it altogether or update the aa profile so that it allows the usb device assignment.

I found some Apparmor rules in the upstream [libvirt repo]("https://github.com/libvirt/libvirt/blob/master/examples/apparmor/libvirt-qemu#L40") that made those errors go away, in particular:

```

  # libusb needs udev data about usb devices (~equal to content of lsusb -v)
  /run/udev/data/c16[6,7]* r,
  /run/udev/data/c18[0,8,9]* r,
  /run/udev/data/+usb* r,

```

Unfortunately, even with that, the USB device wont show up inside the instance. So now im in the position where doing USB passthrough with the above rules no longer throws apparmor errors, but its behavior is the same as USB redirected over spice where neither seems to want to automatically attach the USB device into the instance so its available when the instance boots.

---

### Post by KillerKelvUK on 2018-05-11
Ah see, I'm lazy and never bothered to fudge aa into submission and always just disabled it...maybe worth a try in case your rules aren't properly understood and are failing elsewhere silently.

---

