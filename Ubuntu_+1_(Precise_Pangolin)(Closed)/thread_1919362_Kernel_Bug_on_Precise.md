---
title: "Kernel Bug on Precise"
date: 2012-02-02
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by FaBMak on 2012-02-02
I've upgraded from Oneiric to Precise. The problem is that i'm experimenting kernel panic a couple minutes after boot.

I've never get a bug in Ubuntu's kernels until now. So, how do i report a bug, since i can't boot on Precise kernel? Wich files do i have to send?

I waited a week for new versions on the kernel, but the problem persists. Now, i've two options: boot on Oneiric kernel (3.0) or use a LiveUSB.

---

### Post by xyzzyman on 2012-02-02
It's most likely this: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/917962](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/917962)

The fix has been finally been found and committed, and will come through with the next kernel update. It affects me using 3.2 kernels on oneiric also, and the fix was made in 3.3 and is now being backported. For now you will probably just have to use the Oneiric kernel and see if that's it. I'm lucky that it doesn't kick me off, and I have it set to ignore it and just log it, but I've read of alot of people with it locking.

---

### Post by kevpan815 on 2012-02-02
> **FaBMak said:**
> I've upgraded from Oneiric to Precise. The problem is that i'm experimenting kernel panic a couple minutes after boot.

I've never get a bug in Ubuntu's kernels until now. So, how do i report a bug, since i can't boot on Precise kernel? Wich files do i have to send?

I waited a week for new versions on the kernel, but the problem persists. Now, i've two options: boot on Oneiric kernel (3.0) or use a LiveUSB.

It's affecting me too on my Net Book. One Work Around that works for me is to use the Guest Account instead of my Administrator Account, the Kernel Panic does NOT occur for me in the Guest Account. The problem is with your Realtek Sound Card. There was a mistake made in the latest Kernel Opps File Update!

---

### Post by xyzzyman on 2012-02-02
> **kevpan815 said:**
> It's affecting me too on my Net Book. One Work Around that works for me is to use the Guest Account instead of my Administrator Account, the Kernel Panic does NOT occur for me in the Guest Account. The problem is with your Realtek Sound Card. There was a mistake made in the latest Kernel Opps File Update!

No, it you look at the fix it was the realtek usb storage driver. The patch is:

```
-                       usb_autopm_put_interface(us->pusb_intf);
+                       usb_autopm_put_interface_async(us->pusb_intf);

```

I'm compiling a 3.2 kernel with the latest ubuntu patches and that fix for my 11.10 install right now.

As far as using the guest account, all that is accomplishing is avoiding the notification. If you check your dmesg log you will find it would still be occuring.

EDIT: Fixed. Installed it on my 12.04 install also no panics.

---

### Post by kevpan815 on 2012-02-02
> **xyzzyman said:**
> No, it you look at the fix it was the realtek usb storage driver. The patch is:

```
-                       usb_autopm_put_interface(us->pusb_intf);
+                       usb_autopm_put_interface_async(us->pusb_intf);

```

I'm compiling a 3.2 kernel with the latest ubuntu patches and that fix for my 11.10 install right now.

As far as using the guest account, all that is accomplishing is avoiding the notification. If you check your dmesg log you will find it would still be occuring.

EDIT: Fixed. Installed it on my 12.04 install also no panics.

As far as I am aware, I have only 2 Realtek Integrated Devices on this Netbook: My Sound Card and My Ethernet Port on this PC. Just FYI.

---

### Post by xyzzyman on 2012-02-02
> **kevpan815 said:**
> As far as I am aware, I have only 2 Realtek Integrated Devices on this Netbook: My Sound Card and My Ethernet Port on this PC. Just FYI.

**JUST FYI** You have a Realtek card reader in that notebook.

[http://support.dell.com/support/edocs/systems/ins1012/en/cs/cs_en.pdf](http://support.dell.com/support/edocs/systems/ins1012/en/cs/cs_en.pdf)

---

### Post by kevpan815 on 2012-02-02
> **xyzzyman said:**
> **JUST FYI** You have a Realtek card reader in that notebook.

[http://support.dell.com/support/edocs/systems/ins1012/en/cs/cs_en.pdf](http://support.dell.com/support/edocs/systems/ins1012/en/cs/cs_en.pdf)

Thanks for sharing that info.

---

### Post by mdurham on 2012-02-02
We are not alone with this bug here are a couple of interesting discussion links.

[Bug 784404 – Kernel Panic after installing kernel-3.2.1-3.fc16.i686]("https://bugzilla.redhat.com/show_bug.cgi?id=784404")

[[SOLVED] Fedora16 kernel 3.2.1 panic on ATOM netbook - FedoraForum.org]("http://www.fedoraforum.org/forum/showthread.php?p=1549797")

---

### Post by kevpan815 on 2012-02-02
> **mdurham said:**
> We are not alone with this bug here are a couple of interesting discussion links.

[Bug 784404 – Kernel Panic after installing kernel-3.2.1-3.fc16.i686]("https://bugzilla.redhat.com/show_bug.cgi?id=784404")

[[SOLVED] Fedora16 kernel 3.2.1 panic on ATOM netbook - FedoraForum.org]("http://www.fedoraforum.org/forum/showthread.php?p=1549797")

I just fixed the problem on my Net Book by installing Ubuntu Kernel 3.3.0 RC2 from the Ubuntu Kernel PPA Mainline. Everything there was easy to install as all the Installer Files were in .DEB File Format. Just FYI.

---

### Post by xyzzyman on 2012-02-02
> **kevpan815 said:**
> I just fixed the problem on my Net Book by installing Ubuntu Kernel 3.3.0 RC2 from the Ubuntu Kernel PPA Mainline. Everything there was easy to install as all the Installer Files were in .DEB File Format. Just FYI.

Just FYI. Those are mainline kernel's. They are missing all the ubuntu patches, so it makes it hard to properly test and alpha Ubuntu 12.04 when you use a mainline kernel.

---

