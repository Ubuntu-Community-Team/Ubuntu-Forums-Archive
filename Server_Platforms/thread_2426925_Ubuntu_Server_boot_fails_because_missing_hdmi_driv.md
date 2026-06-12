---
title: "Ubuntu Server boot fails because missing hdmi drivers"
date: 2019-09-15
forum: Server Platforms
---

### Post by kaefert66014235 on 2019-09-15
Hi there!

I've installed Ubuntu Server 19.04 on my [Qnap TS-469L]("https://www.qnap.com/en/product/ts-469l/specs/hardware") NAS (powered by an Intel Atom x86_64 CPU).

At first I've tried to use ubuntu-19.04-live-server-amd64.iso image, but I could not get that to work because the HDMI output seems to only work in text mode with Ubuntu (in contrast to the super old and out of date proprietary qnap linux version) and the *live* isos seem to have a graphical installer.

So I found the text based installer iso [ubuntu-19.04-server-amd64.iso]("http://cdimage.ubuntu.com/releases/19.04/release/ubuntu-19.04-server-amd64.iso) and managed to install Ubuntu Server 19.04 on my NAS using that.

Problem now is, the installed GRUB bootloader works and starts booting into the system, but it never reaches as console, but looses it's ability to paint stuff to the screen halfway through the boot process, probably because it tries to do some fancy graphics.

How can I make it boot just into a text console, and forget about that graphics stuff?

I tried writing a "3" and or "text" in the GRUB line starting with "linux" but that didn't help, just varied the text size before my HDMI screen switches to the "No Signal" picture. I've also tried some of those [https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions).

It might also be that the LUKS key entry is some graphics stuff which doesn't show because of missing graphics drivers and prevents the system from booting completely (because I don't see it in my network and the ssh server installed during setup doesn't show up)

Can somebody help me get this to work?

---

### Post by darkod on 2019-09-15
As far as I know the -server- ISO doesn't do any graphics except the basic text CLI.

Have you tried LTS release like 18.04? That is the latest LTS.

---

### Post by kaefert66014235 on 2019-09-15
hmm, strange. maybe it just increases the text resolution sometime during boot?

I'm trying Ubuntu 18.04 next. Currently clicking through the minimal network installer iso..

UPDATE: somethings broken in that installer. I can't setup LUKS partitions, on entering the passphrase it flashes very shortly the text:
> libgcc_s.so.1 must be installed for pthread_canel to work
And it will just ask for the same passphrase in an endless loop.

UPDATE2: just tried with ubuntu-18.04.3-server-amd64.iso - same problem. can't setup encrypted partitions with 18.04

---

### Post by darkod on 2019-09-15
Are you encrypting the root partition too?

---

### Post by kaefert66014235 on 2019-09-15
yes, I had planned to, but now I'm trying to install 18.04 without encryption. let's see if that works.

---

### Post by darkod on 2019-09-15
If you are encrypting root make sure you have separate /boot partition, unencrypted. I think it needs that to work correctly.

I use 18.04 with encrypted partitions for data, but not root. And it works OK for me. In fact I had set up the data partitions encryption long time ago, and then reinstalled just the OS when 18.04 came out. It picked up the old encrypted partitions without any problems.

---

### Post by kaefert66014235 on 2019-09-15
18.04 shows the same behavior as 19.04. Boot process starts and shows some lines but then the display is black and the ssh server never comes online. I'm gonna try Debian now, let's see if that works any different. Installer looks very similar.

UPDATE: Debian worked, though the netinstaller took so long and I'm already so tired that I forgot what user name and password I configured hours ago. So I'm redoing the installation again and documented it a bit better this time round ;)

---

### Post by mastablasta on 2019-09-16
what is the GPU chip used?

---

### Post by kaefert66014235 on 2019-09-16
If you can tell me how to find that out (with a running debian 10 installation) I can tell you...

---

