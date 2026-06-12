---
title: "Any way to virtualize Win 7 from a preinstalled PC?"
date: 2012-01-05
forum: Virtualisation
---

### Post by Kurtosis on 2012-01-05
Hello,

I just bought a laptop with Win 7 preinstalled, and I want to backup Win 7, format the hdd, install Linux, then install the backed up Win 7 image as a virtualized guest (probably VirtualBox, maybe VMWare).

It appears from several threads I've found via googling that it is not possible to do this using the OEM's system recovery discs (HP), nor using the Windows Recovery Disc created with recdisc.exe. Is it possible using some other method, perhaps by cloning the drive with Clonezilla?

If not, what's the best option for getting a copy of Win 7 (64bit, at least Home Premium or better) for a virtualized guest installation on linux? Is the full, non-OEM, Win 7 installation DVD the only option?

Thanks!

---

### Post by 2F4U on 2012-01-06
The problem is that if you clone the installed OS and deploy it into a VM, Windows is still using the old hardware configuration. But since it is a VM, the hardware shown to Windows will be totally different. I think for an installation in a VM you can use any install media. The difference between OEM and retail versions is that with OEM you don't have any kind of support from Microsoft, thats why it is usually cheaper.

---

### Post by Kurtosis on 2012-01-06
Ah, thanks.  A bit annoying to pay the MS tax and not even be able to use it in a vm.  :/

---

### Post by 2F4U on 2012-01-06
I may have been a bit too fast in saying that you couldn't do it. Just found out about VMware vCenter Converter

[http://www.vmware.com/products/converter/](http://www.vmware.com/products/converter/)

This tool seems to be able to convert physical installations into a VM.

---

### Post by Kurtosis on 2012-01-06
That's the best option I've seen so far.  Thanks!

---

### Post by dcstar on 2012-01-11
> **2F4U said:**
> I may have been a bit too fast in saying that you couldn't do it. Just found out about VMware vCenter Converter

[http://www.vmware.com/products/converter/](http://www.vmware.com/products/converter/)

This tool seems to be able to convert physical installations into a VM.

It has been doing this sort of thing successfully for many years, there is no "seems" about it!

---

### Post by japzone on 2012-01-13
[s]Are there OpenSource alternatives to this(with VirtualBox output formats) or is VMware's solution the only reliable one?[/s]
Scratch that. If I really feel like running a Pure VB setup I can always convert the VMDK to VDI but VMDKs work fine in VB so why waste the extra effort.

---

### Post by kurt18947 on 2012-01-14
Depending on which Win7 you're machine is licensed for, you could download and burn an oem version of Windows, image your existing install for safety sake then wipe, install Linux, VM then install Win7 from your burned disk.  It doesn't seem like this would not a violation of any licensing as long as the 'flavor' is the same e.g. Home Premium, Pro etc.  Here is a download source:
[http://www.mydigitallife.info/download-windows-7-iso-official-32-bit-and-64-bit-direct-download-links/](http://www.mydigitallife.info/download-windows-7-iso-official-32-bit-and-64-bit-direct-download-links/)
You still need the appropriate license/key to activate.

---

