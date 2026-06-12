---
title: "Kernel 4.3 RC (Release Candidate) series"
date: 2015-09-13
forum: Ubuntu Development Version
---

### Post by Doug S on 2015-09-13
Kernel 4.3RC1 is [available]("http://kernel.ubuntu.com/~kernel-ppa/mainline/v4.3-rc1-unstable/"). It'll be several hours before I can try it.

EDIT 1: I spoke too soon. The builds in the Ubuntu PPA link I gave above seem incomplete, so far. I'll see if I can build it myself.
EDIT 2: The build fails for me. I am attempting to build the kernel.org one, and just set the build to use default configs for anything new in the kernel configuration. i.e. I did this:```
doug@s15:~/temp-k-git/linux$ git checkout -b k43rc1_stock v4.3-rc1
Switched to a new branch 'k43rc1_stock'
doug@s15:~/temp-k-git/linux$ time make -j9 olddefconfig deb-pkg LOCALVERSION=stock

```and it errored out here:```
  HOSTCC  scripts/sign-file
scripts/sign-file.c:20:25: fatal error: openssl/bio.h: No such file or directory
 #include <openssl/bio.h>
                         ^
compilation terminated.
  HOSTCC  scripts/extract-cert
make[4]: *** [scripts/sign-file] Error 1
make[4]: *** Waiting for unfinished jobs....
scripts/extract-cert.c:23:25: fatal error: openssl/bio.h: No such file or directory
 #include <openssl/bio.h>
```

EDIT 3: I installed the libssl-dev package and was able to proceed with the compile. There seems to be new stuff involved for signing kernel modules. The resulting compiled kernel seems to run O.K., so far.

---

### Post by dino99 on 2015-09-13
4.3 have again lot of changes; so expecting some hard times with the first RCs (1 - 4)

---

### Post by Doug S on 2015-09-13
> **dino99 said:**
> 4.3 have again lot of changes; so expecting some hard times with the first RCs (1 - 4)Dino, yes of course. However I would expect it to at least build.
By the way, I see the exact same error as I got in the [PPA build log for amd64]("http://kernel.ubuntu.com/~kernel-ppa/mainline/v4.3-rc1-unstable/BUILD.LOG.amd64").

---

### Post by Doug S on 2015-09-13
Compiling the kernel now seems to depend on the libssl-dev package. I edited my original post.

---

### Post by Doug S on 2015-09-13
There seems to have been some recent changes in the Makefile. As a result, there is bunch of stuff going on during compile that I do not want.

1.) There are several files created that didn't used to be and that I do not want:

linux-4.3.0-rc1stock_4.3.0-rc1stock-48.debian.tar.gz
linux-4.3.0-rc1stock_4.3.0-rc1stock.orig.tar.gz
linux-4.3.0-rc1stock_4.3.0-rc1stock-48.dsc
linux-4.3.0-rc1stock_4.3.0-rc1stock-48_amd64.changes

2.) There are a great many "dpkg-genchanges" and "Use of uninitialized value" warnings at the end of the compile.

However, reading the commit messages reveals that there was new directive added to do it the old way, just generating the binary packages.
So now, instead of doing this:
```
time make -j9 olddefconfig deb-pkg LOCALVERSION=stock
```I would do this:```
time make -j9 olddefconfig bindeb-pkg LOCALVERSION=stock
```However, that still seems to generate the .change file and the 532 lines of "dpkg-genchanges" and "Use of uninitialized value" crap.

EDIT:

Commit 3716001bcb7f5822382ac1f2f54226b87312cc6b does the messing around with the deb-pkg option and introduces the bindeb-pkg build option as "the old way".
I am suggesting that in scripts/package/builddeb this stuff:
+else
+       dpkg-genchanges -b > ../${sourcename}_${packageversion}_${debarch}.changes
+fi
shouldn't be there. Anyway, I have asked why on the #ubuntu-kernel IRC channel, and might eventually follow up on [EMAIL="linux-kbuild@vger.kernel.org"]linux-kbuild@vger.kernel.org[/EMAIL]

---

### Post by Doug S on 2015-09-15
The [daily build]("http://kernel.ubuntu.com/~kernel-ppa/mainline/daily/current/") is finally fixed.

Upstream, and after some e-mails back and forth, a [patch has been submitted]("http://www.spinics.net/lists/linux-kbuild/msg11638.html") to address the bindeb-pkg build issues. I do not know if it will make it into RC2 or not.

---

### Post by zika on 2015-09-16
I've just had enough time to try it and to see that it has some problems with EHCI, OHCI at PCI (no USB mouse...)
I will try to investigate more either while at work or when I come back home.
Update1: On laptop (same set of .deb files, 15.04) it works OK.
Update2: No more luck with newer version of rc1 (issued today on mainline)... But, more opportunity for debug I guess...
Update3: Works OK. Nice.