### Post by kaefert66014235 on 2019-09-16
found this guide: [https://www.cyberciti.biz/faq/linux-tell-which-graphics-vga-card-installed/](https://www.cyberciti.biz/faq/linux-tell-which-graphics-vga-card-installed/)

> $ sudo lspci -v -s 00:02.0
00:02.0 VGA compatible controller: Intel Corporation Atom Processor D2xxx/N2xxx Integrated Graphics Controller (rev 09) (prog-if 00 [VGA controller])
	Subsystem: Intel Corporation Atom Processor D2xxx/N2xxx Integrated Graphics Controller
	Flags: bus master, fast devsel, latency 0, IRQ 32
	Memory at c0300000 (32-bit, non-prefetchable) [size=1M]
	I/O ports at 4110 [size=8]
	[virtual] Expansion ROM at 000c0000 [disabled] [size=128K]
	Capabilities: [d0] Power Management version 2
	Capabilities: [b0] Vendor Specific Information: Len=07 <?>
	Capabilities: [90] MSI: Enable+ Count=1/1 Maskable- 64bit-
	Kernel driver in use: gma500
	Kernel modules: gma500_gfx


But after some reflection I'm no longer so sure that the HDMI / VGA stuff is at fault, because even without them it should have become visible in my LAN which it didn't.
Luckily for me Debian 10 works, even though Ubuntu 18.04 and Ubuntu 19.04 didn't.

---

### Post by mastablasta on 2019-09-17
some chips on atom did not have linux support at all. i can't remember which ones. but they were not actually made by intel, just designed and then outsourced. because the rest of intel chips have opensource drivers and are not an issue on linux.

in any case use what works best. Debian is a very good OS, especially for servers. and it's is not that much different from Ubuntu. their documentation is also very good and i often use it for Ubuntu as well.

---

### Post by kaefert66014235 on 2019-09-17
Yes, I know Debian is a fine Linux distribution (and the base of Ubuntu and therefore quite similar to it) - That's why I've tried it next after Ubuntu sadly didn't work for me.

I just would have preferred Ubuntu, since I've got much more experience with it and I love the community communication channels available for Ubuntu such as ubuntuforums.org here.

Yes since this Qnap TS-469L is hardware that was never sold with the expectation that users would install a different operating system on it, I'm on a seldom travelled path here and it seems there are some incompatibilities.

I'm positively surprised that Debian 10 works without a problem, and would love it if somebody more knowledgeable than me could help me debug why Ubuntu doesn't.

---

### Post by mastablasta on 2019-09-18
Drivers in linux are part of kernel (core of the OS)

Debian 10 has kernel 4.19
Ubuntu 18.04 and 18.04.1 has kernel 4.15
Ubutnu 18.04.2 has kernel 4.18
Ubutnu 18.04.3 has kernel 5.0
[COLOR=#333333][FONT=&amp]
Each kernel has smaller or larger changes to drivers. sometimes thing get dropped or sometimes there are regressions. you could try an older version of Ubuntu server - the 18.04.1 It is supported for 5 years with security updates.
[/FONT][/COLOR][http://old-releases.ubuntu.com/releases/18.04.1/](http://old-releases.ubuntu.com/releases/18.04.1/)

if this was a regression that caused the issue, it might get fixed. if some drivers (e.g. GPU or CPU support) got dropped from kernel with version 5.0 then time on your hardware started to run out. :( unless you are willing to patch the kernel or build one yourself (not something i would do).

---

### Post by kaefert66014235 on 2019-09-18
ah okey, that's a good angle. I guess I could try different kernel versions under Debian 10? Is there an easy way to do that? On my Desktop I saw some GUI near the updater thingy to choose different kernel versions, can I do something similar on a Debian 10 server?

---

### Post by mastablasta on 2019-09-18
yes, you can. but if debian works you need to try Ubuntu with older kernel. if you downloaded from ubuntu website the default downloaded image will be the latest version. so you would have used 18.04.3, but you need to download and try 18.04.1, to see if kernel is the issue.

---

### Post by kaefert66014235 on 2019-09-19
okey so in the default Debian 10 repositories I could only find a very limited range of available Kernel versions:

```
$ sudo apt-cache search linux-image
linux-headers-4.19.0-6-amd64 - Header files for Linux 4.19.0-6-amd64
linux-headers-4.19.0-6-cloud-amd64 - Header files for Linux 4.19.0-6-cloud-amd64
linux-headers-4.19.0-6-rt-amd64 - Header files for Linux 4.19.0-6-rt-amd64
linux-image-4.19.0-6-amd64-dbg - Debug symbols for linux-image-4.19.0-6-amd64
linux-image-4.19.0-6-amd64-unsigned - Linux 4.19 for 64-bit PCs
linux-image-4.19.0-6-cloud-amd64-dbg - Debug symbols for linux-image-4.19.0-6-cloud-amd64
linux-image-4.19.0-6-cloud-amd64-unsigned - Linux 4.19 for x86-64 cloud
linux-image-4.19.0-6-rt-amd64-dbg - Debug symbols for linux-image-4.19.0-6-rt-amd64
linux-image-4.19.0-6-rt-amd64-unsigned - Linux 4.19 for 64-bit PCs, PREEMPT_RT
linux-image-amd64-signed-template - Template for signed linux-image packages for amd64
linux-image-amd64 - Linux for 64-bit PCs (meta-package)
linux-image-amd64-dbg - Debugging symbols for Linux amd64 configuration (meta-package)
linux-image-cloud-amd64 - Linux for x86-64 cloud (meta-package)
linux-image-cloud-amd64-dbg - Debugging symbols for Linux cloud-amd64 configuration (meta-package)
linux-image-rt-amd64 - Linux for 64-bit PCs (meta-package), PREEMPT_RT
linux-image-rt-amd64-dbg - Debugging symbols for Linux rt-amd64 configuration (meta-package)
linux-image-4.19.0-6-amd64 - Linux 4.19 for 64-bit PCs (signed)
linux-image-4.19.0-6-cloud-amd64 - Linux 4.19 for x86-64 cloud (signed)
linux-image-4.19.0-6-rt-amd64 - Linux 4.19 for 64-bit PCs, PREEMPT_RT (signed)
linux-headers-4.19.0-5-amd64 - Header files for Linux 4.19.0-5-amd64
linux-headers-4.19.0-5-cloud-amd64 - Header files for Linux 4.19.0-5-cloud-amd64
linux-headers-4.19.0-5-rt-amd64 - Header files for Linux 4.19.0-5-rt-amd64
linux-image-4.19.0-5-amd64-dbg - Debug symbols for linux-image-4.19.0-5-amd64
linux-image-4.19.0-5-amd64-unsigned - Linux 4.19 for 64-bit PCs
linux-image-4.19.0-5-cloud-amd64-dbg - Debug symbols for linux-image-4.19.0-5-cloud-amd64
linux-image-4.19.0-5-cloud-amd64-unsigned - Linux 4.19 for x86-64 cloud
linux-image-4.19.0-5-rt-amd64-dbg - Debug symbols for linux-image-4.19.0-5-rt-amd64
linux-image-4.19.0-5-rt-amd64-unsigned - Linux 4.19 for 64-bit PCs, PREEMPT_RT
linux-image-4.19.0-5-amd64 - Linux 4.19 for 64-bit PCs (signed)
linux-image-4.19.0-5-cloud-amd64 - Linux 4.19 for x86-64 cloud (signed)
linux-image-4.19.0-5-rt-amd64 - Linux 4.19 for 64-bit PCs, PREEMPT_RT (signed)
```

But from the info you've posted under the assumption that the problem is a kernel regression the 3 Ubuntu versions 18.04, 18.04.1 and 18.04.2 should work the same as Debian 10 does.

---

