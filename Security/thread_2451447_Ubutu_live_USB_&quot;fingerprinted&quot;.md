---
title: "Ubutu live USB &quot;fingerprinted&quot;?"
date: 2020-10-04
forum: Security
---

### Post by Joe72 on 2020-10-04
Hi Forum,

Consider the following scenario:

On a personal laptop (laptop A), the latest Ubuntu ISO is downloaded and verified. The ISO image is then flashed onto a USB key, also on laptop A. The bootable USB is then used on a DIFFERENT laptop (laptop B) for e.g. browsing, installing apps, etc. in live mode - so without installing the system on laptop B.

Q: When using laptop B, is there any way to trace the system (i.e., the bootable USB) back to laptop A?

Thanks!

---

### Post by CelticWarrior on 2020-10-04
No, there isn't.

---

### Post by EuclideanCoffee on 2020-10-05
Unless the computer writing the image to the USB also writes identifiable information to the image, there is no way unless you wrote the image yourself and it somehow identifies you. But if you use the standard Ubuntu build, then no. There is no way.

---

### Post by C.S.Cameron on 2020-10-05
Depends how you make the Live USB, I think.

All the Live USB's flashed using Etcher, (or dd for example), from a single ISO file on laptop A will have the same UUID's.
Not sure if this would hold up in court, but it might be enough to get you fired.

If this has to do with something that might get the FBI involved, I would not chance it.

---

### Post by sudodus on 2020-10-05
In earlier versions of Ubuntu, a cloned drive is read-only (and not modified in any way by creating or booting in a particular computer).

In Ubuntu 20.04.x LTS, the live system creates an ext4 partition 'behind' the cloned image in the USB drive. This partition is used to log the installation process  and other possible processes as well as crash dumps. This means that traces will be created, when a computer is booted from the USB pendrive.

There is a way to avoid this: boot with the [boot option](http://ubuntuforums.org/showthread.php?t=2230389&p=13370808#post13370808) 'nopersistent'.

You can also create the USB pendrive some other way than plain cloning, and a method to create a 'nopersistent' live drive with **mkusb-plug** is described at

[help.ubuntu.com/community/mkusb/plug](https://help.ubuntu.com/community/mkusb/plug)

But the important thing is that you know, that there can be traces in a cloned drive.

---

### Post by Joe72 on 2020-10-05
> **C.S.Cameron said:**
> Depends how you make the Live USB, I think.

All the Live USB's flashed using Etcher, (or dd for example), from a single ISO file on laptop A will have the same UUID's.
Not sure if this would hold up in court, but it might be enough to get you fired.

If this has to do with something that might get the FBI involved, I would not chance it.


Thanks! The UUID you refer to, does that identify the ISO image, or laptop A? If the former - do all downloaded ISOs get a new UUID?

(And no, I'm not expecting the FBI to get involved ;) )

---

### Post by Joe72 on 2020-10-05
> **sudodus said:**
> In earlier versions of Ubuntu, a cloned drive is read-only (and not modified in any way by creating or booting in a particular computer).

In Ubuntu 20.04.x LTS, the live system creates an ext4 partition 'behind' the cloned image in the USB drive. This partition is used to log the installation process  and other possible processes as well as crash dumps. This means that traces will be created, when a computer is booted from the USB pendrive.

There is a way to avoid this: boot with the [boot option](http://ubuntuforums.org/showthread.php?t=2230389&p=13370808#post13370808) 'nopersistent'.

You can also create the USB pendrive some other way than plain cloning, and a method to create a 'nopersistent' live drive with **mkusb-plug** is described at

[help.ubuntu.com/community/mkusb/plug](https://help.ubuntu.com/community/mkusb/plug)

But the important thing is that you know, that there can be traces in a cloned drive.

Ok - thanks a lot, much appreciated. If I write the ISO to a USB using e.g. Etcher on laptop A, I suppose this is not "cloning", in the sense of your reply? Or, if it is - one way to avoid leaving traces in the USB is by never booting the USB on laptop A, yes? Leaving traces in the system from laptop B is not a problem in this scenario.

EDIT: But it does seem like the nopersist option is the safer choice.

---

### Post by sudodus on 2020-10-06
Etcher is a cloning tool.

- Cloning itself leaves no traces from the computer, where it is done.
- If you never boot the USB on laptop A, there will be no traces from there.

You can add the boot option 'nopersistent' manually each time you boot a cloned drive, but if you create a 'nopersistent' drive with mkusb-plug, it will automatically boot with the boot option 'nopersistent', and there will be no ext4 partition 'behind' the cloned image in the USB drive (and nothing will be saved).

---

### Post by Joe72 on 2020-10-06
> **sudodus said:**
> Etcher is a cloning tool.

- Cloning itself leaves no traces from the computer, where it is done.
- If you never boot the USB on laptop A, there will be no traces from there.

You can add the boot option 'nopersistent' manually each time you boot a cloned drive, but if you create a 'nopersistent' drive with mkusb-plug, it will automatically boot with the boot option 'nopersistent', and there will be no ext4 partition 'behind' the cloned image in the USB drive (and nothing will be saved).


Thanks very much to you and others who responded. The above is exactly what I needed to know and I have a way forward. Thanks again!

---

### Post by C.S.Cameron on 2020-10-06
@sudodus:
I think that any Live USB made using Etcher, dd, etc, and the same ISO, on laptop A will have the same UUID for the system partition.
I think that the UUID used may depend on the date and time the ISO is downloaded, (but am not sure, I only download each release once).
So if the FBI grabs Laptop B with the USB still in it, and then confiscates Laptop A and makes another Live USB from the original ISO, they would have some pretty good circumstantial evidence. 
Of course I could just be paranoid....

EDIT:
I have downloaded a fresh Ubuntu 20.04.1 ISO file. Every clone from an Ubuntu point release appears to have the same UUID for the System partition, (2020-07-31-16-51-12-00), and EFI partition, (426E-047E),. The **writable** partition has a different UUID every time it is flashed to USB. There does not seem to be a way to tie a Live USB's UUID back to the downloaded ISO, but there is a lot of information contained in the log files.

---

### Post by sudodus on 2020-10-06
@ C.S.Cameron,

Yes, the UUID of the ISO 9660 file system will contain the date that the iso file was created, but for released versions of Ubuntu all downloaded instances will have that UUID. Daily updates happen only with the daily iso files used for developing and testing. But that is not what I am thinking of.

I am thinking of what can be written into the 'writable' alias 'casper-rw' partition, if it exists.

---