---

### Post by fyfe54 on 2015-09-16
I just installed 4.3RC1 from ~kernel-ppa/mainline/.  Went smoothly and it has been running for all of 17 minutes now.
System76 Gazelle Pro (April 2014) Ubuntu 15.04

---

### Post by rrnbtter on 2015-09-17
Greetings,
Installed on 16th all was ok, with recent updates, trash. Back to 4.2 for a bit.

---

### Post by Doug S on 2015-09-27
Kernel 4.3-rc3 is available. While I have not been running it for long, it has been under heavy burden on my test server. So far so good.

> **Doug S said:**
> a [patch has been submitted]("http://www.spinics.net/lists/linux-kbuild/msg11638.html") to address the bindeb-pkg build issues. I do not know if it will make it into RC2 or not.For whatever reason, the maintainer has not yet pushed the patch into the mainstream.

---

### Post by P-I H on 2015-09-28
I have a Radeon R9 380 graphic card in my test system. There were a lot of AMDGPU fixes in 4.3-rc3 and I installed it. It is working fine so far with Chrome, Kodi and Civ5.

---

### Post by fyfe54 on 2015-09-30
Just udated to 15.10.  Smooth install and so far is running perfectly with kernel 4.3RC3.

---

### Post by Doug S on 2015-10-09
I have problems with S3 suspend, where it won't actually suspend. Found by accident while working on something else. [Bug report filed]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1504584"), and upstream notified.

---

### Post by Doug S on 2015-10-11
[Kernel 4.3-rc5 is available]("http://kernel.ubuntu.com/~kernel-ppa/mainline/v4.3-rc5-unstable/"). I am compiling it now.

---

### Post by rrnbtter on 2015-10-19
Greetings,
RC6 is approaching stability. Very decent on my system in fact. 

rrnbtter@rrnbtter-Satellite-L305:~$ inxi -Fz
System:    Host: rrnbtter-Satellite-L305 Kernel: 4.3.0-040300rc6-generic i686 (32 bit)
           Desktop: Unity 7.3.2  Distro: Ubuntu 15.10 wily
Machine:   System: TOSHIBA product: Satellite L305 v: PSLB8U-0JG037
           Mobo: TOSHIBA model: Portable PC
           Bios: INSYDE v: 2.20 date: 12/09/2009
CPU:       Single core Intel 585 (-UP-) cache: 1024 KB speed: 2161 MHz (max)
Graphics:  Card: Intel Mobile 4 Series Integrated Graphics Controller
           Display Server: X.Org 1.17.2 drivers: intel (unloaded: fbdev,vesa)
           Resolution: 1280x800@60.00hz
           GLX Renderer: Mesa DRI Mobile Intel GM45 Express x86/MMX/SSE2
           GLX Version: 2.1 Mesa 11.0.2
Audio:     Card Intel 82801I (ICH9 Family) HD Audio Controller
           driver: snd_hda_intel
           Sound: ALSA v: k4.3.0-040300rc6-generic
Network:   Card-1: Realtek RTL8101/2/6E PCI Express Fast/Gigabit Ethernet controller
           driver: r8169
           IF: enp2s0 state: down mac: <filter>
           Card-2: Qualcomm Atheros AR242x / AR542x Wireless Network Adapter (PCI-Express)
           driver: ath5k
           IF: wlp3s0 state: up mac: <filter>
Drives:    HDD Total Size: 500.1GB (30.0% used)
           ID-1: /dev/sda model: WDC_WD5000LPVX size: 500.1GB
Partition: ID-1: / size: 24G used: 8.1G (36%) fs: ext4 dev: /dev/sda3
           ID-2: /boot size: 1.9G used: 218M (12%) fs: ext4 dev: /dev/sda1
           ID-3: /home size: 429G used: 128G (32%) fs: ext4 dev: /dev/sda4
           ID-4: swap-1 size: 4.19GB used: 0.00GB (0%) fs: swap dev: /dev/sda2
RAID:      No RAID devices: /proc/mdstat, md_mod kernel module present
Sensors:   System Temperatures: cpu: 76.0C mobo: N/A
           Fan Speeds (in rpm): cpu: N/A
Info:      Processes: 211 Uptime: 31 min Memory: 493.2/3910.9MB
           Client: Shell (bash) inxi: 2.2.16

---

### Post by Doug S on 2015-10-19
While I haven't tried it yet, rc6 finally includes the fix for the builddeb issue, introduced in rc1.

---

### Post by rrnbtter on 2015-10-25
Greetings,
For anyone interested 4.3RC7 is out a half day early. But seems to be I386 only. At least for now.
Working fine here.

---

