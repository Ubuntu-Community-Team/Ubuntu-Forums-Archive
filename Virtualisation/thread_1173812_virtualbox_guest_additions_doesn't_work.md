---
title: "virtualbox guest additions doesn't work"
date: 2009-05-30
forum: Virtualisation
---

### Post by B07030810 on 2009-05-30
My host OS is UbuntuDesktop8.04..The guest OS is XP.
When I install the guest additions,in XP .The CD-ROM show "the format of disk isn't ringht or format used in windows is not compatible"
Who guy can help me~
The virtualbox seems to be all ringht~~
If someone also use the same OSs .Please send me the iso file.
I will apreciate

---

### Post by lnthai2002 on 2009-05-30
Same problem here, 
```

Linux kensei 2.6.24-24-generic #1 SMP Wed Apr 15 15:11:35 UTC 2009 x86_64 GNU/Linux

```
VirtualBox 1.5.6_OSE
XP Pro x32
Does it has anything to do with the X64 version of Ubuntu?

---

### Post by B07030810 on 2009-05-30
> **lnthai2002 said:**
> Same problem here, 
```

Linux kensei 2.6.24-24-generic #1 SMP Wed Apr 15 15:11:35 UTC 2009 x86_64 GNU/Linux

```VirtualBox 1.5.6_OSE
XP Pro x32
Does it has anything to do with the X64 version of Ubuntu?



It seems to be not.Becasuse Mine is X32....

---

### Post by lnthai2002 on 2009-05-31
I see the light.
Problem: When i installed virtual box from universe source(OSE), the package version is > 2.0 but it download and use the guest addition CD 1.5 (check the ISO file name you will see)
Solution: replace virtualbox-OSE with virtualbox commercial (it has more feeature like USB support and is free for individual use). Follow this instruction:
NOTE: if you done want to reinstall XP, just dont delete the VM nor the XP partition. The new virtualbox will reuse OSE config so it can see the previous installed XP.

[http://www.samlesher.com/ubuntu/virtualbox-with-usb-support-on-ubuntu](http://www.samlesher.com/ubuntu/virtualbox-with-usb-support-on-ubuntu)

Have fun

PS:You should to delete the old guestAddition ISO before downloading a new one. Vbox commercial will automatically download a new one call VboxGuestAddition.iso (no version number)

---

