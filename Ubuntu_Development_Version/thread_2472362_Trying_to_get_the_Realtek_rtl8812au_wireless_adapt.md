---
title: "Trying to get the Realtek rtl8812au wireless adapter to work in Ubuntu 22.04"
date: 2022-02-25
forum: Ubuntu Development Version
---

### Post by Joe_Linux on 2022-02-25
I am trying to get the Realtek rtl8812au wireless adapter to work in Ubuntu 22.04, I tried following this post.
```
https://tutorialforlinux.com/2022/01/11/realtek-rtl8812au-driver-ubuntu-22-04-installation-step-by-step/
```
This is my result 
```
ubuntu@ubuntu:~/Desktop$ sudo apt-get update
Ign:1 cdrom://Ubuntu 22.04 LTS _Jammy Jellyfish_ - Alpha amd64 (20220202) jammy InRelease
Hit:2 cdrom://Ubuntu 22.04 LTS _Jammy Jellyfish_ - Alpha amd64 (20220202) jammy Release
Hit:4 http://archive.ubuntu.com/ubuntu jammy InRelease                         
Hit:5 http://security.ubuntu.com/ubuntu jammy-security InRelease               
Hit:6 http://archive.ubuntu.com/ubuntu jammy-updates InRelease
Reading package lists... Done
ubuntu@ubuntu:~/Desktop$ sudo apt remove rtl8812au-dkms
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
E: Unable to locate package rtl8812au-dkms
```

Also FYI the dongle does show up in the lsusb command 
```
ubuntu@ubuntu:~/Desktop$ lsusb
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 011: ID 0bda:0811 Realtek Semiconductor Corp. Realtek 8812AU/8821AU 802.11ac WLAN Adapter [USB Wireless Dual-Band Adapter 2.4/5Ghz]
Bus 001 Device 007: ID 1f75:0917 Innostor Technology Corporation IS917 Mass storage
Bus 001 Device 006: ID 07b8:3071 AboCom Systems Inc 802.11n/b/g Mini Wireless LAN USB2.0 Adapter
Bus 001 Device 004: ID 05e3:0610 Genesys Logic, Inc. Hub
Bus 001 Device 002: ID 05e3:0610 Genesys Logic, Inc. Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 002: ID 0e8f:0022 GreenAsia Inc. multimedia keyboard controller
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 046d:c05a Logitech, Inc. M90/M100 Optical Mouse
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
ubuntu@ubuntu:~/Desktop$ 





```

BTW the dongle works in Ubuntu 18.04 
```
https://askubuntu.com/questions/1185952/need-rtl8814au-driver-for-kernel-5-3-on-ubuntu-19-10
```
```
oe@joe-GA-78LMT-USB3:~$ sudo apt install git dkms
[sudo] password for joe:
Reading package lists... Done
Building dependency tree
Reading state information... Done
dkms is already the newest version (2.3-3ubuntu9.7).
dkms set to manually installed.
git is already the newest version (1:2.17.1-1ubuntu0.6).
The following packages were automatically installed and are no longer required:
libllvm7 libllvm8
Use 'sudo apt autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 6 not upgraded.
joe@joe-GA-78LMT-USB3:~$ git clone https://github.com/aircrack-ng/rtl8812au.git
Cloning into 'rtl8812au'...
remote: Enumerating objects: 10205, done.
remote: Total 10205 (delta 0), reused 0 (delta 0), pack-reused 10205
Receiving objects: 100% (10205/10205), 69.58 MiB | 2.02 MiB/s, done.
Resolving deltas: 100% (7122/7122), done.
joe@joe-GA-78LMT-USB3:~$ cd rtl8812au
joe@joe-GA-78LMT-USB3:~/rtl8812au$ sudo ./dkms-install.sh
About to run dkms install steps...
Creating symlink /var/lib/dkms/rtl8812au/5.6.4.2/source ->
/usr/src/rtl8812au-5.6.4.2
DKMS: add completed.
Kernel preparation unnecessary for this kernel. Skipping...
Building module:
cleaning build area...
'make' -j8 KVER=5.3.0-46-generic KSRC=/lib/modules/5.3.0-46-generic/build.............
cleaning build area...
DKMS: build completed.
88XXau:
Running module version sanity check.
- Original module
- This kernel never originally had a module by this name
- Installation
- Installing to /lib/modules/5.3.0-46-generic/updates/dkms/
depmod....
DKMS: install completed.
Finished running dkms install steps.
joe@joe-GA-78LMT-USB3:~/rtl8812au$
```

---

### Post by mastablasta on 2022-02-25
look like it successfully installed. is the dongle not working?

also does anything show up in additional drivers application?  Realtek are sometimes included in kernel and other times they are available in additional drivers.  

for DKMS patching you need to have secure boot off i believe.