### Post by zika on 2015-10-25
> **rrnbtter said:**
> Greetings,
For anyone interested 4.3RC7 is out a half day early. But seems to be I386 only. At least for now.
Working fine here.```
[COLOR=#000000]Debug: /home/kernel/COD/linux/debian/stamps/stamp-build-generic spl
[/COLOR]install -d /home/kernel/COD/linux/debian/build/build-generic/spl
rsync -a --exclude=dkms.conf --delete spl/ /home/kernel/COD/linux/debian/build/build-generic/spl/
rsync: change_dir "/home/kernel/COD/linux//spl" failed: No such file or directory (2)
rsync error: some files/attrs were not transferred (see previous errors) (code 23) at main.c(1183) [sender=3.1.0] 
[COLOR=#000000]make: *** [/home/kernel/COD/linux/debian/stamps/stamp-build-generic] Error 23[/COLOR]
```It seems that there is a systematic trouble at mainline with 64-bit compile...
[http://ubuntuforums.org/showthread.php?t=2285505&p=13378385#post13378385](http://ubuntuforums.org/showthread.php?t=2285505&p=13378385#post13378385)

---

### Post by Doug S on 2015-10-25
> **rrnbtter said:**
> Greetings,
For anyone interested 4.3RC7 is out a half day early. But seems to be I386 only. At least for now.
Working fine here.I built my own 64 bit rc7 kernel. It seems to be running O.K., but still with the suspend issue I [commented on]("http://ubuntuforums.org/showthread.php?t=2294800&page=2&p=13370248#post13370248") a couple of weeks ago.

---

### Post by rrnbtter on 2015-11-02
Greetings,
Kernel 4.3 up and working fine. Very crisp experience.

Linux rrnbtter-Satellite-L305 4.3.0-040300-generic #201511012034 SMP Mon Nov 2 01:51:22 UTC 2015 i686 i686 i686 GNU/Linux

---

### Post by rrnbtter on 2015-11-02
Greetings, 
Well, now in addition to the previous,  dev has released a 4.3 Wily edition [http://kernel.ubuntu.com/~kernel-ppa/mainline/v4.3-wily/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v4.3-wily/) . Think I will take a look at the change log and see what the difference is. 
FYI

---

### Post by Doug S on 2016-03-08
> **Doug S said:**
> I have problems with S3 suspend, where it won't actually suspend. Found by accident while working on something else. [Bug report filed]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1504584"), and upstream notified.The issue persisted for me, on my test system, right through kernel 4.5-rc5 (or 6). My test system was 14.04 server based. I just did a fresh install of 16.04 server edition, and this issue is not present (so far).

---

### Post by QDR06VV9 on 2016-03-08
I have been running this on trusty && everything is good,,not a laptop so the suspend is not an issue here..
Logout and login works... well long story short all is ubuntu good..
```
System:    Host: TheGhost Kernel: 4.3.0-040300-lowlatency x86_64 (64 bit) Desktop: N/A Distro: Ubuntu 14.04 trusty
Machine:   System: Acer product: Aspire M3300
           Mobo: Acer model: FRS780M Bios: American Megatrends version: P03-B0 date: 11/16/2009
CPU:       Quad core AMD Phenom II X4 810 (-MCP-) clocked at 2600.00 MHz 
Graphics:  Card: NVIDIA GF119 [GeForce GT 520] 
           X.Org: 1.15.1 drivers: nvidia (unloaded: fbdev,vesa,nouveau) Resolution: 1920x1080@60.0hz 
           GLX Renderer: GeForce GT 520/PCIe/SSE2 GLX Version: 4.5.0 NVIDIA 355.11
Network:   Card-1: Marvell 88E8071 PCI-E Gigabit Ethernet Controller driver: sky2 
           Card-2: Realtek RTL-8100/8101L/8139 PCI Fast Ethernet Adapter driver: 8139too 
Drives:    HDD Total Size: 2532.5GB (2.4% used)
Info:      Processes: 221 Uptime: 14 min Memory: 531.4/5967.2MB Client: Shell (bash) inxi: 1.9.17
```

---

### Post by Doug S on 2016-03-08
> **runrickus said:**
> I have been running this on trusty && everything is good,,not a laptop so the suspend is not an issue here..My test server is not a LapTop either. I was doing S3 suspends manually, for something else I was working on at the time. Once I get my build environment setup again, I'll try a kernel (4.5) I compile myself.

---

### Post by QDR06VV9 on 2016-03-08
> **Doug S said:**
> My test server is not a LapTop either. I was doing S3 suspends manually, for something else I was working on at the time. Once I get my build environment setup again, I'll try a kernel (4.5) I compile myself.

I should have realized that(Server) sorry.
But I can do a "sudo pm-suspend" and it works... still a little lag before resume, but been that way since i can remember.
regards

---

