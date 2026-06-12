---
title: "Free Virtualization OS for Laptop"
date: 2009-02-03
forum: Virtualisation
---

### Post by GV1pJTHl on 2009-02-03
Does anyone know of free or low cost Virtual Server such as [ESXi]("http://www.vmware.com/products/esxi/")? What we're looking for is something that we can use on our laptops to allow us to chose one or more VMs to boot into and switch between. An extremely lightweight Linux distro for this purpose would also be considered however we need something that will recognize the hardware on our laptops such as Bluetooth, Audio, Wireless, etc. Currently we're using Latitude D830s.

Thank you for your time.

---

### Post by PilotJLR on 2009-02-03
For a laptop, just install Ubuntu on it and then add Sun's VirtualBox. ESXi isn't suitable for laptops, especially if you want audio, wireless, etc.

Or use Xubuntu for a really light base.

---

### Post by HotShotDJ on 2009-02-03
> **GV1pJTHl said:**
> one or more VMs to boot into and switch between.This could be difficult.  Remember, you must assign a specific amount of RAM to each VM, which becomes unavailable to both the host OS and any other VM that you have running.  Depending on the actual physical RAM you have available, it my not be possible to have more than one VM open at a time.  However, if you only intend to run one VM at a time, you can have as many VM's installed as you have room on your hard drive.

VirtualBox would be a good choice.  It is relatively easy to use (as far as VM software goes).  However, unless you choose the OSE version, you'll have to pay a license fee if you are going to be using it commercially.  The PUEL -- Personal Use and Evaluation License -- version (which supports USB among other things that are not included in the OSE version) is only for personal use.  You can also use the PUEL free of charge for academic use.

---

