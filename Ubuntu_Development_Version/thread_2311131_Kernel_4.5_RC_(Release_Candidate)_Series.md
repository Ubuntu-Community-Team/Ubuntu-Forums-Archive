---
title: "Kernel 4.5 RC (Release Candidate) Series"
date: 2016-01-24
forum: Ubuntu Development Version
---

### Post by Doug S on 2016-01-24
Kernel [4.5-rc1]("http://kernel.ubuntu.com/~kernel-ppa/mainline/v4.5-rc1-wily/") is available, so I am starting this usual thread.
I am running my own compiled version, having stolen, and used, the Ubuntu kernel configuration file:
```
Linux s15 4.5.0-rc1-stock #153 SMP Sun Jan 24 18:01:09 PST 2016 x86_64 x86_64 x86_64 GNU/Linux
```

Links to some previous threads:
[4.4 RC series]("http://ubuntuforums.org/showthread.php?t=2303120")
[4.3 RC series]("http://ubuntuforums.org/showthread.php?t=2294800")
[4.2 RC series]("http://ubuntuforums.org/showthread.php?t=2285505")

---

### Post by MikeMecanic on 2016-01-25
```
xx45@ug:~$ dpkg --list | grep linux-image
ii  linux-image-4.4.0-1-generic           4.4.0-1.15                                 amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-4.5.0-040500rc1-generic   4.5.0-040500rc1.201601241731               amd64        Linux kernel image for version 4.5.0 on 64 bit x86 SMP
ii  linux-image-extra-4.4.0-1-generic     4.4.0-1.15                                 amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
xx45@ug:~$ 

```[LEFT][FONT=Georgia][B]
4.5RC_1
[/B]
```
cd /tmp
```[/FONT]
[/LEFT]
```
wget**\**
```
```
[COLOR=#000000][FONT=Georgia]kernel.ubuntu.com/~kernel-ppa/mainline/v4.5-rc1-wily/linux-headers-4.5.0-040500rc1_4.5.0-040500rc1.201601241731_all.deb\[/FONT][/COLOR]
```
```
[COLOR=#000000][FONT=Georgia]kernel.ubuntu.com/~kernel-ppa/mainline/v4.5-rc1-wily/llinux-headers-4.5.0-040500rc1-generic_4.5.0-040500rc1.201601241731_amd64.deb\[/FONT][/COLOR]
```
```
[COLOR=#000000][FONT=Georgia]kernel.ubuntu.com/~kernel-ppa/mainline/v4.5-rc1-wily/linux-image-4.5.0-040500rc1-generic_4.5.0-040500rc1.201601241731_amd64.deb[/FONT][/COLOR]
```
```
[FONT=Georgia]**s**udodpkg -i linux-headers-4.5*.deblinux-image-4.5*.deb[/FONT]
```

```
[FONT=Georgia]sudo reboot[/FONT]
```

---

### Post by P-I H on 2016-01-25
I installed the Ubuntu version from kernel.ubuntu.com/~kernel-ppa/mainline/v4.5-rc1-wily. It booted fine. However config parameter "CONFIG_DRM_AMD_POWERPLAY" isn't enabled and powerplay in AMDGPU isn't working.
I suppose I have to learn how do compile my own version.

---

