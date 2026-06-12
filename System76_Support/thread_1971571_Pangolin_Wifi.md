---
title: "Pangolin Wifi"
date: 2012-05-02
forum: System76 Support
---

### Post by neomantic on 2012-05-02
My Pangolin arrived yesterday, and so far I'm impressed.  I bought it because I knew it would work with Linux, and indeed, everything seemed to 'just worked' when it booted into ubuntu...including wifi.  

But I'm a long time Debian, since Debian Potato, so I switched it to the latest unstable Debian....which I run on another machine and seldom have problems with.  

Unfortunately, the wifi no longer works...I downloaded the latest stable kernel 3.2.16, and compiled it myself, since Debian's own kernel leaves out non-dfsg compliant drivers.  Booted it up, and the wifi still doesn't work.

When I say it doesn't, I mean, that there is no option to select a wifi hotspot using the Network manager.

After more investigating, I looked at dmseg, and found that it's an 
Intel(R) Wireless WiFi Link AGN driver for Linux, in-tree:
iwlwifi 0000:02:00.0: Detected Intel(R) Centrino(R) Wireless-N 1030 BGN, REV=0xB0

So the the wifi is being recognized, and the kernel module - lwlwifi - is being loading....this is confirmed by lsmod.

At this point, I'm stuck. If anyone can point the way to resolving this issue, I would greatly appreciate it.  I understand that this may be a debian issue, and this is a ubuntu support forum, but they are close cousins.

Chad

p.s., I've tried to download the System76 drivers, and install them, but, while the installation works, the driver system config doesn't because it depends on Ubuntu.  The docs say that the System76 drivers are open-source, but all I can find are the debs, and not the source.  Would installing the System76 drivers solve this problem?

---

### Post by kc1di on 2012-05-02
Don't have an exact answer for you but this similar thread might give a clue. 

[http://ubuntuforums.org/showthread.php?t=1830848]("http://ubuntuforums.org/showthread.php?t=1830848")

---

### Post by isantop on 2012-05-02
> **neomantic said:**
> My Pangolin arrived yesterday, and so far I'm impressed.  I bought it because I knew it would work with Linux, and indeed, everything seemed to 'just worked' when it booted into ubuntu...including wifi.  

But I'm a long time Debian, since Debian Potato, so I switched it to the latest unstable Debian....which I run on another machine and seldom have problems with.  

Unfortunately, the wifi no longer works...I downloaded the latest stable kernel 3.2.16, and compiled it myself, since Debian's own kernel leaves out non-dfsg compliant drivers.  Booted it up, and the wifi still doesn't work.

When I say it doesn't, I mean, that there is no option to select a wifi hotspot using the Network manager.

After more investigating, I looked at dmseg, and found that it's an 
Intel(R) Wireless WiFi Link AGN driver for Linux, in-tree:
iwlwifi 0000:02:00.0: Detected Intel(R) Centrino(R) Wireless-N 1030 BGN, REV=0xB0

So the the wifi is being recognized, and the kernel module - lwlwifi - is being loading....this is confirmed by lsmod.

At this point, I'm stuck. If anyone can point the way to resolving this issue, I would greatly appreciate it.  I understand that this may be a debian issue, and this is a ubuntu support forum, but they are close cousins.

Chad

p.s., I've tried to download the System76 drivers, and install them, but, while the installation works, the driver system config doesn't because it depends on Ubuntu.  The docs say that the System76 drivers are open-source, but all I can find are the debs, and not the source.  Would installing the System76 drivers solve this problem?

Once the Deb is installed, the source is located at /opt/system76 . It would be separate, but it's just python.

---

### Post by osx424242 on 2012-05-02
> **neomantic said:**
> Unfortunately, the wifi no longer works...I downloaded the latest stable kernel 3.2.16, and compiled it myself, since Debian's own kernel leaves out non-dfsg compliant drivers.  Booted it up, and the wifi still doesn't work.
...
When I say it doesn't, I mean, that there is no option to select a wifi hotspot using the Network manager.

Is there a reason you didn't just enable the non-free repository and install firmware-iwlwifi?  I thought, at least in Squeeze (current Stable), that was where the drivers for the most (all?) Intel WiFi cards were: [http://packages.debian.org/squeeze/firmware-iwlwifi](http://packages.debian.org/squeeze/firmware-iwlwifi) .

I grabbed the .deb for Sid and it includes 'iwlwifi-6000g2b-5.ucode', while the Intel driver site [http://intellinuxwireless.org/?n=downloads](http://intellinuxwireless.org/?n=downloads) has a link to "iwlwifi-6000g2b-ucode-18.168.6.1.tgz" for the "Wireless-N 1030."  Since the appropriate driver seems to already be in the package, I'd revert to the stock kernel and try firmware-iwlwifi.

---

### Post by neomantic on 2012-05-03
Thanks for everyone's help.  It did, indeed, turn out to be a firmware problem.  Although the intel wireless site say that their driver is in kernel, and although building a kernel manually using debian's tool creates a package with firmware, the necessary firmware is not in that package.  I had to download the firmware myself, and install it in /lib/firmware.   

I know have wifi working.  Thanks again!

Chad

---

