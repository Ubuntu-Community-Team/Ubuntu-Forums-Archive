---
title: "Possible missing firmware /lib/firmware/rtl_nic/rtl8168f-2.fw for module r8169"
date: 2011-12-07
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by mdurham on 2011-12-07
I get the following when installing the latest kernel. I also can't use this kernal as it crashes when it gets to logging in to the user.
> Kernel panic - not syncing: fatal exception in interrupt.
Any ideas how to fix?
Cheers, Mike

> update-initramfs: Generating /boot/initrd.img-3.2.0-3-generic
W: Possible missing firmware /lib/firmware/rtl_nic/rtl8168f-2.fw for module r8169
W: Possible missing firmware /lib/firmware/rtl_nic/rtl8168f-1.fw for module r8169

---

### Post by Irihapeti on 2011-12-08
I've been getting the missing firmware message for quite some time. I have no idea how to fix it, but it doesn't seem to be affecting normal operation.

I suspect that the kernel panic is related to something else.

---

### Post by Harry33 on 2011-12-08
Same here.
However, it really does not seem to be harmfull, just a warning.
It would still be interesting to know if anyone has that particular Realtec NIC (r8168f) hardware.
My Realtek 8111D works very well the r8169 provided by kernel.

---

### Post by ArtLaForge on 2011-12-08
> **Harry33 said:**
> Same here.
However, it really does not seem to be harmfull, just a warning.
It would still be interesting to know if anyone has that particular Realtec NIC (r8168f) hardware.
My Realtek 8111D works very well the r8169 provided by kernel.

I have been getting this error also. My symptoms seem to be limited to no audio after upgrad/reboot but activating rythmbox and playing something usually restores the audio..

I also have the Realtec NIC but haven't experienced Ethernet problems.

---

### Post by zika on 2011-12-08
Closest to finding these two file is this: [http://patchwork.ozlabs.org/patch/112825/](http://patchwork.ozlabs.org/patch/112825/)...

---

### Post by fjgaude on 2011-12-08
> **Harry33 said:**
> Same here.
However, it really does not seem to be harmfull, just a warning.
It would still be interesting to know if anyone has that particular Realtec NIC (r8168f) hardware.
My Realtek 8111D works very well the r8169 provided by kernel.

My Realtek RTL8111/8168B works fine with 12.04. NM shows it loads r8169 driver.

---

### Post by Harry33 on 2011-12-15
There was an update to the package linux-firmware (1.63):
[FONT=monospace]
[/FONT]> linux-firmware (1.63) precise; urgency=low
Add rtl8168d-2.fw to nic-firmware.  LP: #900750.

This was rtl8168d, not rtl8168f though.

---

### Post by mdurham on 2011-12-15
Why is it **Possible** missing firmware, Doesn't it know if it's missing or not?
Anyway, where can we get the **definately** missing firware?
Cheers, Mike

---

### Post by zika on 2011-12-15
```
cd /lib/firmware/rtl_nic/
sudo cp rtl8168e-1.fw rtl8168f-1.fw
sudo cp rtl8168e-2.fw rtl8168f-2.fw
sudo update-initramfs -u -k `uname -r`
```
That got me from seeing that warning.
I do not advise this to anyone else. It worked for me, I have several kernels so if this one (999) got corrupted I could boot with any other...
```
:~$ sudo lshw |grep 8169
configuration: autonegotiation=off broadcast=yes [COLOR="Red"]driver=r8169[/COLOR] driverversion=2.3LK-NAPI duplex=full firmware=N/A ip=192.168.0.44 latency=0 link=yes multicast=yes port=MII speed=100Mbit/s
```

---

### Post by Harry33 on 2011-12-15
> **mdurham said:**
> Why is it **Possible** missing firmware, Doesn't it know if it's missing or not?
Anyway, where can we get the **definately** missing firware?
Cheers, Mike

It is either missing (from kernel) or some kind of race condition makes a failure to load it.
Someone could make a bug report about this.
I cannot, because my hardware does not need that particular firmware.

---

### Post by zika on 2011-12-15
> **Harry33 said:**
> It is either missing (from kernel) or some kind of race condition makes a failure to load it.
Someone could make a bug report about this.
I cannot, because my hardware does not need that particular firmware.
Is it not my little exercise in [http://ubuntuforums.org/showpost.php?p=11539311&postcount=9](http://ubuntuforums.org/showpost.php?p=11539311&postcount=9) a proof that it is just a case of missing files declared somewhere in install-notes as &#8222;needed&#8220;...?

---

### Post by Harry33 on 2011-12-15
> **zika said:**
> Is it not my little exercise in [http://ubuntuforums.org/showpost.php?p=11539311&postcount=9](http://ubuntuforums.org/showpost.php?p=11539311&postcount=9) a proof that it is just a case of missing files declared somewhere in install-notes as „needed“...?

That rtl 8168f-2 firmware may be needed or it is only marked as needed somewhere.
Yes that is correct.
Your exercise would work around the situation where that particular firware is only marked as needed, but not really needed. However, it would not help if you had a hardware installed that really needed the 8168f-2 firmware.

---

### Post by Harry33 on 2011-12-15
Well now this issue has been fixed. The firmware rtl8168f has been added into new linux-firmware update: version 1.65

> **Changelog**

          linux-firmware (1.65) precise; urgency=low    * rtl_nic: add new firmware for RTL8111F  -- Tim Gardner <email address hidden>   Thu, 15 Dec 2011 15:14:21 -0700      


---

### Post by mdurham on 2011-12-15
> **Harry33 said:**
> Well now this issue has been fixed. The firmware rtl8168f has been added into new linux-firmware update: version 1.65

Fixed indeed.

---

### Post by Harry33 on 2011-12-16
> **mdurham said:**
> Fixed indeed.

Could you then mark this thread as "solved".

---

### Post by zika on 2011-12-16
> **Harry33 said:**
> That rtl 8168f-2 firmware may be needed or it is only marked as needed somewhere.
Yes that is correct.
Your exercise would work around the situation where that particular firware is only marked as needed, but not really needed. However, it would not help if you had a hardware installed that really needed the 8168f-2 firmware.I know. That is why I sad I would not advise this to anybody...

---