also you might also be able to install via PPA. for example: [https://launchpad.net/~mrazavi/+archive/ubuntu/rtl8812au-5.9.3.2](https://launchpad.net/~mrazavi/+archive/ubuntu/rtl8812au-5.9.3.2)

---

### Post by Joe_Linux on 2022-02-26
> **mastablasta said:**
> look like it successfully installed. is the dongle not working? No it is not working

also does anything show up in additional drivers application?  Realtek are sometimes included in kernel and other times they are available in additional drivers. no
for DKMS patching you need to have secure boot off i believe.

also you might also be able to install via PPA. for example: [https://launchpad.net/~mrazavi/+archive/ubuntu/rtl8812au-5.9.3.2](https://launchpad.net/~mrazavi/+archive/ubuntu/rtl8812au-5.9.3.2) Tried it the driver it  was for 20.04 not 22.04 it did not work. 

```
ubuntu@ubuntu:~/Desktop$ sudo add-apt-repository ppa:mrazavi/rtl8812au-5.9.3.2
Repository: 'deb [http://ppa.launchpad.net/mrazavi/rtl8812au-5.9.3.2/ubuntu/](http://ppa.launchpad.net/mrazavi/rtl8812au-5.9.3.2/ubuntu/) jammy main'
Description:
Based on [https://github.com/admirito/rtl8812au-5.9.3.2/tree/debian](https://github.com/admirito/rtl8812au-5.9.3.2/tree/debian)

I created this PPA for easier installation of Realtek 8812AU driver for my Tenda U12 AC1300 Wireless USB Adapter on Ubuntu 20.04 Focal Fossa. Although it is probably compatible with the following devices, too (you can use lsusb command and compare the sixth column xxxx:xxxx digits with the following xxxx:xxxx IDs to check if your device is actually compatiable with this driver or not):

* 0409:0408 NEC
* 0411:025D Buffalo - WI-U3-866D
* 04BB:0952 I-O DATA - Edimax
* 050D:1106 Belkin - Sercomm
* 050D:1109 Belkin - SerComm F9L1109
* 0586:3426 ZyXEL
* 0789:016E Logitec - Edimax
* 07B8:8812 Abocom - Abocom
* 0846:9051 Netgear A6200 v2
* 0B05:17D2 ASUS - Edimax
* 0BDA:8812 KOOTEK
* 0BDA:881A Unex DAUK-W8812
* 0DF6:0074 Sitecom - Edimax
* 0E66:0022 HAWKING - Edimax
* 1058:0632 WD - Cybertan
* 13B1:003F Linksys - WUSB6300
* 148F:9097 Amped Wireless - ACA1
* 1740:0100 EnGenius - EnGenius
* 2001:330E D-Link - ALPHA
* 2001:3313 D-Link - ALPHA
* 2001:3315 D-Link - Cameo
* 2001:3316 D-Link - Cameo
* 2019:AB30 Planex - Abocom
* 20F4:805B TRENDnet - Cameo
* 2357:0101 TP-Link - Archer T4U
* 2357:0103 TP-Link - Archer T4UH
* 2357:010D TP-Link - Archer T4U AC1300
* 2357:010E TP-Link - Archer T4UH AC1300
* 2357:010F TP-Link - T4UHP
* 2357:0122 TP-Link - Archer T4UHP(US) v1 AC1300
* 2604:0012 Tenda - U12
* 7392:A812 Edimax - EW-7811UTC
* 7392:A822 Edimax - Edimax

To install the driver on Ubuntu 20.04, use the following commands. I have only tested it with linux kernel 5.13.0 (with linux-generic-hwe-20.04-edge package), but it may work on other kernels as well:

sudo add-apt-repository ppa:mrazavi/rtl8812au-5.9.3.2
sudo apt update
sudo apt install rtl8812au-dkms
More info: [https://launchpad.net/~mrazavi/+archive/ubuntu/rtl8812au-5.9.3.2](https://launchpad.net/~mrazavi/+archive/ubuntu/rtl8812au-5.9.3.2)
Adding repository.
Press [ENTER] to continue or Ctrl-c to cancel.
Adding deb entry to /etc/apt/sources.list.d/mrazavi-ubuntu-rtl8812au-5_9_3_2-jammy.list
Adding disabled deb-src entry to /etc/apt/sources.list.d/mrazavi-ubuntu-rtl8812au-5_9_3_2-jammy.list
Adding key to /etc/apt/trusted.gpg.d/mrazavi-ubuntu-rtl8812au-5_9_3_2.gpg with fingerprint CF38C8D889ADEAC0265E36983C453D244AA450E0
Ign:1 cdrom://Ubuntu 22.04 LTS _Jammy Jellyfish_ - Alpha amd64 (20220202) jammy InRelease
Hit:2 cdrom://Ubuntu 22.04 LTS _Jammy Jellyfish_ - Alpha amd64 (20220202) jammy Release
Hit:4 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) jammy InRelease                 
Ign:5 [http://ppa.launchpad.net/mrazavi/rtl8812au-5.9.3.2/ubuntu](http://ppa.launchpad.net/mrazavi/rtl8812au-5.9.3.2/ubuntu) jammy InRelease
Hit:6 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) jammy-updates InRelease                 
Hit:7 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jammy-security InRelease               
Err:8 [http://ppa.launchpad.net/mrazavi/rtl8812au-5.9.3.2/ubuntu](http://ppa.launchpad.net/mrazavi/rtl8812au-5.9.3.2/ubuntu) jammy Release  
  404  Not Found [IP: 2001:67c:1560:8008::19 80]
Reading package lists... Done
E: The repository 'http://ppa.launchpad.net/mrazavi/rtl8812au-5.9.3.2/ubuntu jammy Release' does not have a Release file.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
N: See apt-secure(8) manpage for repository creation and user configuration details.
ubuntu@ubuntu:~/Desktop$ sudo apt-get update
Ign:1 cdrom://Ubuntu 22.04 LTS _Jammy Jellyfish_ - Alpha amd64 (20220202) jammy InRelease
Hit:2 cdrom://Ubuntu 22.04 LTS _Jammy Jellyfish_ - Alpha amd64 (20220202) jammy Release
Hit:4 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) jammy InRelease                         
Hit:5 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jammy-security InRelease               
Ign:6 [http://ppa.launchpad.net/mrazavi/rtl8812au-5.9.3.2/ubuntu](http://ppa.launchpad.net/mrazavi/rtl8812au-5.9.3.2/ubuntu) jammy InRelease
Hit:7 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) jammy-updates InRelease
Err:8 [http://ppa.launchpad.net/mrazavi/rtl8812au-5.9.3.2/ubuntu](http://ppa.launchpad.net/mrazavi/rtl8812au-5.9.3.2/ubuntu) jammy Release
  404  Not Found [IP: 2001:67c:1560:8008::19 80]
Reading package lists... Done
E: The repository 'http://ppa.launchpad.net/mrazavi/rtl8812au-5.9.3.2/ubuntu jammy Release' does not have a Release file.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
N: See apt-secure(8) manpage for repository creation and user configuration details.
ubuntu@ubuntu:~/Desktop$ 
```
Thank you for your suggestions
```
ubuntu@ubuntu:~/Desktop$ lsmod
Module                  Size  Used by
ccm                    20480  6
rt2800usb              32768  0
rt2x00usb              24576  1 rt2800usb
rt2800lib             143360  1 rt2800usb
rt2x00lib              73728  3 rt2800usb,rt2x00usb,rt2800lib
mac80211             1228800  3 rt2x00lib,rt2x00usb,rt2800lib
cfg80211              962560  2 rt2x00lib,mac80211
libarc4                16384  1 mac80211
tls                   106496  0
ntfs3                 274432  0
snd_seq_dummy          16384  0
snd_hrtimer            16384  1
zfs                  4399104  6
zunicode              348160  1 zfs
zzstd                 487424  1 zfs
zlua                  155648  1 zfs
zavl                   20480  1 zfs
icp                   319488  1 zfs
zcommon               102400  2 zfs,icp
znvpair                94208  2 zfs,zcommon
spl                   122880  6 zfs,icp,zzstd,znvpair,zcommon,zavl
edac_mce_amd           36864  0
snd_hda_codec_via      20480  1
ccp                   102400  0
snd_hda_codec_generic   102400  1 snd_hda_codec_via
snd_hda_codec_hdmi     73728  1
ledtrig_audio          16384  1 snd_hda_codec_generic
snd_hda_intel          53248  5
kvm                  1003520  0
snd_intel_dspcfg       28672  1 snd_hda_intel
snd_intel_sdw_acpi     20480  1 snd_intel_dspcfg
snd_hda_codec         155648  4 snd_hda_codec_generic,snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec_via
input_leds             16384  0
joydev                 32768  0
snd_hda_core          110592  5 snd_hda_codec_generic,snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec,snd_hda_codec_via
snd_hwdep              16384  1 snd_hda_codec
snd_pcm               139264  4 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec,snd_hda_core
snd_seq_midi           20480  0
snd_seq_midi_event     16384  1 snd_seq_midi
snd_rawmidi            49152  1 snd_seq_midi
snd_seq                73728  9 snd_seq_midi,snd_seq_midi_event,snd_seq_dummy
snd_seq_device         16384  3 snd_seq,snd_seq_midi,snd_rawmidi
snd_timer              40960  3 snd_seq,snd_hrtimer,snd_pcm
snd                   102400  23 snd_hda_codec_generic,snd_seq,snd_seq_device,snd_hda_codec_hdmi,snd_hwdep,snd_hda_intel,snd_hda_codec,snd_timer,snd_hda_codec_via,snd_pcm,snd_rawmidi
soundcore              16384  1 snd
k10temp                16384  0
fam15h_power           16384  0
mac_hid                16384  0
wmi_bmof               16384  0
serio_raw              20480  0
sch_fq_codel           20480  6
ipmi_devintf           20480  0
ipmi_msghandler       122880  1 ipmi_devintf
msr                    16384  0
parport_pc             49152  1
ppdev                  24576  0
lp                     28672  0
parport                65536  3 parport_pc,lp,ppdev
ip_tables              32768  0
x_tables               53248  1 ip_tables
autofs4                49152  2
overlay               147456  1
isofs                  53248  1
nls_iso8859_1          16384  1
dm_mirror              24576  0
dm_region_hash         24576  1 dm_mirror
dm_log                 20480  2 dm_region_hash,dm_mirror
uas                    28672  0
usb_storage            77824  5 uas
nouveau              2269184  14
mxm_wmi                16384  1 nouveau
i2c_algo_bit           16384  1 nouveau
drm_ttm_helper         16384  1 nouveau
ttm                    86016  2 drm_ttm_helper,nouveau
drm_kms_helper        307200  1 nouveau
syscopyarea            16384  1 drm_kms_helper
sysfillrect            20480  1 drm_kms_helper
crct10dif_pclmul       16384  1
sysimgblt              16384  1 drm_kms_helper
fb_sys_fops            16384  1 drm_kms_helper
crc32_pclmul           16384  0
cec                    61440  1 drm_kms_helper
ghash_clmulni_intel    16384  0
aesni_intel           376832  4
rc_core                65536  1 cec
crypto_simd            16384  1 aesni_intel
cryptd                 24576  2 crypto_simd,ghash_clmulni_intel
drm                   606208  10 drm_kms_helper,drm_ttm_helper,ttm,nouveau
pata_acpi              16384  0
video                  53248  1 nouveau
pata_atiixp            16384  0
i2c_piix4              28672  0
ahci                   45056  1
r8169                 102400  0
wmi                    32768  3 wmi_bmof,mxm_wmi,nouveau
libahci                45056  1 ahci
realtek                32768  1
hid_generic            16384  0
usbhid                 65536  0
hid                   147456  2 usbhid,hid_generic
ubuntu@ubuntu:~/Desktop$
```
Did not see the driver again thanks learning things here

---

### Post by jeremy31 on 2022-02-26
Moved to Ubuntu Dev Version as 22.04 hasn't been released yet
Post results from terminal for ```
cat /proc/cmdline; mokutil --sb-state
```

Why are you using the 5.3 kernel with 22.04, it should be using the 5.15 kernel

---

### Post by Joe_Linux on 2022-02-27
```
buntu@ubuntu:~/Desktop$ cat /proc/cmdline; mokutil --sb-state
BOOT_IMAGE=(hd0,msdos4,gpt1)/casper/vmlinuz boot=casper quiet splash fsck.mode=skip persistent --
EFI variables are not supported on this system
ubuntu@ubuntu:~/Desktop$
```

---

### Post by jeremy31 on 2022-02-27
After a reboot, is the rtl8812au folder still there?  I don't think dkms can be used with a persistent install as the kernel can't really be changed

---

### Post by Joe_Linux on 2022-02-28
jeremy31
Are you aware of a chip set (802.11ac wireless usb dongle) that works out of the box with Ubuntu 22.04 ?
Thank you

---

### Post by jeremy31 on 2022-02-28
Netgear A6210 is one of them, has a Mediatek MT7612U chipset

---

### Post by Joe_Linux on 2022-02-28
Thank you

---

### Post by Joe_Linux on 2022-03-07
jeremy31 
Do you think this would work if 22.04 was installed on a usb ssd ? [https://tutorialforlinux.com/2022/01/11/realtek-rtl8812au-driver-ubuntu-22-04-installation-step-by-step/](https://tutorialforlinux.com/2022/01/11/realtek-rtl8812au-driver-ubuntu-22-04-installation-step-by-step/)

---

### Post by SeijiSensei on 2022-03-07
I built the driver from aircrack-ng, and it is working flawlessly.

[https://github.com/aircrack-ng/rtl8812au](https://github.com/aircrack-ng/rtl8812au)

Installed git, build-essential, and dkms.  Then I cloned the archive with git then ran "make dkms_install" as I recall.

---

### Post by Joe_Linux on 2022-03-11
First thank you to everyone who posted to help me in this thread. 
```
buntu@ubuntu:~/Desktop$ sudo apt install git build-essential libelf-dev linux-headers-`uname -r` debhelper dpkg-dev dkms bc
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
build-essential is already the newest version (12.9ubuntu2).
dkms is already the newest version (2.8.7-2).
dpkg-dev is already the newest version (1.21.1ubuntu1).
dpkg-dev set to manually installed.
bc is already the newest version (1.07.1-3).
bc set to manually installed.
git is already the newest version (1:2.34.1-1ubuntu1).
linux-headers-5.15.0-18-generic is already the newest version (5.15.0-18.18).
linux-headers-5.15.0-18-generic set to manually installed.
The following additional packages will be installed:
  autoconf automake autopoint autotools-dev debugedit dh-autoreconf
  dh-strip-nondeterminism dwz gettext intltool-debian libarchive-cpio-perl
  libarchive-zip-perl libdebhelper-perl libfile-stripnondeterminism-perl
  libltdl-dev libmail-sendmail-perl libsigsegv2 libsub-override-perl
  libsys-hostname-long-perl libtool m4 po-debconf zlib1g-dev
Suggested packages:
  autoconf-archive gnu-standards autoconf-doc dh-make gettext-doc
  libasprintf-dev libgettextpo-dev libtool-doc gfortran | fortran95-compiler
  gcj-jdk m4-doc libmail-box-perl
The following NEW packages will be installed:
  autoconf automake autopoint autotools-dev debhelper debugedit dh-autoreconf
  dh-strip-nondeterminism dwz gettext intltool-debian libarchive-cpio-perl
  libarchive-zip-perl libdebhelper-perl libelf-dev
  libfile-stripnondeterminism-perl libltdl-dev libmail-sendmail-perl
  libsigsegv2 libsub-override-perl libsys-hostname-long-perl libtool m4
  po-debconf zlib1g-dev
0 upgraded, 25 newly installed, 0 to remove and 341 not upgraded.
Need to get 4543 kB of archives.
After this operation, 14.1 MB of additional disk space will be used.
Do you want to continue? [Y/n] y
Get:1 http://archive.ubuntu.com/ubuntu jammy/main amd64 libsigsegv2 amd64 2.13-1ubuntu2 [14.6 kB]
Get:2 http://archive.ubuntu.com/ubuntu jammy/main amd64 m4 amd64 1.4.18-5ubuntu1 [199 kB]
Get:3 http://archive.ubuntu.com/ubuntu jammy/main amd64 autoconf all 2.71-2 [338 kB]
Get:4 http://archive.ubuntu.com/ubuntu jammy/main amd64 autotools-dev all 20220109.1 [44.9 kB]
Get:5 http://archive.ubuntu.com/ubuntu jammy/main amd64 automake all 1:1.16.5-1.1ubuntu1 [558 kB]
Get:6 http://archive.ubuntu.com/ubuntu jammy/main amd64 autopoint all 0.21-4ubuntu3 [422 kB]
Get:7 http://archive.ubuntu.com/ubuntu jammy/main amd64 libdebhelper-perl all 13.6ubuntu1 [67.2 kB]
Get:8 http://archive.ubuntu.com/ubuntu jammy/main amd64 libtool all 2.4.6-15build1 [164 kB]
Get:9 http://archive.ubuntu.com/ubuntu jammy/main amd64 dh-autoreconf all 20 [16.1 kB]
Get:10 http://archive.ubuntu.com/ubuntu jammy/main amd64 libarchive-zip-perl all 1.68-1 [90.2 kB]
Get:11 http://archive.ubuntu.com/ubuntu jammy/main amd64 libsub-override-perl all 0.09-2 [9532 B]
Get:12 http://archive.ubuntu.com/ubuntu jammy/main amd64 libfile-stripnondeterminism-perl all 1.13.0-1 [18.1 kB]
Get:13 http://archive.ubuntu.com/ubuntu jammy/main amd64 dh-strip-nondeterminism all 1.13.0-1 [5344 B]
Get:14 http://archive.ubuntu.com/ubuntu jammy/main amd64 debugedit amd64 1:5.0-4 [47.1 kB]
Get:15 http://archive.ubuntu.com/ubuntu jammy/main amd64 dwz amd64 0.14-1build1 [104 kB]
Get:16 http://archive.ubuntu.com/ubuntu jammy/main amd64 gettext amd64 0.21-4ubuntu3 [824 kB]
Get:17 http://archive.ubuntu.com/ubuntu jammy/main amd64 intltool-debian all 0.35.0+20060710.5 [24.9 kB]
Get:18 http://archive.ubuntu.com/ubuntu jammy/main amd64 po-debconf all 1.0.21+nmu1 [233 kB]
Get:19 http://archive.ubuntu.com/ubuntu jammy/main amd64 debhelper all 13.6ubuntu1 [923 kB]
Get:20 http://archive.ubuntu.com/ubuntu jammy/main amd64 libarchive-cpio-perl all 0.10-1.1 [9928 B]
Get:21 http://archive.ubuntu.com/ubuntu jammy/main amd64 zlib1g-dev amd64 1:1.2.11.dfsg-2ubuntu7 [164 kB]
Get:22 http://archive.ubuntu.com/ubuntu jammy/main amd64 libelf-dev amd64 0.186-1 [64.4 kB]
Get:23 http://archive.ubuntu.com/ubuntu jammy/main amd64 libltdl-dev amd64 2.4.6-15build1 [167 kB]
Get:24 http://archive.ubuntu.com/ubuntu jammy/main amd64 libsys-hostname-long-perl all 1.5-2 [11.5 kB]
Get:25 http://archive.ubuntu.com/ubuntu jammy/main amd64 libmail-sendmail-perl all 0.80-1.1 [22.7 kB]
Fetched 4543 kB in 30s (153 kB/s)                                              
Selecting previously unselected package libsigsegv2:amd64.
(Reading database ... 206096 files and directories currently installed.)
Preparing to unpack .../00-libsigsegv2_2.13-1ubuntu2_amd64.deb ...
Unpacking libsigsegv2:amd64 (2.13-1ubuntu2) ...
Selecting previously unselected package m4.
Preparing to unpack .../01-m4_1.4.18-5ubuntu1_amd64.deb ...
Unpacking m4 (1.4.18-5ubuntu1) ...
Selecting previously unselected package autoconf.
Preparing to unpack .../02-autoconf_2.71-2_all.deb ...
Unpacking autoconf (2.71-2) ...
Selecting previously unselected package autotools-dev.
Preparing to unpack .../03-autotools-dev_20220109.1_all.deb ...
Unpacking autotools-dev (20220109.1) ...
Selecting previously unselected package automake.
Preparing to unpack .../04-automake_1%3a1.16.5-1.1ubuntu1_all.deb ...
Unpacking automake (1:1.16.5-1.1ubuntu1) ...
Selecting previously unselected package autopoint.
Preparing to unpack .../05-autopoint_0.21-4ubuntu3_all.deb ...
Unpacking autopoint (0.21-4ubuntu3) ...
Selecting previously unselected package libdebhelper-perl.
Preparing to unpack .../06-libdebhelper-perl_13.6ubuntu1_all.deb ...
Unpacking libdebhelper-perl (13.6ubuntu1) ...
Selecting previously unselected package libtool.
Preparing to unpack .../07-libtool_2.4.6-15build1_all.deb ...
Unpacking libtool (2.4.6-15build1) ...
Selecting previously unselected package dh-autoreconf.
Preparing to unpack .../08-dh-autoreconf_20_all.deb ...
Unpacking dh-autoreconf (20) ...
Selecting previously unselected package libarchive-zip-perl.
Preparing to unpack .../09-libarchive-zip-perl_1.68-1_all.deb ...
Unpacking libarchive-zip-perl (1.68-1) ...
Selecting previously unselected package libsub-override-perl.
Preparing to unpack .../10-libsub-override-perl_0.09-2_all.deb ...
Unpacking libsub-override-perl (0.09-2) ...
Selecting previously unselected package libfile-stripnondeterminism-perl.
Preparing to unpack .../11-libfile-stripnondeterminism-perl_1.13.0-1_all.deb ...
Unpacking libfile-stripnondeterminism-perl (1.13.0-1) ...
Selecting previously unselected package dh-strip-nondeterminism.
Preparing to unpack .../12-dh-strip-nondeterminism_1.13.0-1_all.deb ...
Unpacking dh-strip-nondeterminism (1.13.0-1) ...
Selecting previously unselected package debugedit.
Preparing to unpack .../13-debugedit_1%3a5.0-4_amd64.deb ...
Unpacking debugedit (1:5.0-4) ...
Selecting previously unselected package dwz.
Preparing to unpack .../14-dwz_0.14-1build1_amd64.deb ...
Unpacking dwz (0.14-1build1) ...
Selecting previously unselected package gettext.
Preparing to unpack .../15-gettext_0.21-4ubuntu3_amd64.deb ...
Unpacking gettext (0.21-4ubuntu3) ...
Selecting previously unselected package intltool-debian.
Preparing to unpack .../16-intltool-debian_0.35.0+20060710.5_all.deb ...
Unpacking intltool-debian (0.35.0+20060710.5) ...
Selecting previously unselected package po-debconf.
Preparing to unpack .../17-po-debconf_1.0.21+nmu1_all.deb ...
Unpacking po-debconf (1.0.21+nmu1) ...
Selecting previously unselected package debhelper.
Preparing to unpack .../18-debhelper_13.6ubuntu1_all.deb ...
Unpacking debhelper (13.6ubuntu1) ...
Selecting previously unselected package libarchive-cpio-perl.
Preparing to unpack .../19-libarchive-cpio-perl_0.10-1.1_all.deb ...
Unpacking libarchive-cpio-perl (0.10-1.1) ...
Selecting previously unselected package zlib1g-dev:amd64.
Preparing to unpack .../20-zlib1g-dev_1%3a1.2.11.dfsg-2ubuntu7_amd64.deb ...
Unpacking zlib1g-dev:amd64 (1:1.2.11.dfsg-2ubuntu7) ...
Selecting previously unselected package libelf-dev:amd64.
Preparing to unpack .../21-libelf-dev_0.186-1_amd64.deb ...
Unpacking libelf-dev:amd64 (0.186-1) ...
Selecting previously unselected package libltdl-dev:amd64.
Preparing to unpack .../22-libltdl-dev_2.4.6-15build1_amd64.deb ...
Unpacking libltdl-dev:amd64 (2.4.6-15build1) ...
Selecting previously unselected package libsys-hostname-long-perl.
Preparing to unpack .../23-libsys-hostname-long-perl_1.5-2_all.deb ...
Unpacking libsys-hostname-long-perl (1.5-2) ...
Selecting previously unselected package libmail-sendmail-perl.
Preparing to unpack .../24-libmail-sendmail-perl_0.80-1.1_all.deb ...
Unpacking libmail-sendmail-perl (0.80-1.1) ...
Setting up gettext (0.21-4ubuntu3) ...
Setting up libarchive-zip-perl (1.68-1) ...
Setting up libdebhelper-perl (13.6ubuntu1) ...
Setting up intltool-debian (0.35.0+20060710.5) ...
Setting up autotools-dev (20220109.1) ...
Setting up libsigsegv2:amd64 (2.13-1ubuntu2) ...
Setting up autopoint (0.21-4ubuntu3) ...
Setting up zlib1g-dev:amd64 (1:1.2.11.dfsg-2ubuntu7) ...
Setting up dwz (0.14-1build1) ...
Setting up libarchive-cpio-perl (0.10-1.1) ...
Setting up debugedit (1:5.0-4) ...
Setting up libsub-override-perl (0.09-2) ...
Setting up libsys-hostname-long-perl (1.5-2) ...
Setting up libfile-stripnondeterminism-perl (1.13.0-1) ...
Setting up libtool (2.4.6-15build1) ...
Setting up po-debconf (1.0.21+nmu1) ...
Setting up m4 (1.4.18-5ubuntu1) ...
Setting up libmail-sendmail-perl (0.80-1.1) ...
Setting up libelf-dev:amd64 (0.186-1) ...
Setting up autoconf (2.71-2) ...
Setting up dh-strip-nondeterminism (1.13.0-1) ...
Setting up automake (1:1.16.5-1.1ubuntu1) ...
update-alternatives: using /usr/bin/automake-1.16 to provide /usr/bin/automake (
automake) in auto mode
Setting up dh-autoreconf (20) ...
Setting up libltdl-dev:amd64 (2.4.6-15build1) ...
Setting up debhelper (13.6ubuntu1) ...
Processing triggers for install-info (6.8-4) ...
Processing triggers for libc-bin (2.35-0ubuntu1) ...
Processing triggers for man-db (2.10.1-1) ...
ubuntu@ubuntu:~/Desktop$ git clone https://github.com/aircrack-ng/rtl8812au
Cloning into 'rtl8812au'...
remote: Enumerating objects: 10643, done.
remote: Counting objects: 100% (538/538), done.
remote: Compressing objects: 100% (428/428), done.
remote: Total 10643 (delta 176), reused 434 (delta 99), pack-reused 10105
Receiving objects: 100% (10643/10643), 71.52 MiB | 1.46 MiB/s, done.
Resolving deltas: 100% (7143/7143), done.
ubuntu@ubuntu:~/Desktop$ cd rtl*
ubuntu@ubuntu:~/Desktop/rtl8812au$ sudo make dkms_install
mkdir: created directory '/usr/src/8812au-5.6.4.2_35491.20191025'
cp -r * /usr/src/8812au-5.6.4.2_35491.20191025
dkms add -m 8812au -v 5.6.4.2_35491.20191025
Creating symlink /var/lib/dkms/8812au/5.6.4.2_35491.20191025/source -> /usr/src/8812au-5.6.4.2_35491.20191025
dkms build -m 8812au -v 5.6.4.2_35491.20191025

Kernel preparation unnecessary for this kernel. Skipping...

Building module:
cleaning build area...
'make' -j8 KVER=5.15.0-18-generic KSRC=/lib/modules/5.15.0-18-generic/build........................
Signing module:
 - /var/lib/dkms/8812au/5.6.4.2_35491.20191025/5.15.0-18-generic/x86_64/module/88XXau.ko
EFI variables are not supported on this system
/sys/firmware/efi/efivars not found, aborting.
cleaning build area...
dkms install -m 8812au -v 5.6.4.2_35491.20191025

88XXau.ko:
Running module version sanity check.
 - Original module
   - No original module exists within this kernel
 - Installation
   - Installing to /lib/modules/5.15.0-18-generic/updates/dkms/

depmod.......................
dkms status -m 8812au
8812au/4.2.3: added
8812au/5.6.4.2_35491.20191025, 5.15.0-18-generic, x86_64: installed
ubuntu@ubuntu:~/Desktop/rtl8812au$ dkms status
8812au/4.2.3: added
8812au/5.6.4.2_35491.20191025, 5.15.0-18-generic, x86_64: installed
ubuntu@ubuntu:~/Desktop/rtl8812au$ 


```
Ubuntu 22.04 sees the rtl8812au adapter :)

---

### Post by Joe_Linux on 2022-03-11
BTW here is the URL I used the section that included Ubuntu instructions 
[https://miloserdov.org/?p=5507](https://miloserdov.org/?p=5507) Thank you again to all the people who posted

---

### Post by Joe_Linux on 2022-03-12
How do I mark this thread as solved ?

---

### Post by Joe_Linux on 2022-03-15
How did you know that this chipset would work ?

---

### Post by comperem on 2022-07-15
These steps from @Joe_Linux worked like a champ for Ubuntu 22.04 with EDUP wifi dongle using RTL8812au chipset.

Had to unplug then re-plug in dongle after final dkms command. Did not have to reboot.

Summary steps pulled from quoted post:
(1) sudo apt install git build-essential libelf-dev linux-headers-`uname -r` debhelper dpkg-dev dkms bc
(2) git clone [https://github.com/aircrack-ng/rtl8812au](https://github.com/aircrack-ng/rtl8812au)
(3) cd rtl8812au
(4) sudo make dkms_install

unplug usb wifi dongle then re-plug back in.

boom. led lights up right away looking for SSIDs

thank you.


> **Joe_Linux said:**
> First thank you to everyone who posted to help me in this thread. 
```
buntu@ubuntu:~/Desktop$ sudo apt install git build-essential libelf-dev linux-headers-`uname -r` debhelper dpkg-dev dkms bc
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
build-essential is already the newest version (12.9ubuntu2).
dkms is already the newest version (2.8.7-2).
dpkg-dev is already the newest version (1.21.1ubuntu1).
dpkg-dev set to manually installed.
bc is already the newest version (1.07.1-3).
bc set to manually installed.
git is already the newest version (1:2.34.1-1ubuntu1).
linux-headers-5.15.0-18-generic is already the newest version (5.15.0-18.18).
linux-headers-5.15.0-18-generic set to manually installed.
The following additional packages will be installed:
  autoconf automake autopoint autotools-dev debugedit dh-autoreconf
  dh-strip-nondeterminism dwz gettext intltool-debian libarchive-cpio-perl
  libarchive-zip-perl libdebhelper-perl libfile-stripnondeterminism-perl
  libltdl-dev libmail-sendmail-perl libsigsegv2 libsub-override-perl
  libsys-hostname-long-perl libtool m4 po-debconf zlib1g-dev
Suggested packages:
  autoconf-archive gnu-standards autoconf-doc dh-make gettext-doc
  libasprintf-dev libgettextpo-dev libtool-doc gfortran | fortran95-compiler
  gcj-jdk m4-doc libmail-box-perl
The following NEW packages will be installed:
  autoconf automake autopoint autotools-dev debhelper debugedit dh-autoreconf
  dh-strip-nondeterminism dwz gettext intltool-debian libarchive-cpio-perl
  libarchive-zip-perl libdebhelper-perl libelf-dev
  libfile-stripnondeterminism-perl libltdl-dev libmail-sendmail-perl
  libsigsegv2 libsub-override-perl libsys-hostname-long-perl libtool m4
  po-debconf zlib1g-dev
0 upgraded, 25 newly installed, 0 to remove and 341 not upgraded.
Need to get 4543 kB of archives.
After this operation, 14.1 MB of additional disk space will be used.
Do you want to continue? [Y/n] y
Get:1 http://archive.ubuntu.com/ubuntu jammy/main amd64 libsigsegv2 amd64 2.13-1ubuntu2 [14.6 kB]
Get:2 http://archive.ubuntu.com/ubuntu jammy/main amd64 m4 amd64 1.4.18-5ubuntu1 [199 kB]
Get:3 http://archive.ubuntu.com/ubuntu jammy/main amd64 autoconf all 2.71-2 [338 kB]
Get:4 http://archive.ubuntu.com/ubuntu jammy/main amd64 autotools-dev all 20220109.1 [44.9 kB]
Get:5 http://archive.ubuntu.com/ubuntu jammy/main amd64 automake all 1:1.16.5-1.1ubuntu1 [558 kB]
Get:6 http://archive.ubuntu.com/ubuntu jammy/main amd64 autopoint all 0.21-4ubuntu3 [422 kB]
Get:7 http://archive.ubuntu.com/ubuntu jammy/main amd64 libdebhelper-perl all 13.6ubuntu1 [67.2 kB]
Get:8 http://archive.ubuntu.com/ubuntu jammy/main amd64 libtool all 2.4.6-15build1 [164 kB]
Get:9 http://archive.ubuntu.com/ubuntu jammy/main amd64 dh-autoreconf all 20 [16.1 kB]
Get:10 http://archive.ubuntu.com/ubuntu jammy/main amd64 libarchive-zip-perl all 1.68-1 [90.2 kB]
Get:11 http://archive.ubuntu.com/ubuntu jammy/main amd64 libsub-override-perl all 0.09-2 [9532 B]
Get:12 http://archive.ubuntu.com/ubuntu jammy/main amd64 libfile-stripnondeterminism-perl all 1.13.0-1 [18.1 kB]
Get:13 http://archive.ubuntu.com/ubuntu jammy/main amd64 dh-strip-nondeterminism all 1.13.0-1 [5344 B]
Get:14 http://archive.ubuntu.com/ubuntu jammy/main amd64 debugedit amd64 1:5.0-4 [47.1 kB]
Get:15 http://archive.ubuntu.com/ubuntu jammy/main amd64 dwz amd64 0.14-1build1 [104 kB]
Get:16 http://archive.ubuntu.com/ubuntu jammy/main amd64 gettext amd64 0.21-4ubuntu3 [824 kB]
Get:17 http://archive.ubuntu.com/ubuntu jammy/main amd64 intltool-debian all 0.35.0+20060710.5 [24.9 kB]
Get:18 http://archive.ubuntu.com/ubuntu jammy/main amd64 po-debconf all 1.0.21+nmu1 [233 kB]
Get:19 http://archive.ubuntu.com/ubuntu jammy/main amd64 debhelper all 13.6ubuntu1 [923 kB]
Get:20 http://archive.ubuntu.com/ubuntu jammy/main amd64 libarchive-cpio-perl all 0.10-1.1 [9928 B]
Get:21 http://archive.ubuntu.com/ubuntu jammy/main amd64 zlib1g-dev amd64 1:1.2.11.dfsg-2ubuntu7 [164 kB]
Get:22 http://archive.ubuntu.com/ubuntu jammy/main amd64 libelf-dev amd64 0.186-1 [64.4 kB]
Get:23 http://archive.ubuntu.com/ubuntu jammy/main amd64 libltdl-dev amd64 2.4.6-15build1 [167 kB]
Get:24 http://archive.ubuntu.com/ubuntu jammy/main amd64 libsys-hostname-long-perl all 1.5-2 [11.5 kB]
Get:25 http://archive.ubuntu.com/ubuntu jammy/main amd64 libmail-sendmail-perl all 0.80-1.1 [22.7 kB]
Fetched 4543 kB in 30s (153 kB/s)                                              
Selecting previously unselected package libsigsegv2:amd64.
(Reading database ... 206096 files and directories currently installed.)
Preparing to unpack .../00-libsigsegv2_2.13-1ubuntu2_amd64.deb ...
Unpacking libsigsegv2:amd64 (2.13-1ubuntu2) ...
Selecting previously unselected package m4.
Preparing to unpack .../01-m4_1.4.18-5ubuntu1_amd64.deb ...
Unpacking m4 (1.4.18-5ubuntu1) ...
Selecting previously unselected package autoconf.
Preparing to unpack .../02-autoconf_2.71-2_all.deb ...
Unpacking autoconf (2.71-2) ...
Selecting previously unselected package autotools-dev.
Preparing to unpack .../03-autotools-dev_20220109.1_all.deb ...
Unpacking autotools-dev (20220109.1) ...
Selecting previously unselected package automake.
Preparing to unpack .../04-automake_1%3a1.16.5-1.1ubuntu1_all.deb ...
Unpacking automake (1:1.16.5-1.1ubuntu1) ...
Selecting previously unselected package autopoint.
Preparing to unpack .../05-autopoint_0.21-4ubuntu3_all.deb ...
Unpacking autopoint (0.21-4ubuntu3) ...
Selecting previously unselected package libdebhelper-perl.
Preparing to unpack .../06-libdebhelper-perl_13.6ubuntu1_all.deb ...
Unpacking libdebhelper-perl (13.6ubuntu1) ...
Selecting previously unselected package libtool.
Preparing to unpack .../07-libtool_2.4.6-15build1_all.deb ...
Unpacking libtool (2.4.6-15build1) ...
Selecting previously unselected package dh-autoreconf.
Preparing to unpack .../08-dh-autoreconf_20_all.deb ...
Unpacking dh-autoreconf (20) ...
Selecting previously unselected package libarchive-zip-perl.
Preparing to unpack .../09-libarchive-zip-perl_1.68-1_all.deb ...
Unpacking libarchive-zip-perl (1.68-1) ...
Selecting previously unselected package libsub-override-perl.
Preparing to unpack .../10-libsub-override-perl_0.09-2_all.deb ...
Unpacking libsub-override-perl (0.09-2) ...
Selecting previously unselected package libfile-stripnondeterminism-perl.
Preparing to unpack .../11-libfile-stripnondeterminism-perl_1.13.0-1_all.deb ...
Unpacking libfile-stripnondeterminism-perl (1.13.0-1) ...
Selecting previously unselected package dh-strip-nondeterminism.
Preparing to unpack .../12-dh-strip-nondeterminism_1.13.0-1_all.deb ...
Unpacking dh-strip-nondeterminism (1.13.0-1) ...
Selecting previously unselected package debugedit.
Preparing to unpack .../13-debugedit_1%3a5.0-4_amd64.deb ...
Unpacking debugedit (1:5.0-4) ...
Selecting previously unselected package dwz.
Preparing to unpack .../14-dwz_0.14-1build1_amd64.deb ...
Unpacking dwz (0.14-1build1) ...
Selecting previously unselected package gettext.
Preparing to unpack .../15-gettext_0.21-4ubuntu3_amd64.deb ...
Unpacking gettext (0.21-4ubuntu3) ...
Selecting previously unselected package intltool-debian.
Preparing to unpack .../16-intltool-debian_0.35.0+20060710.5_all.deb ...
Unpacking intltool-debian (0.35.0+20060710.5) ...
Selecting previously unselected package po-debconf.
Preparing to unpack .../17-po-debconf_1.0.21+nmu1_all.deb ...
Unpacking po-debconf (1.0.21+nmu1) ...
Selecting previously unselected package debhelper.
Preparing to unpack .../18-debhelper_13.6ubuntu1_all.deb ...
Unpacking debhelper (13.6ubuntu1) ...
Selecting previously unselected package libarchive-cpio-perl.
Preparing to unpack .../19-libarchive-cpio-perl_0.10-1.1_all.deb ...
Unpacking libarchive-cpio-perl (0.10-1.1) ...
Selecting previously unselected package zlib1g-dev:amd64.
Preparing to unpack .../20-zlib1g-dev_1%3a1.2.11.dfsg-2ubuntu7_amd64.deb ...
Unpacking zlib1g-dev:amd64 (1:1.2.11.dfsg-2ubuntu7) ...
Selecting previously unselected package libelf-dev:amd64.
Preparing to unpack .../21-libelf-dev_0.186-1_amd64.deb ...
Unpacking libelf-dev:amd64 (0.186-1) ...
Selecting previously unselected package libltdl-dev:amd64.
Preparing to unpack .../22-libltdl-dev_2.4.6-15build1_amd64.deb ...
Unpacking libltdl-dev:amd64 (2.4.6-15build1) ...
Selecting previously unselected package libsys-hostname-long-perl.
Preparing to unpack .../23-libsys-hostname-long-perl_1.5-2_all.deb ...
Unpacking libsys-hostname-long-perl (1.5-2) ...
Selecting previously unselected package libmail-sendmail-perl.
Preparing to unpack .../24-libmail-sendmail-perl_0.80-1.1_all.deb ...
Unpacking libmail-sendmail-perl (0.80-1.1) ...
Setting up gettext (0.21-4ubuntu3) ...
Setting up libarchive-zip-perl (1.68-1) ...
Setting up libdebhelper-perl (13.6ubuntu1) ...
Setting up intltool-debian (0.35.0+20060710.5) ...
Setting up autotools-dev (20220109.1) ...
Setting up libsigsegv2:amd64 (2.13-1ubuntu2) ...
Setting up autopoint (0.21-4ubuntu3) ...
Setting up zlib1g-dev:amd64 (1:1.2.11.dfsg-2ubuntu7) ...
Setting up dwz (0.14-1build1) ...
Setting up libarchive-cpio-perl (0.10-1.1) ...
Setting up debugedit (1:5.0-4) ...
Setting up libsub-override-perl (0.09-2) ...
Setting up libsys-hostname-long-perl (1.5-2) ...
Setting up libfile-stripnondeterminism-perl (1.13.0-1) ...
Setting up libtool (2.4.6-15build1) ...
Setting up po-debconf (1.0.21+nmu1) ...
Setting up m4 (1.4.18-5ubuntu1) ...
Setting up libmail-sendmail-perl (0.80-1.1) ...
Setting up libelf-dev:amd64 (0.186-1) ...
Setting up autoconf (2.71-2) ...
Setting up dh-strip-nondeterminism (1.13.0-1) ...
Setting up automake (1:1.16.5-1.1ubuntu1) ...
update-alternatives: using /usr/bin/automake-1.16 to provide /usr/bin/automake (
automake) in auto mode
Setting up dh-autoreconf (20) ...
Setting up libltdl-dev:amd64 (2.4.6-15build1) ...
Setting up debhelper (13.6ubuntu1) ...
Processing triggers for install-info (6.8-4) ...
Processing triggers for libc-bin (2.35-0ubuntu1) ...
Processing triggers for man-db (2.10.1-1) ...
ubuntu@ubuntu:~/Desktop$ git clone https://github.com/aircrack-ng/rtl8812au
Cloning into 'rtl8812au'...
remote: Enumerating objects: 10643, done.
remote: Counting objects: 100% (538/538), done.
remote: Compressing objects: 100% (428/428), done.
remote: Total 10643 (delta 176), reused 434 (delta 99), pack-reused 10105
Receiving objects: 100% (10643/10643), 71.52 MiB | 1.46 MiB/s, done.
Resolving deltas: 100% (7143/7143), done.
ubuntu@ubuntu:~/Desktop$ cd rtl*
ubuntu@ubuntu:~/Desktop/rtl8812au$ sudo make dkms_install
mkdir: created directory '/usr/src/8812au-5.6.4.2_35491.20191025'
cp -r * /usr/src/8812au-5.6.4.2_35491.20191025
dkms add -m 8812au -v 5.6.4.2_35491.20191025
Creating symlink /var/lib/dkms/8812au/5.6.4.2_35491.20191025/source -> /usr/src/8812au-5.6.4.2_35491.20191025
dkms build -m 8812au -v 5.6.4.2_35491.20191025

Kernel preparation unnecessary for this kernel. Skipping...

Building module:
cleaning build area...
'make' -j8 KVER=5.15.0-18-generic KSRC=/lib/modules/5.15.0-18-generic/build........................
Signing module:
 - /var/lib/dkms/8812au/5.6.4.2_35491.20191025/5.15.0-18-generic/x86_64/module/88XXau.ko
EFI variables are not supported on this system
/sys/firmware/efi/efivars not found, aborting.
cleaning build area...
dkms install -m 8812au -v 5.6.4.2_35491.20191025

88XXau.ko:
Running module version sanity check.
 - Original module
   - No original module exists within this kernel
 - Installation
   - Installing to /lib/modules/5.15.0-18-generic/updates/dkms/

depmod.......................
dkms status -m 8812au
8812au/4.2.3: added
8812au/5.6.4.2_35491.20191025, 5.15.0-18-generic, x86_64: installed
ubuntu@ubuntu:~/Desktop/rtl8812au$ dkms status
8812au/4.2.3: added
8812au/5.6.4.2_35491.20191025, 5.15.0-18-generic, x86_64: installed
ubuntu@ubuntu:~/Desktop/rtl8812au$ 


```
Ubuntu 22.04 sees the rtl8812au adapter :)

---

### Post by Joe_Linux on 2022-07-15
I am glad that this helped you.

---

### Post by morrownr on 2022-08-20
Joe,

I know this is an old thread that is marked solved but...

You asked about adapters that work with in-kernel drivers:

[https://github.com/morrownr/USB-WiFi](https://github.com/morrownr/USB-WiFi)

Select menu item 2 for a long list of usb wifi adapters that use in-kernel adapters.

If you still have the 8812au based adapter, select menu item 5 and you will find the link to the 8812au driver. It is a good driver as far as Realtek out-of kernel drivers go.

Cheers

---

### Post by Joe_Linux on 2022-08-20
Thank you

---