### Post by P-I H on 2016-01-25
Compiled a custom kernel according to this page
[http://askubuntu.com/questions/724900/how-to-apply-kernel-patches](http://askubuntu.com/questions/724900/how-to-apply-kernel-patches)

AMD powerplay is working OK, when the config parameter "CONFIG_DRM_AMD_POWERPLAY=y" is set.

---

### Post by Doug S on 2016-01-25
> **P-I H said:**
> Compiled a custom kernel according to this page
[http://askubuntu.com/questions/724900/how-to-apply-kernel-patches](http://askubuntu.com/questions/724900/how-to-apply-kernel-patches)Interesting. I saw that post and thought that for it to work, this would also be needed (as of kernel 4.3):```
sudo apt-get install libssl-dev
```I also did not understand why apply the config patches and then just copy the config file anyway. (but I don't compile that way, so maybe I just don't understand.)

> **P-I H said:**
> AMD powerplay is working OK, when the config parameter "CONFIG_DRM_AMD_POWERPLAY=y" is set.And you didn't also need "amdgpu.powerplay=1" on your grub kernel command line, as per [this]("https://www.phoronix.com/scan.php?page=news_item&px=AMDGPU-PP-4.5-Steps")?

---

### Post by P-I H on 2016-01-25
> **Doug S said:**
> Interesting. I saw that post and thought that for it to work, this would also be needed (as of kernel 4.3):```
sudo apt-get install libssl-dev
```I also did not understand why apply the config patches and then just copy the config file anyway. (but I don't compile that way, so maybe I just don't understand.)

And you didn't also need "amdgpu.powerplay=1" on your grub kernel command line, as per [this]("https://www.phoronix.com/scan.php?page=news_item&px=AMDGPU-PP-4.5-Steps")?

Yes to both comments.

I installed packages according to two instructions
```
sudo apt-get install libncurses5-dev gcc make git exuberant-ctags bc libssl-dev
sudo apt-get install git build-essential kernel-package fakeroot libncurses5-dev

```

I had already changed the grub kernel command line as I have used a 4.4 kernel made by Phoronix.

The AMDGPU driver is almost as fast as the fglrx driver used on Ubuntu 15.10

---

### Post by P-I H on 2016-01-27
I had a problem with time & date on my custom kernel.
With the setting "Automatically from the Internet" i got wrong time and the error message
"systemd-timesyncd[5766]: Failed to call clock_adjtime(): Invalid argument"
After installing ntp and ntpdate I get the correct time and no error message.

---

### Post by MikeMecanic on 2016-02-01
[COLOR=#000000][FONT=Calibri]All smooth here. 
[/FONT][/COLOR]
Kernel 4.5 rc2
```
k4_5@uk:~$ dpkg --list | grep linux-image
ii  [COLOR=#ff0000]linux-image[/COLOR]-4.5.0-040500rc1-generic           4.5.0-040500rc1.201601241731               amd64        Linux kernel image for version 4.5.0 on 64 bit x86 SMP
ii  [COLOR=#ff0000]linux-image[/COLOR]-4.5.0-040500rc2-generic           4.5.0-040500rc2.201601312230               amd64        Linux kernel image for version 4.5.0 on 64 bit x86 SMP
k4_5@uk:~$ dpkg -l|grep firmware
ii  intel-microcode                               3.20151106.1                               amd64        Processor microcode [COLOR=#ff0000]firmware [/COLOR]for Intel CPUs
ii  linux-[COLOR=#ff0000]firmware [/COLOR]                               1.155                                      all          Firmware for Linux kernel drivers
k4_5@uk:~$ exit

```

EDIT: Made a perfect fresh install with today's build: Ubuntu Kylin Feb. 1st. 

```
xx@uk:~$ dpkg --list | grep linux-image
ii [COLOR=#ff0000] linux-image[/COLOR]-4.4.0-2-generic                   4.4.0-2.16                                 amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
ii  [COLOR=#ff0000]linux-image[/COLOR]-4.5.0-040500rc2-generic           4.5.0-040500rc2.201601312230               amd64        Linux kernel image for version 4.5.0 on 64 bit x86 SMP
ii [COLOR=#ff0000] linux-image[/COLOR]-extra-4.4.0-2-generic             4.4.0-2.16                                 amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
ii  [COLOR=#ff0000]linux-image[/COLOR]-generic                           4.4.0.2.1                                  amd64        Generic Linux kernel image
xx@uk:~$ exit

```

---

### Post by Doug S on 2016-02-05
Just catching up...
```
doug@s15:~$ uname -a
Linux s15 4.5.0-rc2-stock #156 SMP Fri Feb 5 09:26:07 PST 2016 x86_64 x86_64 x86_64 GNU/Linux
```
A lot of changes between rc1 and rc2, which is not unusual early in the cycle. Seems O.K. so far.

---

### Post by Doug S on 2016-02-07
Kernel 4.5-rc3 is available from [kernel.org]("https://www.kernel.org/"), but not yet in the[ Ubuntu mainline PPA]("http://kernel.ubuntu.com/~kernel-ppa/mainline/?C=N;O=D").
Myself, I'm going to wait before I compile it, so that I can steal the Ubuntu kernel configuration.

---

### Post by MikeMecanic on 2016-02-08
**There is only one missing piece here  :  Nautilus 3.18.x  **


```
x@k:~$ dpkg --list |grep linux-image
ii [COLOR=#ff3333]**linux-image**[/COLOR]-4.5.0-040500rc3-generic          4.5.0-040500rc3.201602071930               amd64       Linux kernel image for version 4.5.0 on 64 bit x86 SMP

x@k:~$ df -h | grep^/dev/sda1
[COLOR=#ff3333]**/dev/sda1**[/COLOR]                          236M   54M  170M  24% /boot

x@k:~$ sudo lsblk -oNAME,FSTYPE,SIZE,MOUNTPOINT,LABEL
NAME                        FSTYPE        SIZE MOUNTPOINT LABEL
sda                                     698.7G            
&#9500;&#9472;sda1                      ext2          243M /boot      
&#9500;&#9472;sda2                                      1K            
&#9492;&#9472;sda5                      LVM2_member 698.4G            
 &#9500;&#9472;ubuntu--kylin--vg-root   ext4        694.5G /          
 &#9492;&#9472;ubuntu--kylin--vg-swap_1 swap          3.9G [SWAP]     
sr0                                      1024M            

```

[http://news.softpedia.com/news/linus-torvalds-releases-a-slightly-bigger-than-expected-linux-kernel-4-5-rc3-500042.shtml](http://news.softpedia.com/news/linus-torvalds-releases-a-slightly-bigger-than-expected-linux-kernel-4-5-rc3-500042.shtml)

EDIT: Made a fresh install with Gnome today's image.  Didn't get any issues.

```
Kernel: 4.5.0-040500rc3-generic x86_64 (64 bit) Desktop: Gnome 3.18.3Distro: Ubuntu 16.04 xenial
```

---

### Post by IanW on 2016-02-08
> **MikeMecanic said:**
> **There is only one missing piece here  :  Nautilus 3.18.x  **

Perhaps because [this]("http://www.omgubuntu.co.uk/2016/02/ubuntu-16-04-reverts-to-older-version-of-nautilus")?

---

### Post by dino99 on 2016-02-08
nautilus 3.18-5 from gnome3 ppa here :p
wonder why the desktop team is introducing a bigger delta with the gnome dev trend ;) The little design problems are very harmless

---

### Post by P-I H on 2016-02-08
Compiled RC3.
Takes a little longer to boot
RC2
```
p-i@pi-GA-990FXA-UD3-xenial:~$ systemd-analyze
Startup finished in 4.808s (kernel) + 9.459s (userspace) = 14.267s
```
RC3
```
p-i@pi-GA-990FXA-UD3-xenial:~$ systemd-analyze
Startup finished in 8.996s (kernel) + 9.596s (userspace) = 18.593s

```
Unigine Valley has about the same result as on RC2 with POWERPLAY=y and a Radeon R9 380.
```
Unigine Valley Benchmark 1.0

FPS:    42.8
Score:    1790
Min FPS:15.4
Max FPS:65.2

System
Platform:    Linux 4.5.0-rc3-custom x86_64
CPU model:    AMD FX(tm)-8120 Eight-Core Processor (4024MHz) x8
GPU model:    Unknown GPU (256MB) x1

Settings
Render:    OpenGL
Mode:    1920x1200 fullscreen
Preset    Custom
Quality    High

Powered by UNIGINE Engine
Unigine Corp. © 2005-2013

```

---

### Post by jos-dehaes on 2016-02-08
Did you know, you can copy the old config file and do "make oldconfig", this will only prompt you for any new config items.

---

### Post by Doug S on 2016-02-08
> **jos-dehaes said:**
> Did you know, you can copy the old config file and do "make oldconfig", this will only prompt you for any new config items.I suspect that most people that compile their own mainline rc series kernels would know that.

For my part of it, I often steal the Ubuntu kernel configuration just keep synchronized the Ubuntu mainline rc kernels. I don't do it every time, but have noticed the Ubuntu kernel configuration often changes significantly, including changes to old settings. On these rc threads, we have found a few issues with the Ubuntu kernel configurations, that have resulted in bug reports and/or escalation to the kernel team via their IRC channel.

Myself, I have never ever used "make oldconfig", I Just compile telling it to use defaults wherever there is some kernel configuration decision needed, which can be particularly useful when doing a kernel bisection. I.E. my process for rc3 was:
```
cp /boot/config-4.5.0-040500rc3-generic .config-4.5.0-040500rc3-generic
cp .config .config-4.5-rc2-doug
cp .config-4.5.0-040500rc3-generic .config
scripts/config --disable DEBUG_INFO   [COLOR="#FF0000"]<<< Otherwise the kernel is giant sized and compile takes twice as long[/COLOR]
scripts/config --disable CC_STACKPROTECTOR_STRONG   [COLOR="#FF0000"]<<< Because I compile on a 14.04 server, with an older version of the c compiler[/COLOR]
cp .config .config-4.5-rc3-doug
git checkout master
git pull
git checkout -b k45rc3_stock v4.5-rc3
time make -j9 [COLOR="#FF0000"]olddefconfig[/COLOR] bindeb-pkg LOCALVERSION=-stock
sudo dpkg -i ../linux-headers-4.5.0-rc3-stock_4.5.0-rc3-stock-157_amd64.deb
sudo dpkg -i ../linux-image-4.5.0-rc3-stock_4.5.0-rc3-stock-157_amd64.deb
diff .config .config-4.5-rc3-doug  [COLOR="#FF0000"]<<< changes should be minimal. They are.[/COLOR]
cp .config .config-4.5-rc3-doug   [COLOR="#FF0000"]<<< Save it anyhow[/COLOR]

```
```
doug@s15:~$ uname -a
Linux s15 4.5.0-rc3-stock #157 SMP Mon Feb 8 09:00:09 PST 2016 x86_64 x86_64 x86_64 GNU/Linux
```

---

### Post by P-I H on 2016-02-14
Some differences between kernel 4.5 and 4.4

systemd-analyze 4.5
Startup finished in 8.951s (kernel) + 5.968s (userspace) = 14.920s

systemd-analyze kernel 4.4
Startup finished in 4.769s (kernel) + 7.951s (userspace) = 12.720s

Unigine Valley benchmark kernel 4.4
FPS: 9.7 Score: 407

Unigine Valley benchmark kernel 4.5 with powerplay enabled
FPS: 43.1 Score: 1803

---

### Post by Doug S on 2016-02-14
Kernel 4.5-rc4 is [available]("http://kernel.ubuntu.com/~kernel-ppa/mainline/v4.5-rc4-wily/"). Myself, I'll have to stay with -rc3 for awhile, as I 'm in the middle of some tests.

---

### Post by MikeMecanic on 2016-02-14
Perfect week here .

[LEFT][COLOR=#000000][FONT=Georgia][B][http://lkml.iu.edu/hypermail/linux/kernel/1602.1/05012.html?utm_source=anzwix](http://lkml.iu.edu/hypermail/linux/kernel/1602.1/05012.html?utm_source=anzwix)

[/B][/FONT][/COLOR][/LEFT]
```
x@g:~$ dpkg --list | grep linux-image
ii  **[COLOR=#ff0000]linux-image[/COLOR]**-4.5.0-040500rc3-generic   4.5.0-040500rc3.201602071930               amd64        Linux kernel image for version 4.5.0 on 64 bit x86 SMP
ii  **[COLOR=#ff0000]linux-image[/COLOR]**-4.5.0-040500rc4-generic   4.5.0-040500rc4.201602141731               amd64        Linux kernel image for version 4.5.0 on 64 bit x86 SMP
x@g:~$ 
```
```
x@g:~$ inxi -b
System:    Host: g Kernel: 4.5.0-040500rc4-generic x86_64 (64 bit) Desktop: Gnome 3.18.3
           Distro: Ubuntu 16.04 xenial
```

**EDIT:  Just made a fresh install of Mate daily ISO. Still using Startup Disk Creator.**

```
[LEFT]Host:xx Kernel: 4.5.0-040500rc4-generic x86_64 (64 bit)          
Desktop: MATE 1.12.1  Distro: Ubuntu 16.04 xenial[/LEFT]

```[LEFT]
Loading Sequence Proposed Enable:

[/LEFT]
```
m@xx:~$ dpkg --list| grep linux-image
ii **[COLOR=#ff0000]linux-image[/COLOR]**-4.4.0-4-generic           4.4.0-4.19                                amd64        Linux kernel image for version 4.4.0 on 64bit x86 SMP
ii **[COLOR=#ff0000]linux-image[/COLOR]**-4.4.0-5-generic           4.4.0-5.20                                amd64        Linux kernel image for version 4.4.0 on 64bit x86 SMP
ii** [COLOR=#ff0000]linux-image[/COLOR]**-4.5.0-040500rc4-generic   4.5.0-040500rc4.201602141731              amd64        Linux kernel image for version 4.5.0 on 64bit x86 SMP
ii **[COLOR=#ff0000]linux-image[/COLOR]**-extra-4.4.0-4-generic     4.4.0-4.19                                amd64        Linux kernel extra modules for version 4.4.0on 64 bit x86 SMP
ii**[COLOR=#ff0000] linux-image[/COLOR]**-extra-4.4.0-5-generic     4.4.0-5.20                                amd64        Linux kernel extra modules for version 4.4.0on 64 bit x86 SMP
ii **[COLOR=#ff0000]linux-image[/COLOR]**-generic                   4.4.0.5.4                                 amd64        Generic Linux kernel image
m@xx:

```

[LEFT]I got only one issue at the very end:  Black screen on restart after loading Proposed (341Kb patch). 

All the best,[/LEFT]

---

### Post by Doug S on 2016-02-15
O.K. now running 4.5-rc3. so far so good.
```
doug@s15:~/temp-k-git/linux$ uname -a
Linux s15 4.5.0-rc4-rjwv10 #165 SMP Mon Feb 15 07:41:21 PST 2016 x86_64 x86_64 x86_64 GNU/Linux

```

---

### Post by MikeMecanic on 2016-02-21
One day earlier this week: [http://linux.softpedia.com/blog/linus-torvalds-announces-linux-kernel-4-5-release-candidate-5-things-remain-calm-500706.shtml](http://linux.softpedia.com/blog/linus-torvalds-announces-linux-kernel-4-5-release-candidate-5-things-remain-calm-500706.shtml)

```
u@tt:~$ dpkg --list | grep linux-image
ii **[COLOR=#ff0000] linux-image[/COLOR]**-4.5.0-040500rc4-generic                   4.5.0-040500rc4.201602141731                        amd64        Linux kernel image for version 4.5.0 on 64 bit x86 SMP
ii **[COLOR=#ff0000] linux-image[/COLOR]**-4.5.0-040500rc5-generic                   4.5.0-040500rc5.201602201730                        amd64        Linux kernel image for version 4.5.0 on 64 bit x86 SMP
u@tt:~$ 

```

---

### Post by MikeMecanic on 2016-02-28
Sixteenth week without any major issues. The 4.5 cycle remains quiet and stable. The latest stable Kernel is now 4.4.3.


I Was on Ubuntu most of the week and many old bugs are now part of history. The boot sequence is among the biggest changes so that I don’t get black screen issues no more. Will do a fresh install of Ubuntu tomorrow that remains my favorite one.


Kernel 4.4.3 Stable: 201602251634
Kernel 4.5 rc6: 201602281230
[https://www.kernel.org/](https://www.kernel.org/)
[https://lkml.org/lkml/2016/2/28/207](https://lkml.org/lkml/2016/2/28/207)
RC6 PPA:[http://kernel.ubuntu.com/~kernel-ppa/mainline/v4.5-rc6-wily/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v4.5-rc6-wily/)


```
kk@u:~$ dpkg --list | grep linux-image
ii [COLOR=#ff3333]**linux-image**[/COLOR]-4.4.3-040403-generic    4.4.3-040403.201602251634    amd64 Linux kernel image for version 4.4.3 on 64 bit x86 SMP
ii [COLOR=#ff3333]**linux-image**[/COLOR]-4.5.0-040500rc5-generic 4.5.0-040500rc5.201602201730 amd64 Linux kernel image for version 4.5.0 on 64 bit x86 SMP
ii [COLOR=#ff3333]**linux-image**[/COLOR]-4.5.0-040500rc6-generic 4.5.0-040500rc6.201602281230 amd64 Linux kernel image for version 4.5.0 on 64 bit x86 SMP
k@u:~$ exit

```

Cheers,

EDIT: Ubuntu Pending ISO:20160229
A+
x@u:~$ dpkg --list |grep linux-image
ii [COLOR=#ff3333]**linux-image**[/COLOR]-4.5.0-040500rc6-generic          4.5.0-040500rc6.201602281230               amd64       Linux kernel image for version 4.5.0 on 64 bit x86 SMP
x@u:~$ exit

---

### Post by aljosa2 on 2016-02-28
Hi, with kernel '4.5.0-040500rc6-generic' I have some problems that no exist with kernel '4.4.0-8-generic':

> 
dmesg | grep Bluetooth
[    2.932907] Bluetooth: Core ver 2.21
[    2.932921] Bluetooth: HCI device and connection manager initialized
[    2.932924] Bluetooth: HCI socket layer initialized
[    2.932926] Bluetooth: L2CAP socket layer initialized
[    2.932930] Bluetooth: SCO socket layer initialized
[    2.944765] Bluetooth: HCI UART driver ver 2.3
[    2.944767] Bluetooth: HCI UART protocol H4 registered
[    2.944768] Bluetooth: HCI UART protocol BCSP registered
[    2.944768] Bluetooth: HCI UART protocol LL registered
[    2.944769] Bluetooth: HCI UART protocol ATH3K registered
[    2.944769] Bluetooth: HCI UART protocol Three-wire (H5) registered
[    2.944786] Bluetooth: HCI UART protocol Intel registered
[    2.944795] Bluetooth: HCI UART protocol BCM registered
[    2.944795] Bluetooth: HCI UART protocol QCA registered
[    2.961824] Bluetooth: hci0: Bootloader revision 0.0 build 2 week 52 2014
[    2.966835] Bluetooth: hci0: Device revision is 5
[    2.966837] Bluetooth: hci0: Secure boot is enabled
[    2.966838] Bluetooth: hci0: OTP lock is enabled
[    2.966839] Bluetooth: hci0: API lock is enabled
[    2.966840] Bluetooth: hci0: Debug lock is disabled
[    2.966841] Bluetooth: hci0: Minimum firmware build 1 week 10 2014
[    2.980288] Bluetooth: hci0: Found device firmware: intel/ibt-11-5.sfi
[    3.061757] **Bluetooth: hci0: Failed to send firmware data (-38)**
[    4.149807] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[    4.149809] Bluetooth: BNEP filters: protocol multicast
[    4.149812] Bluetooth: BNEP socket layer initialized
[    5.060725] **Bluetooth: hci0: Reading Intel version information failed (-110)**
[    5.064722] **Bluetooth: hci0 command tx timeout**
[   10.346970] Bluetooth: hci0: Bootloader revision 0.0 build 2 week 52 2014
[   10.351991] Bluetooth: hci0: Device revision is 5
[   10.351993] Bluetooth: hci0: Secure boot is enabled
[   10.351994] Bluetooth: hci0: OTP lock is enabled
[   10.351995] Bluetooth: hci0: API lock is enabled
[   10.351995] Bluetooth: hci0: Debug lock is disabled
[   10.351996] Bluetooth: hci0: Minimum firmware build 1 week 10 2014
[   10.352107] Bluetooth: hci0: Found device firmware: intel/ibt-11-5.sfi
[   11.716459] Bluetooth: hci0: Waiting for firmware download to complete
[   11.716968] Bluetooth: hci0: Firmware loaded in 1338431 usecs
[   11.716995] Bluetooth: hci0: Waiting for device to boot
[   11.729025] Bluetooth: hci0: Device booted in 11754 usecs
[   11.731862] Bluetooth: hci0: Found Intel DDC parameters: intel/ibt-11-5.ddc
[   11.734062] Bluetooth: hci0: Applying Intel DDC parameters completed
[   11.735058] **Bluetooth: hci0: Setting Intel event mask failed (-16)**
[   11.790704] Bluetooth: RFCOMM TTY layer initialized
[   11.790708] Bluetooth: RFCOMM socket layer initialized
[   11.790711] Bluetooth: RFCOMM ver 1.11


In my BIOS settings 'secure boot' is disabled, so

> [    2.966837] Bluetooth: hci0: Secure boot is enabled
[   10.351993] Bluetooth: hci0: Secure boot is enabled


seems quite strange to me.
By the way, in kernel '[COLOR=#000000]4.4.0-8-generic[/COLOR]' dmesg output there's nothing related to bluetooth and secure boot.

Also with booth kerrnels I have boot error: 
> [COLOR=#333333][FONT=monospace]failure writing sector 0x21c8800 to 'hd0'[/FONT][/COLOR]
[COLOR=#333333][FONT=monospace]press any key to continue...[/FONT][/COLOR]

---

### Post by Doug S on 2016-02-28
> **aljosa2 said:**
> Hi, with kernel '4.5.0-040500rc6-generic' I have some problems that no exist with kernel '4.4.0-8-generic':

In my BIOS settings 'secure boot' is disabled, so

seems quite strange to me.
By the way, in kernel '[COLOR=#000000]4.4.0-8-generic[/COLOR]' dmesg output there's nothing related to bluetooth and secure boot.

Also with booth kernels I have boot error:Are your issues new with -rc6 or you just never tried -rc1 through -rc5?

---

### Post by Doug S on 2016-02-28
> **MikeMecanic said:**
> Sixteenth week without any major issues.I couldn't disagree more strenuously. I have never seen anything like the kernel 4.4 cycle. There were issues in the 4.3 cycle also. Yes, 4.5 has been quiet so far.

---

### Post by aljosa2 on 2016-02-28
Hi Doug S, thank you for your reply:
I have already tried only kernel -rc5 and I would say that I am in a quite complicated situation:

***Multiple Issues with Ubuntu 16.04 on Lenovo Y700-17ISK notebook***
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1547934/comments/6](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1547934/comments/6)

---

### Post by MikeMecanic on 2016-03-01
Got an issue with Systemd last night after the 10 PM (ET) or the 12:30 AM updates(proposed enable):  systemd-analyze was showing 3 minutes 10 seconds with a messages saying that the bootup process is not finish yet, try later for 3 minutes.


Possible causes: 
1- Proposed
2- Boot Manager from USC(first time I use this app)
This app is not working anymore and is the one I&#8217;m using to gain 2-3 seconds on startup:  BUM
[LEFT][COLOR=#000000][FONT=Calibri]s[/FONT][/COLOR][COLOR=#000000][FONT=Calibri]udo apt-get install bum[/FONT][/COLOR][COLOR=#000000] 
[FONT=Calibri]gksudo bum[/FONT][/COLOR][/LEFT]
3-Kernel 4.5-rc6 but it works fine today
4-  Ubuntu Pending ISO file (not tested): 20160229
5- Me that went too far...

Re-enabling all most everything and loading Kernel 4.4.0.8 didn&#8217;t do nothing.  


Made a fresh install with another ISO, **did not enable Proposed**, did not run Boot Manager,disable a few things in Startup Applications, made a normal post-installation sequence and I&#8217;m still running Kernel 4.5-rc6 alone with no bug,  Systemd is showing normal results: 10-15 seconds.

---

### Post by MikeMecanic on 2016-03-02
Enable Proposed this morning and nothing abnormal.

---

### Post by MikeMecanic on 2016-03-06
[rc7 Announcement]("http://lkml.iu.edu/hypermail/linux/kernel/1603.0/05078.html?utm_source=anzwix")
                      
 Release Candidate 7 will be the last? 
_The good news this week is that live streaming works now in VLC ( .m3u8). _   
 
 **Removing Kernel 4.4.0.11**
 ```
 sudo apt-get purge linux-headers-4.4.0-11 linux-headers-4.4.0-11-generic linux-image-4.4.0-11-generic
``` 
 **Removing Kernel 4.5-rc6**
 ```
sudo apt-get purge linux-headers-4.5.0-040500rc6 linux-headers-4.5.0-040500rc6-generic linux-image-4.5.0-040500rc6-generic
``` 
** Remaining Kernel**
 ```
k@u:~$ dpkg --list | grep linux-image
ii  [COLOR=#ff3333]**linux-image**[/COLOR]-4.5.0-040500rc7-generic  4.5.0-040500rc7.201603061830  amd64    Linux kernel image for version 4.5.0 on 64 bit x86 SMP
k@u:~$ date
Sun Mar  6 20:11:12 EST 2016

``` 
 **Removing Thermald 1.5-2**
```
sudo apt-get purge thermald
``` 
 
 [SIZE=4][COLOR=#ff3333]**There is a bug on startup with Kernel 4.4.0.11 (from Proposed) and the problem can not be reported (Apport).  Was booting default into rc-6 with an error message each time.**[/COLOR][/SIZE]

---

### Post by MikeMecanic on 2016-03-06
A long lasting bug out of Proposed.  I have to pass by Synaptic to upgrade to 20160112-1 on all fresh install since January.
 
 
 ```
k@u:~$ sudo apt list --upgradable -a
 Listing... Done
 [COLOR=#007826]**usb-modeswitch-data**[/COLOR]/xenial-proposed,xenial-proposed 20160112-1 all [upgradable from: 20151101-1]
 [COLOR=#007826]**usb-modeswitch**[/COLOR]-data/xenial,xenial,now 20151101-1 all [installed,upgradable to: 20160112-1]
k@u:~$

```

Edit:  Will do another fresh install to reproduce the bug.  Kylin takes more time to tweak,  Don't see nothing in the log.  Be back in 30 minutes with the bug.

Edit 2:  I'm not able to reproduce the bug.  But I remember that error message was mentioning something about Kernel oops.  Its about the only thing I remember and it was after removing 4.4.0.10.  Will keep that ways until tomorrow and see if it comes back.  
So I have rc-6 and 4.4.0.11 just like it was when I was having the error.  

Take care,

---

### Post by Doug S on 2016-03-09
Just catching up. I missed rc6 as I had to keep rc5 as a baseline for some tests I was doing.
I have converted my test server computer from 14.04 to 16.04, and so now can compile the kernel without doing this first:```
scripts/config --disable CC_STACKPROTECTOR_STRONG
```Anyway, I have been running a few versions of rc7 for less than a day so far, without issues.

---

### Post by MikeMecanic on 2016-03-15
[Testing Kermel 4.5]("https://lkml.org/lkml/2016/3/14/50")
 
 A peak was reached, *Release Candidate Seven* was simply the best one and Ubuntu runs very well now upfront.   

 Many improvements were made in the last two weeks... *Chapeau!*
 
 ```

 
 xx@u:~$ **dpkg --list | grep linux-image**
 ii  [COLOR=#ff3333]**linux-image**[/COLOR]-4.5.0-040500-generic    4.5.0-040500.201603140130   amd64  Linux kernel image for version 4.5.0 on 64 bit x86 SMP
 xx@u:~$ **df -h | grep ^/dev/sda1**
 [COLOR=#ff3333]**/dev/sda1**[/COLOR]    236M   57M  167M  26% /boot
 xx@u:~$ **dpkg -l|grep firmware**
 ii  intel-microcode    3.20151106.1     amd64   Processor microcode [COLOR=#ff3333]**firmware **[/COLOR]for Intel CPUs
 ii  linux-[COLOR=#ff3333]**firmware**[/COLOR]     1.156       all          Firmware for Linux kernel drivers
  
 

```  
 
 Regards,
 
 
Mike

---

