---
title: "Call for testing the current daily Groovy iso files"
date: 2020-07-17
forum: Ubuntu Development Version
---

### Post by sudodus on 2020-07-17
**Edit:**

[SIZE=4]Call for testing the current daily Groovy iso files[/SIZE]

The current daily Ubuntu Groovy iso file is modified, so that it gets a valid GUID partition table (GPT).

```

$ ls -l groovy-desktop-amd64.iso
-rw------- 1 sudodus sudodus 2936969216 okt 9 21:15 groovy-desktop-amd64.iso

$ md5sum groovy-desktop-amd64.iso
00cbcce8855c00dd2231077e3a01aebc groovy-desktop-amd64.iso

$ sudo gdisk groovy-desktop-amd64.iso
[sudo] password for sudodus: 
GPT fdisk (gdisk) version 1.0.3

Partition table scan:
  MBR: protective
  BSD: not present
  APM: not present
  GPT: present

Found valid GPT with protective MBR; using GPT.

Command (? for help): q

```

After this modification a USB drive with the system **cloned** from the iso file can boot also problematic Lenovo V series computers, for example my Lenovo V130 laptop, in UEFI mode with secure boot.

I checked that it works also in a Dell Precision M4800 both in BIOS mode and UEFI mode.

There have been many modifications of the boot structure of the Groovy iso files. There may be regressions for computers, that we (the testers involved in squashing the bug) have not tested. **Please wait for the next daily Groovy iso file of *your favourite* flavour of Ubuntu, and test that it can boot correctly in the computers, where you want it to work.**

The iso file must be released at or after Oct 9 21:15 for this modification to be there.

See the long story at [Bug #1886148 - failure to boot groovy daily](https://bugs.launchpad.net/ubuntu-cdimage/+bug/1886148)

[hr][/hr]
**Original post:**

The boot structure of the Ubuntu family Groovy iso files for PC computers, the amd64 iso files, is modified in a radical way and it has caused problems to boot. The problem has been solved for most of the computers tested by us 'isotesters', but there are still problems. 

**Both older and newer computers are still failing to boot into the current daily Groovy iso files**. Those computers boot into USB drives cloned from the daily iso files uploaded during June (before the radical modification of the boot structure). It seems the developers have no more ideas. See [Bug report #1886148](https://bugs.launchpad.net/bugs/1886148).

**So in order to be ready for a situation, where some computers fail to boot from USB drives created via the standard method, cloning, I suggest that we help each other test if our computers work, and if not, if there is some workaround for the problematic computers.**

- I know (from the bug report) that there are problems with some Core2Duo computers (but I have no such computer).

- I have a fairly new computer (the newest one, that I can access for testing right now, Lenovo V130 bought in Dec 2019), that cannot boot (in UEFI mode with secure boot). This computer works with Focal iso files and with Groovy iso files from June. This computer finds the USB drive in the temporary boot menu (via F12), but skips directly into the grub menu of the internal drive, when I try from a cloned USB drive.

I found that the Lenovo V130 works as expected, when mkusb-dus creates a persistent live drive with the setting 'upefi' - using usb-pack-efi. There is a menu entry for a live-only session for people who want that, so I would say that it is a workaround.

[hr][/hr]
We can suspect that there is more than one mode of failure, different for older and newer computers. We (end users) can hardly guess what needs to be done, but we might be able to find workarounds, when cloned USB drives won't boot.

**Examples of workarounds, that I can think of (to be worthwhile testing)**,

- persistent live by [mkusb-dus](https://help.ubuntu.com/community/mkusb) with various settings (not only 'upefi')
- 'grub-n-iso' or 'isoboot' for example according to [this link](https://help.ubuntu.com/community/Installation/iso2usb/isoboot)
- [Unetbootin](https://unetbootin.github.io/)
- [Rufus](https://rufus.ie) (in Windows)
- burned DVD disk (I guess there is a DVD drive in your old computers).

Finally, new workarounds are welcome :-)

---

### Post by P-I H on 2020-07-18
The 20200717.1 version worked on this computer
```
p-i@pi-X202E:~$ inxi -Fz
System:    Kernel: 5.4.0-26-generic x86_64 bits: 64 Desktop: GNOME 3.36.3 
           Distro: Ubuntu 20.10 (Groovy Gorilla) 
Machine:   Type: Laptop System: ASUSTeK product: X202E v: 1.0 serial: <filter> 
           Mobo: ASUSTeK model: X202E v: 1.0 serial: <filter> UEFI: American Megatrends v: X202E.204 
           date: 09/19/2012 
Battery:   ID-1: BAT0 charge: 32.7 Wh condition: 32.7/36.0 Wh (91%) 
CPU:       Topology: Dual Core model: Intel Core i3-3217U bits: 64 type: MT MCP L2 cache: 3072 KiB 
           Speed: 1309 MHz min/max: 800/1800 MHz Core speeds (MHz): 1: 1532 2: 1381 3: 1372 4: 1800 
Graphics:  Device-1: Intel 3rd Gen Core processor Graphics driver: i915 v: kernel 
           Device-2: IMC Networks type: USB driver: uvcvideo 
           Display: x11 server: X.Org 1.20.8 driver: modesetting unloaded: fbdev,vesa 
           resolution: 1366x768~60Hz 
           OpenGL: renderer: Mesa DRI Intel HD Graphics 4000 (IVB GT2) v: 4.2 Mesa 20.1.2 
Audio:     Device-1: Intel 7 Series/C216 Family High Definition Audio driver: snd_hda_intel 
           Sound Server: ALSA v: k5.4.0-26-generic 
Network:   Device-1: Qualcomm Atheros AR9485 Wireless Network Adapter driver: ath9k 
           IF: wlp2s0 state: up mac: <filter> 
           Device-2: Qualcomm Atheros AR8162 Fast Ethernet driver: alx 
           IF: enp3s0 state: down mac: <filter> 
           Device-3: Lite-On Atheros Bluetooth type: USB driver: btusb 
Drives:    Local Storage: total: 111.79 GiB used: 6.87 GiB (6.1%) 
           ID-1: /dev/sda vendor: Intel model: SSDSA2CW120G3 size: 111.79 GiB 
Partition: ID-1: / size: 109.04 GiB used: 6.86 GiB (6.3%) fs: ext4 dev: /dev/sda2 
Swap:      ID-1: swap-1 type: file size: 2.00 GiB used: 0 KiB (0.0%) file: /swapfile 
Sensors:   System Temperatures: cpu: 57.0 C mobo: N/A 
           Fan Speeds (RPM): cpu: 4000 
Info:      Processes: 220 Uptime: 4m Memory: 3.73 GiB used: 761.3 MiB (19.9%) Shell: Bash inxi: 3.1.04 
p-i@pi-X202E:~$ 
```

---

### Post by guiverc on 2020-07-18
Lubuntu groovy amd64 daily (2020-07-17)
 was written to DVDR following instructions at [https://discourse.ubuntu.com/t/how-to-burn-a-dvd-on-ubuntu/14022](https://discourse.ubuntu.com/t/how-to-burn-a-dvd-on-ubuntu/14022), and it booted on both

 hp dc7700 (c2d-e6320, 5gb, nvidia quadro nvs 290)
hp dc7900 (c2d-e8400, 4gb, intel 4 series integrated i915)

 which have been failing b/c of this issue.

 During boot on dc7700 I accidentally pressed SHIFT+INS on the wrong  keyboard, which resulted in me seeing messages that i normally see  before it asks for permission to download..
"*line 49 can't open /dev/sr0: No medium found*"
before more expected messages like "*fsck:md5sums%*"

Today's thumb-drive boots normally too on both boxes :)

(*I didn't expect the thumb-drive to work, why I wrote it to DVDR & booted those first.  I've been unable to boot a daily on those boxes since 2020-07-03*)

---

### Post by sudodus on 2020-07-18
Now one of the failure modes is removed. Congratulations to the Ubuntu developers and to guiverc :KS

I tested the current daily iso files
```

#perms    	size	date      	time 	file-name
-rw-------	1,8G	2020-07-17	17:09	"lubuntu/groovy-desktop-amd64.iso"
-rw-------	2,8G	2020-07-18	08:20	"ubuntu/groovy-desktop-amd64.iso"

```

- and they work well (like the corresponding iso files of yesterday did) in my Dell Precision M4800 :-)

- but they failed with the same symptom as the corresponding iso files of yesterday in the [Lenovo V130](https://dustinweb.azureedge.net/media/494085/v130.pdf) with a generation 7 Intel i5 CPU. This computer is set to boot in UEFI mode with secure boot :-(

---

### Post by sudodus on 2020-07-18
@P-I H,

Am I understanding correctly that *all* your computers boot from USB drives cloned from the current Groovy iso files now :-)

---

### Post by P-I H on 2020-07-18
I have tested these computers with OK result. The USB boot disk is made with mkusb.
- Asus [COLOR=#000000][FONT=&quot]X202E laptop in UEFI mode [/FONT][/COLOR]
- MSI desktop with Ryzen 3 1200 and MSI  B350 Tomahawk motherboard in UEFI mode
- Gigabyte desktop with Bulldozer FX-8120 and Gigabyte GA-990FXA-UD3 motherbord in MBR/BIOS mode

I have also tested in VirtualBox on my main computer in UEFI mode with OK result.

---

### Post by Cavsfan on 2020-07-19
I was able to install Groovy in UEFI mode with a bootable USB I made on Windows 10 with Rufus last night. It was the latest available Xubuntu 20.10 ISO.

---

### Post by sudodus on 2020-07-19
> **Cavsfan said:**
> I was able to install Groovy in UEFI mode with a bootable USB I made on Windows 10 with Rufus last night. It was the latest available Xubuntu 20.10 ISO.

Another good result :-) Please tell us about the computer: Brand name and model (and other relevant specifications) :-P

---

### Post by Cavsfan on 2020-07-19
> **Cavsfan said:**
> I was able to install Groovy in UEFI mode with a bootable USB I made on Windows 10 with Rufus last night. It was the latest available Xubuntu 20.10 ISO.

> **sudodus said:**
> Another good result :-) Please tell us about the computer: Brand name and model (and other relevant specifications) :-P

I was also able to install the latest 5.8 rc5 kernel and it is running smooth.
```
cavsfan@groovy:~$ inxi -F
System:    Host: groovy Kernel: 5.8.0-050800rc5-lowlatency x86_64 bits: 64 Desktop: Xfce 4.14.2 
           Distro: Ubuntu 20.10 (Groovy Gorilla) 
Machine:   Type: Desktop System: ASUS product: All Series v: N/A serial: <superuser/root required> 
           Mobo: ASUSTeK model: Z87-K v: Rev X.0x serial: <superuser/root required> UEFI: American Megatrends v: 1103 
           date: 01/02/2014 
CPU:       Topology: Quad Core model: Intel Core i7-4770K bits: 64 type: MT MCP L2 cache: 8192 KiB 
           Speed: 3795 MHz min/max: 800/3900 MHz Core speeds (MHz): 1: 3500 2: 3499 3: 3498 4: 3499 5: 3502 6: 3502 7: 3499 
           8: 3501 
Graphics:  Device-1: NVIDIA GM200 [GeForce GTX 980 Ti] driver: nvidia v: 450.57 
           Display: x11 server: X.Org 1.20.8 driver: nvidia resolution: 3840x2160~60Hz 
           OpenGL: renderer: GeForce GTX 980 Ti/PCIe/SSE2 v: 4.6.0 NVIDIA 450.57 
Audio:     Device-1: Intel 8 Series/C220 Series High Definition Audio driver: snd_hda_intel 
           Device-2: NVIDIA GM200 High Definition Audio driver: snd_hda_intel 
           Device-3: Creative Labs CA0108/CA10300 [Sound Blaster Audigy Series] driver: snd_emu10k1 
           Sound Server: ALSA v: k5.8.0-050800rc5-lowlatency 
Network:   Device-1: Realtek RTL8111/8168/8411 PCI Express Gigabit Ethernet driver: r8169 
           IF: enp3s0 state: up speed: 1000 Mbps duplex: full mac: 74:d0:2b:9d:9c:45 
           IF-ID-1: tun0 state: unknown speed: 10 Mbps duplex: full mac: N/A 
Drives:    Local Storage: total: 5.44 TiB used: 70.98 GiB (1.3%) 
           ID-1: /dev/sda vendor: Toshiba model: DT01ACA200 size: 1.82 TiB 
           ID-2: /dev/sdb vendor: Western Digital model: WD5003ABYX-01WERA2 size: 465.76 GiB 
           ID-3: /dev/sdc vendor: Western Digital model: WDS100T2B0A-00SM50 size: 931.51 GiB 
           ID-4: /dev/sdd vendor: OCZ model: VERTEX460 size: 447.13 GiB 
           ID-5: /dev/sde type: USB vendor: Western Digital model: WD Elements 25A1 size: 1.82 TiB 
Partition: ID-1: / size: 39.12 GiB used: 11.23 GiB (28.7%) fs: ext4 dev: /dev/sdc13 
Swap:      ID-1: swap-1 type: partition size: 4.00 GiB used: 0 KiB (0.0%) dev: /dev/sdc5 
Sensors:   System Temperatures: cpu: 31.0 C mobo: 27.8 C gpu: nvidia temp: 48 C 
           Fan Speeds (RPM): cpu: 1746 fan-1: 0 fan-3: 0 fan-4: 0 fan-5: 0 gpu: nvidia fan: 50% 
Info:      Processes: 258 Uptime: 1h 28m Memory: 15.57 GiB used: 1.56 GiB (10.0%) Shell: Bash inxi: 3.1.04 



```

---

### Post by sudodus on 2020-07-20
> **sudodus said:**
> Now one of the failure modes is removed. Congratulations to the Ubuntu developers and to guiverc :KS

I tested the current daily iso files
```

#perms    	size	date      	time 	file-name
-rw-------	1,8G	2020-07-17	17:09	"lubuntu/groovy-desktop-amd64.iso"
-rw-------	2,8G	2020-07-18	08:20	"ubuntu/groovy-desktop-amd64.iso"

```

- and they work well (like the corresponding iso files of yesterday did) in my Dell Precision M4800 :-)

- but they failed with the same symptom as the corresponding iso files of yesterday in the [Lenovo V130](https://dustinweb.azureedge.net/media/494085/v130.pdf) with a generation 7 Intel i5 CPU. This computer is set to boot in UEFI mode with secure boot :-(

Today I found a new workaround for the Lenovo V130:

- I know since before that it this computer boots (in UEFI mode with secure boot) from a persistent live drive made from the same Groovy iso files made with mkusb-dus with the setting 'upefi' (using the usb-pack-efi).

- **Rufus 3.11 (in default mode) will create a drive, that boots in UEFI mode (also with secure boot in this Lenovo V130)**. But this USB drive will not boot in BIOS mode.

- Rufus 3.11 (in dd-mode) will clone and create a USB drive from these Groovy iso files that boots in most computers in UEFI and BIOS mode (but like drives cloned with other tools, it does not boot this Lenovo V130 (in UEFI mode with secure boot)).

---

### Post by guiverc on 2020-08-28
I noted yesterday [https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1892754](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1892754)
"**Unable to boot in UEFI+secure boot mode**"

so played with my sony crapbook and yep it has a secure option in settings.  it fails too

sony vaio svp112a1cw (i5-9400u, 4gb, intel haswell-ULT)

I also had a recent Ubuntu desktop groovy ISO lying around, so booted it, it's impacted too, but it was too late for me to (want to) update my ubuntu daily  ISO and thus record the failure on iso.qa.ubuntu.com, so I made mention of it on #lubuntu-devel

Turns out @sudodus had the same thought as no sooner had I  jumped into bed, my phone beeped with an update to the mentioned bug report that Sudodus had written confirmation on the lp bug report of what I'd mentioned on IRC.  :)

I suspect where bugs impact Ubuntu too, filing reports on iso.qa.ubuntu.com is a great way for them to get noticed, get more attention. 

I'm not a developer so of course haven't see the "*product*" reports that are mailed out, but I'm aware that any bug reported on iso.qa.ubuntu.com seems to be known by developers on teams so I'd recommend everyone recording testing on iso.qa.ubuntu.com too, and testing bugs on other flavors (**esp**. main Ubuntu if impacted so Canonical people see the issues).

And thanks @sudodus.   I'd looked for you on IRC (where I ~always am), plus a quick search here but failed to find this thread (I was tired), so I gave up & went to bed (*do it tomorrow..*).  

*I saw talk yesterday on #ubuntu-devel relating to server boot issues, missing.... so Canonical devs are aware of some issues (may not issue impacting us)*

---

### Post by guiverc on 2020-09-01
Thanks likely to @sudodus & quite possibly the *not-so-subtle push*..

[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1892754](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1892754) has been fixed, or at least fix committed.

For anyone interested in why, see #ubuntu-release (ie. groovy daily ISOs  were pulling in a grub signed with old archive key; made invalid with  recent boothole fixes...)  Vorlon has fixed this.

In a day or so we should have bootable ISOs for thumb-drive media, with secure boot enabled devices  :smile:

---

### Post by zebra2 on 2020-09-01
I don't know exactly what the changes to the boot processes are but I am having no problem installing anything including Windows 10 with my bios set to legacy. One thing that has changed for me with the current 20.10 ISO is I am getting a "system may not boot, no EFI found" warning at the end of the installation. I ignore the warning and my system boots just fine.  Many of the problems may be due to individual bios layout. If you are having a problem booting from USB, note that on some systems you must actually have a USB drive plugged into the USB port before your bios will recognize and allow a USB boot setting.

---

### Post by sudodus on 2020-09-01
@zebra2,

You are right, that there is no problem installing anything including Windows 10 with the bios set to legacy (alias BIOS mode alias CSM as opposite to UEFI mode). For example: I run my main computer in BIOS mode.

But I can see two problems:

- If Windows 10 was installed by the manufacturer of the computer, it is installed in UEFI mode, and users who want to keep Windows and install Ubuntu alongside it want to install in the same boot mode. It is not convenient to switch boot mode every time you want to switch between Ubuntu and Windows.

- Many people want the increased security offered by the secure boot option, and it is only available in UEFI mode.

---

### Post by zebra2 on 2020-09-02
@sudodus,
I wouldn't want to argue any of your valid points however the OP is looking for "workarounds" . What I have is exactly that.  For me it all comes down to what is primary.  Am I a Linux user who only needs Windows for a "Utility" to accomplish a couple or annual chores. Or am I a Windows user that just wants to explore the usability of Linux. 
In my case I am a full time user of Ubuntu on a few Ubuntu friendly Laptops that only needs Windows as a utility (like a garmin update). In addition, all of my  Windows installs are registered with MS and have activation built into bios so Installing Windows 10 for me is not much more difficult than installing Ubuntu. Given my minor need for Windows in the first place and the fact that Windows 10 is (even without Secure Boot) more secure than in the past I don't need the aggravation of UEFI and Secure Boot. I don't want to rant on this but I think it is laughable that MS couldn't build a secure kernel so saddled the whole planet with this UEFI  in hardware pain it the posterior. Windows 10 runs fine in NTFS, Ubuntu runs fine in EXT4, Grub runs fine in MBR, so with my limited need for Windows 10 why muddle around in that messy bog called UEFI.  Thats my workaround and I'm sticking to it until my needs get larger than 2.2T.
You have my applause for your contribution to this really complex section of the forum. I suppose Canonical and Grub will develop a fix that works properly at some point.

This whole thing reminds me of a mechanic trying to fix a customers drive-ability problem with a new car when the problem is actually encoded into the car and everything the mechanic is doing is outside of the mfd specs (workarounds). Software solution for a hardware problem. Write all the software you want to, you still have crap hardware.

---

### Post by sudodus on 2020-09-02
[QUOTE=zebra2;13983576]@sudodus,
I wouldn't want to argue any of your valid points however the OP is looking for "workarounds" . What I have is exactly that./QUOTE]

I am the OP of this thread ;-)

And I think that your workaround to use legacy mode will be useful for many people :KS

But I think we can also look for workarounds, or even better, solutions, that work also in UEFI mode with secure boot :-P

---

### Post by zebra2 on 2020-09-02
> **sudodus said:**
> 
But I think we can also look for workarounds, or even better, solutions, that work also in UEFI mode with secure boot :-P

I know you are the OP but the OP can't by default be about what is know as MS Secure Boot (signed shim).  Workaround means "not secure". I think you are right to put this in the Development section since crashing a Windows system can be a consequence of "looking",  The new user shouldn't be led into an untenable position. For an experienced Ubuntu user, reinstall of Ubuntu and in most cases Windows is no big deal. For the "many" dual booting UEFI can be a *#@?* of a mess. The "Installation and Upgrades" section is getting to be about just that.
Anyway I think discourse on this whole matter is very much needed. 
So thanks.

PS: O Yes, I forgot! If you are now in addition looking for a "solution", that would have to be a UEFI Secure Boot that doesn't have to be dependent on an MS signed shim. Right now Secure Boot isn't Ubuntu's monkey but it is becoming Ubuntu's circus.

---

### Post by sudodus on 2020-09-02
> **guiverc said:**
> Thanks likely to @sudodus & quite possibly the *not-so-subtle push*..

[Bug #1892754](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1892754) has been fixed, or at least fix committed.

For anyone interested in why, see #ubuntu-release (ie. groovy daily ISOs  were pulling in a grub signed with old archive key; made invalid with  recent boothole fixes...)  Vorlon has fixed this.

In a day or so we should have bootable ISOs for thumb-drive media, with secure boot enabled devices  :smile:

Yes, [**Bug #1892754**](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1892754) has been fixed, **USB drives with the live system *cloned* from the current daily Groovy iso files work also in UEFI mode with secure boot** in most computers, for example in my Dell Precision M4800 :-)

But **mkusb-dus** can no longer create persistent live drives from these Groovy iso files, and I have not yet found how to fix it. This also means that the workaround to boot a Lenovo V130 with secure boot no longer works :-(

In addition to cloning there is another method that also works in UEFI mode and with secure boot (for most computers),

[**mkusb-plug**](https://help.ubuntu.com/community/mkusb/plug) can make persistent live drives (as well as live-only drives with and without a data partition) :-)

So far I have only tested *Lubuntu* Groovy, but this method is a semi-cloning process, so there is a good reason to think it will work with standard Ubuntu and all Ubuntu flavours.

---

### Post by sudodus on 2020-09-08
I can report progress: There are **new compressed image files** to be extracted and cloned to USB drives for UEFI and BIOS mode, that **can boot also with secure boot in a computer updated to squash the boothole bug**.

You find these image files at [**phillw.net/isos/linux-tools/uefi-n-bios**](https://phillw.net/isos/linux-tools/uefi-n-bios/?C=M;O=D), where you also find files with the corresponding md5sums.

These compressed image files are similar to the previous ones made recently, but the boot system is made by installing Ubuntu Focal from the current daily iso files (post 20.04.1 LTS) with up to date program packages, that include secure boot shims for the relevant components. This works also with a Lenovo V130, that refuses to boot USB boot drives cloned from current daily Groovy iso files in UEFI mode.

There is still a **problem with usb-pack-efi and mkusb-dus to make persistent live drives that work with secure boot**. It may take some time until I can fix it. Until then, secure boot must be turned off for them to run. The problem is that vital parts of the old tools have an old signature in the shims and lack the fix against the boothole bug.

Fortunately for users, who want a convenient tool with a graphical user interface to make persistent live drives, **mkusb-plug is still working, where cloned drives are working** [with secure boot], that is in most computers.

I think the proposed updates of the LTS release beyond the first point release are not very adventurous, and should not cause too many hiccups. Anyway, I am interested in your opinion about that.

[hr][/hr]
- [FONT=Courier New]**mkusb_grub-boot-template-for-uefi-n-bios_fat32_4GB_use-in-wins_2020-09-07.img.xz**[/FONT]

This image is small, ~ 7.5 MB, and expands to slightly less than 4 GB in order to fit in a 4 GB USB pendrive or memory card.

When extracted, you mount the first partition, which is labeled 'ISODEVICE' and has the file system FAT32 (shown as 'vfat' by Ubuntu), and copy an Ubuntu family iso file [into this first partition 'ISODEVICE']. Rename the file to [FONT=Courier New]**ubuntu.iso**[/FONT]. 

```

$ lsblk -fm /dev/sdc
NAME   FSTYPE LABEL     UUID                                 MOUNTPOINT                 SIZE OWNER GROUP MODE
sdc                                                                                    29,1G root  disk  brw-rw----
&#9500;&#9472;sdc1 vfat   ISODEVICE 0338-85F9                            /media/sudodus/ISODEVICE   3,4G root  disk  brw-rw----
&#9500;&#9472;sdc2                                                                                    1M root  disk  brw-rw----
&#9500;&#9472;sdc3 vfat   ESP       1841-531C                                                        64M root  disk  brw-rw----
&#9492;&#9472;sdc4 ext4   usb-boot  733906cb-a2c4-47f2-8fd0-a2a0bdef765a /media/sudodus/usb-boot    128M root  disk  brw-rw----

$ ls -lh /media/sududus/ISODEVICE
total 1,8G
-rw-r--r-- 1 sudodus sudodus 1,8G sep  7 21:51 ubuntu.iso


```

I have tested iso files of 20.04.1 LTS as well as current daily Groovy, and I can boot live systems in BIOS mode as well as in UEFI mode also with secure boot [in a computer updated to squash the boothole bug].

If you have a bigger drive, you can use gparted to create new partition with the label 'casper-rw' or 'writable' and the file system ext4 and get a persistent live drive. You can also create a data partition with the file system NTFS to store data and exchange data with current versions of WIndows 10, that can manage more than one partition in USB drives. See the attached **screenshots**. (Older versions of Windows can only manage partition #1, and this is preconfigured as 'ISODEVICE' with the file system FAT32.)

- [FONT=Courier New]**dd_unb_ubuntu-20.04_15GB_2020-09-07_with-proposed.img.xz**[/FONT]

This image contains a whole installed and fully updated & upgraded Ubuntu 20.04.1 LTS system. The compressed image is 1.6 MB (1.5 MiB), smaller than the iso file because several files are removed near the end of the installation, for example language files. The language selected is US English, but you can add another language, and you can install whatever drivers and program packages, when your system is running.

When extracted, this installed Ubuntu system expands to slightly less than 16 GB in order to o fit in a 16 GB USB pendrive or memory card. If you have a bigger drive, you can use gparted to grow the root partition to use the whole drive.

[hr][/hr]
See also these links (which should soon be updated with the current compressed image files),

[help.ubuntu.com/community/Installation/UEFI-and-BIOS](https://help.ubuntu.com/community/Installation/UEFI-and-BIOS)

[BIOS/UEFI Template Image for Booting ISO Files](https://askubuntu.com/questions/1269462/bios-uefi-template-image-for-booting-iso-files/1269476)

---

### Post by sudodus on 2020-09-09
There is another step to create USB boot drives for secure boot with a fix for the boothole bug.

See this link: [mkusb version 12.6.0 is uploaded to the unstable PPA](https://ubuntuforums.org/showthread.php?t=1958073&page=51&p=13984621#post13984621)

The 'usb-pack-efi' packages are upgraded with grub versions, that contain the crucial bugfix. Now a Lenovo V130, that has been unwilling to boot Groovy iso files can boot persistent live drives made by mkusb using 'usb-pack-efi'.

---

### Post by C.S.Cameron on 2020-09-10
Testing the latest **mkusb_grub-boot-template-for-uefi-n-bios_fat32_4GB_use-in-wins_2020-09-07.img.xz** ISO boot template with today's Groovy daily. Direct booting of the ISO file works okay in BIOS mode but not in UEFI mode. I have not messed with secure boot etc as the UEFI computer is my wife's. A persistent install made with 12.5.7 also worked fine in BIOS mode but not in UEFI mode.

Edit:

On the Gigabyte Brix GB-BXi7-5775R, (UEFI), computer the error is 

initramfs unpacking failed
decoding failed

with both the loopback loop ISO install and with the dus persistent install.

---

### Post by sudodus on 2020-09-10
@C.S.Cameron,

Thanks for testing :-)

Please show more details about the failure in UEFI mode. How far did the boot reach and how did it fail? I would like to reproduce the failure mode of your wife's computer, if possible, and from there debug it.

---

### Post by sudodus on 2020-09-11
@C.S.Cameron,

I did some more testing with [FONT=Courier New]**mkusb_grub-boot-template-for-uefi-n-bios_fat32_4GB_use-in-wins_2020-09-07.img.xz**[/FONT].

Before I extracted/cloned from it to a USB drive with [FONT=Courier New]**dus**[/FONT] in Ubuntu.
Now I extracted/cloned from it to a USB drive with [FONT=Courier New]**Rufus**[/FONT] in Windows,
and copied a Xubuntu 20.04.1 LTS iso file into the first partition 'ISODEVICE' as [FONT=Courier New]**ubuntu.iso**[/FONT].

In both cases the USB drives work in BIOS mode and UEFI mode in a Dell Latitude E7240 and a Dell Precision M4800.

and with secure boot (and UEFI mode) in a Lenovo V130 and a Toshiba satellite-pro-c850-19w.

So please tell me more details of how it fails for you in UEFI mode.

---

### Post by C.S.Cameron on 2020-09-11
Sorry, I had put this as an edit to my last post:

On the Gigabyte Brix GB-BXi7-5775R, (UEFI), computer the error is

initramfs unpacking failed
decoding failed

This happens with both the Template loopback loop ISO install and with the dus persistent install. 

I will zero the USB and try the template again.
I downloaded the Groovy ISO yesterday.

---

### Post by sudodus on 2020-09-11
> **C.S.Cameron said:**
> Sorry, I had put this as an edit to my last post:

On the Gigabyte Brix GB-BXi7-5775R, (UEFI), computer the error is

initramfs unpacking failed
decoding failed

This happens with both the Template loopback loop ISO install and with the dus persistent install. 

I will zero the USB and try the template again.
I downloaded the Groovy ISO yesterday.

I have seen those complaints at boot, but it was still possible to continue booting. Did you try to continue, for example by pressing the Enter key (or maybe some other key, that is suggested)?

For these tests I stayed away from Groovy because it is haunted by other problems, and there is a debugging process going on with some fundamentally different daily iso files today (addressing the problem raised by Pete Batard (Akeo).

See [ Akeo's bug report](https://bugs.launchpad.net/ubuntu/+source/casper/+bug/1895131)

and [Bug #1886148 reported by Chris Guiver on 2020-07-03: 'failure to boot groovy daily'](https://bugs.launchpad.net/ubuntu-cdimage/+bug/1886148)

So please test an iso file of 16.04.x LTS, 18.04.x LTS or 20.04.1 LTS for these tests.

---

### Post by C.S.Cameron on 2020-09-11
I have tested  16.04.x LTS, 18.04.x LTS or 20.04.1 LTS many times with mkusb_grub-boot-template-for-uefi-n-bios_fat32_4GB_use-in-windows.img.xz. with great success.
(I thought this was a Groovy thread).
I will try these older ones with the new Template-2020-09-07 also.
Must admit I have not seen usbboot as an ext4 partition before, interesting.
 I would also be interested in knowing when Michael Hudson-Doyle's fix is ready for testing.
Thomas Schmitt's idea of standardizing OS installers is a little scary.

---

### Post by sudodus on 2020-09-11
@C.S.Cameron,

Yes it is a Groovy thread, and until a couple of days ago, this new template:

[FONT=Courier New]**mkusb_grub-boot-template-for-uefi-n-bios_fat32_4GB_use-in-wins_2020-09-07.img.xz**[/FONT]

worked for me with the current daily Groovy iso files.

But now the iso files are changing so drastically that we must wait a while until it is meaningful to test them with this template. Maybe we will need another template for things to work correctly, maybe will will need different templates for versions <= 20.04 and for >= 20.10.

---

### Post by sudodus on 2020-09-12
I must say, that I am surprised :-)

mkusb version 12.6.1 can create persistent live drives, that boot both in BIOS mode and UEFI mode, also with secure boot from the current daily Xubuntu Groovy iso file. When cloned to a USB drive, this file does not boot in BIOS mode.

See the attached screenshot.

---

### Post by sudodus on 2020-09-14
@C.S.Cameron and @everybody else interested in booting live drives made from Groovy iso files,

Today (Sept 14) I tested the current daily Xubuntu Groovy iso file with the template

[FONT=Courier New]**mkusb_grub-boot-template-for-uefi-n-bios_fat32_4GB_use-in-wins_2020-09-07.img.xz**[/FONT].

I
- extracted/cloned from it to a USB drive with [FONT=Courier New]**dus**[/FONT] in Ubuntu,
- copied the Xubuntu Groovy iso file into the first partition 'ISODEVICE' as [FONT=Courier New]**ubuntu.iso**[/FONT],
- created a partition for persistence in the unallocated drive space with gparted: file system:ext4, label:writable.

The USB drive works in BIOS mode and UEFI mode in a Dell Precision M4800.

and with secure boot (and UEFI mode) in a Lenovo V130 and a Toshiba satellite-pro-c850-19w.

[HR][/HR]
We can expect more changes of the boot system in the near future, because this Groovy iso file is still not booting in BIOS mode when cloned, but it is very promising that both mkusb and this template can make it boot in BIOS mode.

---

### Post by sudodus on 2020-10-10
[SIZE=4]Call for testing the current daily Groovy iso files[/SIZE]

The current daily Ubuntu Groovy iso file is modified, so that it gets a valid GUID partition table (GPT).

```

$ ls -l groovy-desktop-amd64.iso
-rw------- 1 sudodus sudodus 2936969216 okt 9 21:15 groovy-desktop-amd64.iso

$ md5sum groovy-desktop-amd64.iso
00cbcce8855c00dd2231077e3a01aebc groovy-desktop-amd64.iso

$ sudo gdisk groovy-desktop-amd64.iso
[sudo] password for sudodus: 
GPT fdisk (gdisk) version 1.0.3

Partition table scan:
  MBR: protective
  BSD: not present
  APM: not present
  GPT: present

Found valid GPT with protective MBR; using GPT.

Command (? for help): q

```

After this modification a USB drive with the system **cloned** from the iso file can boot also problematic Lenovo V series computers, for example my Lenovo V130 laptop, in UEFI mode with secure boot.

I checked that it works also in a Dell Precision M4800 both in BIOS mode and UEFI mode.

There have been many modifications of the boot structure of the Groovy iso files. There may be regressions for computers, that we (the testers involved in squashing the bug) have not tested. **Please wait for the next daily Groovy iso file of *your favourite* flavour of Ubuntu, and test that it can boot correctly in the computers, where you want it to work.**

The iso file must be released at or after Oct 9 21:15 for this modification to be there.

Edit 1: See the long story at [Bug #1886148 - failure to boot groovy daily](https://bugs.launchpad.net/ubuntu-cdimage/+bug/1886148)

Edit 2: More tests - here is a list of all computers tested by me with the current Ubuntu Groovy system **cloned** from the iso file. Please note that tested mode shows what is tested, and a missing mode does not indicate failure, only that it was not tested. Booting was successful in all these tests performed today, 2020-10-10.

Computer spec - tested mode
----------------------------------------
Lenovo V130 - UEFI mode secure boot
Lenovo X131e - UEFI mode
Dell Precision M4800 - BIOS & UEFI modes
Dell Latitude E7240 - BIOS & UEFI modes
HP Probook 6450b - BIOS mode
Toshiba Satellite Pro C850-19W - BIOS & UEFI modes (also with secure boot)
VirtualBox 6.1.10_Ubuntu r138449 - iso file emulating optical disk - BIOS mode

---

### Post by P-I H on 2020-10-10
Booted OK with the 20201010 ISO on this computer
```
p-i@pi-MS-7A34:~$ inxi -Fz
System:    Kernel: 5.8.0-21-generic x86_64 bits: 64 Desktop: N/A Distro: Ubuntu 20.10 (Groovy Gorilla) 
Machine:   Type: Desktop Mobo: Micro-Star model: B350 TOMAHAWK (MS-7A34) v: 1.0 serial: <filter> UEFI: American Megatrends 
           v: 1.H0 date: 05/02/2018 
CPU:       Info: Quad Core model: AMD Ryzen 3 1200 bits: 64 type: MCP L2 cache: 2048 KiB 
           Speed: 1377 MHz min/max: 1550/3600 MHz Core speeds (MHz): 1: 1378 2: 1378 3: 1378 4: 1378 
Graphics:  Device-1: NVIDIA GK106 [GeForce GTX 660] driver: nvidia v: 450.80.02 
           Display: x11 server: X.Org 1.20.8 driver: nvidia unloaded: fbdev,modesetting,nouveau,vesa 
           resolution: 1920x1080~60Hz 
           OpenGL: renderer: GeForce GTX 660/PCIe/SSE2 v: 4.6.0 NVIDIA 450.80.02 
Audio:     Device-1: C-Media CMI8788 [Oxygen HD Audio] driver: snd_virtuoso 
           Device-2: NVIDIA GK106 HDMI Audio driver: snd_hda_intel 
           Device-3: Advanced Micro Devices [AMD] Family 17h HD Audio driver: snd_hda_intel 
           Sound Server: ALSA v: k5.8.0-21-generic 
Network:   Device-1: Realtek RTL8111/8168/8411 PCI Express Gigabit Ethernet driver: r8169 
           IF: enp30s0 state: up speed: 1000 Mbps duplex: full mac: <filter> 
Drives:    Local Storage: total: 454.60 GiB used: 8.55 GiB (1.9%) 
           ID-1: /dev/sda vendor: SanDisk model: Ultra II 240GB size: 223.57 GiB 
           ID-2: /dev/sdb vendor: Samsung model: SSD 830 Series size: 119.24 GiB 
           ID-3: /dev/sdc vendor: Kingston model: SV300S37A120G size: 111.79 GiB 
Partition: ID-1: / size: 109.04 GiB used: 8.50 GiB (7.8%) fs: ext4 dev: /dev/sdc2 
Swap:      ID-1: swap-1 type: file size: 2.00 GiB used: 0 KiB (0.0%) file: /swapfile 
Sensors:   System Temperatures: cpu: 33.4 C mobo: N/A gpu: nvidia temp: 34 C 
           Fan Speeds (RPM): N/A gpu: nvidia fan: 30% 
Info:      Processes: 266 Uptime: 4m Memory: 15.65 GiB used: 1.24 GiB (7.9%) Shell: Bash inxi: 3.1.07 
p-i@pi-MS-7A34:~$ 
```

This is a triple boot system with Fedora, W10 and Ubuntu.
The boot file is stored in the EFI system partition on the Fedora disk (sda).

---

### Post by corradoventu on 2020-10-10
Boot ok on system from ISO: Ubuntu 20.10 "Groovy Gorilla" - Beta amd64 (20201009.1)
```
corrado@corrado-x2-gg-1009:~$ inxi -Fxx
System:    Host: corrado-x2-gg-1009 Kernel: 5.8.0-21-generic x86_64 bits: 64 compiler: gcc v: 10.2.0 
           Desktop: N/A wm: gnome-shell dm: GDM3 Distro: Ubuntu 20.10 (Groovy Gorilla) 
Machine:   Type: Desktop Mobo: ASRock model: H110M-G/M.2 serial: <superuser/root required> 
           UEFI: American Megatrends v: P1.10 date: 05/11/2017 
CPU:       Info: Dual Core model: Intel Core i3-7100 bits: 64 type: MT MCP arch: Kaby Lake rev: 9 
           L2 cache: 3072 KiB 
           flags: avx avx2 lm nx pae sse sse2 sse3 sse4_1 sse4_2 ssse3 vmx bogomips: 31199 
           Speed: 800 MHz min/max: 800/3900 MHz Core speeds (MHz): 1: 800 2: 800 3: 800 4: 801 
Graphics:  Device-1: Intel HD Graphics 630 vendor: ASRock driver: i915 v: kernel bus ID: 00:02.0 
           chip ID: 8086:5912 
           Display: x11 server: X.Org 1.20.8 compositor: gnome-shell driver: modesetting unloaded: fbdev,vesa 
           resolution: 1920x1080~60Hz s-dpi: 96 
           OpenGL: renderer: Mesa Intel HD Graphics 630 (KBL GT2) v: 4.6 Mesa 20.2.0 direct render: Yes 
Audio:     Device-1: Intel 100 Series/C230 Series Family HD Audio vendor: ASRock driver: snd_hda_intel 
           v: kernel bus ID: 00:1f.3 chip ID: 8086:a170 
           Device-2: Logitech QuickCam Pro 9000 type: USB driver: snd-usb-audio,uvcvideo bus ID: 1-8:4 
           chip ID: 046d:0990 
           Sound Server: ALSA v: k5.8.0-21-generic 
Network:   Device-1: Intel Ethernet I219-V vendor: ASRock driver: e1000e v: 3.2.6-k port: f040 bus ID: 00:1f.6 
           chip ID: 8086:15b8 
           IF: enp0s31f6 state: up speed: 100 Mbps duplex: full mac: 70:85:c2:44:7b:86 
Drives:    Local Storage: total: 2.05 TiB used: 6.85 GiB (0.3%) 
           ID-1: /dev/nvme0n1 vendor: Kingston model: SKC2000M8250G size: 232.89 GiB speed: 31.6 Gb/s lanes: 4 
           serial: 50026B72823D1475 
           ID-2: /dev/sda vendor: Toshiba model: DT01ACA100 size: 931.51 GiB speed: 6.0 Gb/s serial: 37PYNGAFS 
           ID-3: /dev/sdb vendor: Hitachi model: HDS721010CLA332 size: 931.51 GiB speed: 3.0 Gb/s 
           serial: JP2940J80Z3D3V 
Partition: ID-1: / size: 31.25 GiB used: 6.84 GiB (21.9%) fs: ext4 dev: /dev/nvme0n1p2 
Swap:      ID-1: swap-1 type: partition size: 8.00 GiB used: 0 KiB (0.0%) priority: -2 dev: /dev/sda2 
Sensors:   System Temperatures: cpu: 48.0 C mobo: N/A 
           Fan Speeds (RPM): N/A 
Info:      Processes: 223 Uptime: 28m Memory: 7.48 GiB used: 1.52 GiB (20.3%) Init: systemd v: 246 runlevel: 5 
           Compilers: gcc: N/A Packages: 1786 apt: 1780 snap: 6 Shell: Bash v: 5.0.17 
           running in: gnome-terminal inxi: 3.1.07 
corrado@corrado-x2-gg-1009:~$ 
```

this is a multiple boot system with other Ubuntu releases and Debian

```
corrado@corrado-x2-gg-1009:~$ sudo lsblk -o NAME,LABEL,SIZE,FSTYPE,MOUNTPOINT
[sudo] password for corrado: 
NAME        LABEL          SIZE FSTYPE   MOUNTPOINT
loop0                    217,9M squashfs /snap/gnome-3-34-1804/60
loop1                     55,3M squashfs /snap/core18/1885
loop2                     30,3M squashfs /snap/snapd/9279
loop3                     62,1M squashfs /snap/gtk-common-themes/1506
loop4                     50,7M squashfs /snap/snap-store/481
sda                      931,5G          
&#9500;&#9472;sda1                     256M vfat     
&#9500;&#9472;sda2                       8G swap     [SWAP]
&#9500;&#9472;sda3      p3-gorilla      32G ext4     
&#9500;&#9472;sda4      p4-xenial       32G ext4     
&#9500;&#9472;sda5      p5-debian       32G ext4     
&#9500;&#9472;sda6      p6-eoan-1017    32G ext4     
&#9500;&#9472;sda7      p7-focal-x      32G ext4     
&#9500;&#9472;sda8      p8-bionic       32G ext4     
&#9500;&#9472;sda9                      32G ext4     
&#9500;&#9472;sda10     dati1          256G ext4     /media/corrado/dati1
&#9500;&#9472;sda11     dati2          256G ext4     
&#9492;&#9472;sda12     dati3        187,3G ext4     
sdb                      931,5G          
&#9492;&#9472;sdb1      backup       931,5G ext4     
sr0                       1024M          
nvme0n1                  232,9G          
&#9500;&#9472;nvme0n1p1                256M vfat     /boot/efi
&#9500;&#9472;nvme0n1p2 x2-gg-1009      32G ext4     /
&#9500;&#9472;nvme0n1p3 x3-gg-0930      32G ext4     
&#9500;&#9472;nvme0n1p4 x4-focal        32G ext4     
&#9500;&#9472;nvme0n1p5 x5-ff-0409      32G ext4     
&#9500;&#9472;nvme0n1p6 x6-boh          32G ext4     
&#9492;&#9472;nvme0n1p7 x7-boh        72,6G ext4     
corrado@corrado-x2-gg-1009:~$ 
```

---

### Post by sudodus on 2020-10-11
[SIZE=4]A problem with the current Groovy iso files, when cloned to USB drives[/SIZE]

See [bug #1899308](https://bugs.launchpad.net/ubuntu-cdimage/+bug/1899308)

If you have an old HP computer, and want to boot it in BIOS mode, there is a problem, that I knew since several years but forgot about (when we were squashing bug #1886148).

Some old HP computers refuse to boot

- in BIOS mode
- from a USB drive
- via grub
- in a GUID partition table (GPT),

and the 'final' solution for bug #1886148 is to switch from MSDOS partition table to GPT.

If you have an HP computer, that you want to boot in BIOS mode, please test if it works with the current Groovy iso files, and if it fails, please blow the whistle.

[HR][/HR]
Do you think it is OK with a workaround, for example to create a persistent live drive with mkusb instead of cloning (using a cloning tool)?

In mkusb's settings menu for a persistent live drive you can select

- MSDOS partition table
- usb-pack-efi

and create a persistent live system that can boot such old HP computers.

---

### Post by ajgreeny on 2020-10-11
Tried to install the Xubuntu-20.10-beta-desktop-amd64.iso downloaded using zsync today from [http://cdimage.ubuntu.com/xubuntu/daily-live/current/groovy-desktop-amd64.iso](http://cdimage.ubuntu.com/xubuntu/daily-live/current/groovy-desktop-amd64.iso).

It boots without a problem and the installation goes fine using the default automatic installation until failing to install grub, showing the error
"Sorry, an error occurred and the bootloader can not be installed to your chosen destination" or very similar words (Sorry, I did not copy them exactly).
The system then offers other partitions as destination, which is of no use.

I seem to recall hearing about this elsewhere but so far have not found any bugs about this specific problem.  I'll keep searching while I wait for any clues in this thread.

---

### Post by Frogs Hair on 2020-10-11
> [COLOR=#000000]I seem to recall hearing about this elsewhere but so far have not found any bugs about this specific problem. I'll keep searching while I wait for any clues in this thread.[/COLOR]

I had a fatal error regarding grub installation more than once. The installation completed and grub was in fact installed, but ubiquity failed to exit had to be removed post installation.

[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1896525](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1896525)

---

### Post by sudodus on 2020-10-12
@ajgreeny,

I'm glad the you have no problem to boot into the USB drive.

Bad bugs are still affecting Groovy. You can find lists of them, when you browse to the [ISO testing tracker](http://iso.qa.ubuntu.com/) and look at details for the flavours.

- [Example for installing Xubuntu](http://iso.qa.ubuntu.com/qatracker/milestones/413/builds/221620/testcases/1300/results) - scroll down to 'Bugs to look for'

---

### Post by ajgreeny on 2020-10-12
Not actually a USB drive as it was an attempted installation into KVM as a VM.

However, the boot to the live system was faultless, and the live system itself appeared to run very well; it was only the apparent lack of grub installation that caused my angst!

I will try again ttoday but not wipe the VM after installing; I will try to boot it in the hope that grub is actually installed as it was for Frogs Hair.
I have added my name to the bug he linked with my comments, and did start a bug myself which I will give you the for when on my computer, not this tablet.

---

### Post by ajgreeny on 2020-10-12
No it did not work, though if I look at the installed virtual hard disk it appears that grub has been installed into the EFI partition with all the expected file present.
When I boot to te virtual install all I see is the message "Booting from hard drive" but it goes nowhere and does not seem to boot even though I have left it for many minutes.

I assume from all this that the iso file boots in UEFI mode; is there any way to make it boot in BIOS mode instead, particularly from a KVM virtual boot system?
I may try installing again in whichever mode the iso boots, but then use gparted to create a new partition table in msdos and finally try installing that way; probably a waste of time but who knows!

PS:
Here's the bug created after my first attempt where grub did not install as it should.
[https://bugs.launchpad.net/bugs/1899370](https://bugs.launchpad.net/bugs/1899370)

---

### Post by ajgreeny on 2020-10-12
I have now zsync updated my Xubuntu "current" daily to the "pending" daily; they were slightly different but only by 3%.

This pending has now booted and installed faultlessly in KVM.
However, this was the first time that I have ever noticed in the first general Overview tab, when configuring the new VM, that there's a choice of BIOS or UEFI firmware.
I chose UEFI and the install went quickly and well, grub installing as it should.

Unfortunately I now have no idea whether it was the move to UEFI firmware for this VM or the update to the "pending" iso.

Is it because I booted directly from the iso file that it defaults to UEFI mode for installation or is this how the iso will always boot in future; can a choice be made when you use dd or mkusb to copy the iso to a USB drive?

---

### Post by guiverc on 2020-10-12
@sudodus

I've [tested Thomas Schmitt's variation of the ISO]("https://bugs.launchpad.net/ubuntu-cdimage/+bug/1899308/comments/19")

for [https://bugs.launchpad.net/ubuntu-cdimage/+bug/1899308](https://bugs.launchpad.net/ubuntu-cdimage/+bug/1899308)

Alas it still didn't boot on

- hp dc7700 (c2d-e6320, 5gb, nvidia quadro nvs 290)
- hp dc7900 (c2d-e8400, 4gb, intel 4 series integrated i915)

however it booted on 4 boxes unaffected by the bug.  Please review my test & comment if any mistakes are found.

Thanks for all your work on this Nio.

---

### Post by sudodus on 2020-10-13
> **ajgreeny said:**
> Is it because I booted directly from the iso file that it defaults to UEFI mode for installation or is this how the iso will always boot in future; can a choice be made when you use dd or mkusb to copy the iso to a USB drive?

When booting, the BIOS/UEFI system decides in which mode it should boot. If a drive can boot in both modes, you can probably set a preferred mode (in some BIOS/UEFI systems).

When cloning with dd or mkusb, you cannot do anything to change this.

When making a persistent live drive with mkusb-dus, it tries to make it bootable in both boot modes (and it is usually successful with Ubuntu family iso files). You can disable one of the boot modes afterwards, if you wish, because the content of the persistent USB drive can be edited on the file level with file editing tools or for example [FONT=Courier New]**gparted**[/FONT].

But it is probably easier to modify the settings of the BIOS/UEFI system to boot only in one boot mode, UEFI or BIOS (alias CSM alias legacy) mode.

Edit: It is also possible to modify to boot structure with [FONT=Courier New]**xorriso**[/FONT] according to Thomas Schmitt's instructions in [this link](https://bugs.launchpad.net/ubuntu-cdimage/+bug/1899308)

---

### Post by sudodus on 2020-10-13
> **guiverc said:**
> Alas it still didn't boot on

- hp dc7700 (c2d-e6320, 5gb, nvidia quadro nvs 290)
- hp dc7900 (c2d-e8400, 4gb, intel 4 series integrated i915)


I think you did the things correctly. But your old HPs are stubborn.

Please try also with the current daily Ubuntu Desktop iso file,
```

$ ls -l groovy-desktop-amd64.iso
-rw------- 1 sudodus sudodus 2894153728 okt 13 08:36 groovy-desktop-amd64.iso

$ sha256sum groovy-desktop-amd64.iso
3b92cb0d427998b5a7f58377d0204ef56e3f21e8748331bef4005f8f244e814f groovy-desktop-amd64.iso

```
It works much better for me than the previous one. It needs no tweaks with [FONT=Courier New]**xorriso**[/FONT] :-)

When cloned this iso file boots in my son's HP Elitebook 8560p and also in the Lenovo V130 (in UEFI mode with secure boot).

Let us hope that your HP computers will accept it too.

If not, Thomas Schmitt has suggested a tweak - to convert the iso file's partition table to MSDOS alias MBR with [FONT=Courier New]**xorriso**[/FONT] and test if the tweaked iso file will work.

---

### Post by kansasnoob on 2020-10-13
> **sudodus said:**
> **Edit:**

[SIZE=4]Call for testing the current daily Groovy iso files[/SIZE]

The current daily Ubuntu Groovy iso file is modified, so that it gets a valid GUID partition table (GPT).

```

$ ls -l groovy-desktop-amd64.iso
-rw------- 1 sudodus sudodus 2936969216 okt 9 21:15 groovy-desktop-amd64.iso

$ md5sum groovy-desktop-amd64.iso
00cbcce8855c00dd2231077e3a01aebc groovy-desktop-amd64.iso

$ sudo gdisk groovy-desktop-amd64.iso
[sudo] password for sudodus: 
GPT fdisk (gdisk) version 1.0.3

Partition table scan:
  MBR: protective
  BSD: not present
  APM: not present
  GPT: present

Found valid GPT with protective MBR; using GPT.

Command (? for help): q

```

After this modification a USB drive with the system **cloned** from the iso file can boot also problematic Lenovo V series computers, for example my Lenovo V130 laptop, in UEFI mode with secure boot.

I checked that it works also in a Dell Precision M4800 both in BIOS mode and UEFI mode.

There have been many modifications of the boot structure of the Groovy iso files. There may be regressions for computers, that we (the testers involved in squashing the bug) have not tested. **Please wait for the next daily Groovy iso file of *your favourite* flavour of Ubuntu, and test that it can boot correctly in the computers, where you want it to work.**

The iso file must be released at or after Oct 9 21:15 for this modification to be there.

See the long story at [Bug #1886148 - failure to boot groovy daily](https://bugs.launchpad.net/ubuntu-cdimage/+bug/1886148)

[hr][/hr]
**Original post:**

The boot structure of the Ubuntu family Groovy iso files for PC computers, the amd64 iso files, is modified in a radical way and it has caused problems to boot. The problem has been solved for most of the computers tested by us 'isotesters', but there are still problems. 

**Both older and newer computers are still failing to boot into the current daily Groovy iso files**. Those computers boot into USB drives cloned from the daily iso files uploaded during June (before the radical modification of the boot structure). It seems the developers have no more ideas. See [Bug report #1886148](https://bugs.launchpad.net/bugs/1886148).

**So in order to be ready for a situation, where some computers fail to boot from USB drives created via the standard method, cloning, I suggest that we help each other test if our computers work, and if not, if there is some workaround for the problematic computers.**

- I know (from the bug report) that there are problems with some Core2Duo computers (but I have no such computer).

- I have a fairly new computer (the newest one, that I can access for testing right now, Lenovo V130 bought in Dec 2019), that cannot boot (in UEFI mode with secure boot). This computer works with Focal iso files and with Groovy iso files from June. This computer finds the USB drive in the temporary boot menu (via F12), but skips directly into the grub menu of the internal drive, when I try from a cloned USB drive.

I found that the Lenovo V130 works as expected, when mkusb-dus creates a persistent live drive with the setting 'upefi' - using usb-pack-efi. There is a menu entry for a live-only session for people who want that, so I would say that it is a workaround.

[hr][/hr]
We can suspect that there is more than one mode of failure, different for older and newer computers. We (end users) can hardly guess what needs to be done, but we might be able to find workarounds, when cloned USB drives won't boot.

**Examples of workarounds, that I can think of (to be worthwhile testing)**,

- persistent live by [mkusb-dus](https://help.ubuntu.com/community/mkusb) with various settings (not only 'upefi')
- 'grub-n-iso' or 'isoboot' for example according to [this link](https://help.ubuntu.com/community/Installation/iso2usb/isoboot)
- [Unetbootin](https://unetbootin.github.io/)
- [Rufus](https://rufus.ie) (in Windows)
- burned DVD disk (I guess there is a DVD drive in your old computers).

Finally, new workarounds are welcome :-)

I should have read this before [posting my question]("https://ubuntuforums.org/showthread.php?t=2451966") :oops:

One dumb question - will it be possible to still use msdos/mbr partition tables if using the "something else" option during installation?

---

### Post by guiverc on 2020-10-13
> **kansasnoob said:**
> I should have read this before [posting my question]("https://ubuntuforums.org/showthread.php?t=2451966") :oops:

One dumb question - will it be possible to still use msdos/mbr partition tables if using the "something else" option during installation?

I can't see why not.

Nearly all my installs use MBR (not GPT), both boxes I use and QA-test installs.  I mainly use *flavors* though.

> **sudodus said:**
> ...

Let us hope that your HP computers will accept it too.

If not, Thomas Schmitt has suggested a tweak - to convert the iso file's partition table to MSDOS alias MBR with [FONT=Courier New]**xorriso**[/FONT] and test if the tweaked iso file will work.

Both a success, and failure ?

Boots & completed QA install on  (AM test)
- hp dc7700 (c2d-e6320, 5gb, nvidia quadro nvs 290)

 FAILS TO BOOT on
 - hp dc7900 (c2d-e8400, 4gb, intel 4 series integrated i915)

[I]I'm working on another issue currently, I'll look some more at that later..

Later edit:
[/I]------------

It no longer boots on (PM testing)
- hp dc7700 (c2d-e6320, 5gb, nvidia quadro nvs 290)
- hp dc7900 (c2d-e8400, 4gb, intel 4 series integrated i915)

here I'm bewildered? 

I ejected thumb-drive, re-inserted, flashing of thumb-drive indicates to  me (subjectively) it's being read, then ignored & hdd of 'recent'  QA-install loads (and fast-flashing stops on thumb-drive)

Box has been turned off, let sit awhile, and try again & nope; it won't boot again on dc7700.  It for sure did ~three hours ago (*the box didn't have a bootable installed OS before my earlier success!!*)

---

### Post by kansasnoob on 2020-10-14
Neither Latitude E6400's or an E6510 will even recognize the image on USB. The E6400's are C2D (both P series and T series cpu's fail), and the E6510 has an i7 M620. I've tried creating the live USB's both with Focal's startup disc creator and uNetbootin - no dice! I'll try a DVD tomorrow as time allows. Prior images work fine so it's not hardware settings - usually you just press F12 repeatedly to display the one time boot menu and select USB, but in this case no USB appears to be found.

---

### Post by sudodus on 2020-10-14
> **kansasnoob said:**
> One dumb question - will it be possible to still use msdos/mbr partition tables if using the "something else" option during installation?

This should be independent of the boot structure of the iso files, so I think: ***Yes***.

If you fail, you are probably affected by another [new?] bug.

---

### Post by sudodus on 2020-10-14
> **kansasnoob said:**
> Neither Latitude E6400's or an E6510 will even recognize the image on USB. The E6400's are C2D (both P series and T series cpu's fail), and the E6510 has an i7 M620. I've tried creating the live USB's both with Focal's startup disc creator and uNetbootin - no dice! I'll try a DVD tomorrow as time allows. Prior images work fine so it's not hardware settings - usually you just press F12 repeatedly to display the one time boot menu and select USB, but in this case no USB appears to be found.

I'm glad you found this before the release of Groovy.

So now there are problems not only with old HPs but also old Dells, and you can add more heat to the [bug report #1899308](https://bugs.launchpad.net/ubuntu-cdimage/+bug/1899308)

Please be sure to **test the current Ubuntu Desktop Groovy iso file when cloned** (for example via Startup Disk Creator or mkusb) in the old Dells:

Ubuntu Groovy version dated Okt 13 08:36 from zsync,

- '20201013.1' in the testing tracker
```

$ ls -l groovy-desktop-amd64.iso
-rw------- 1 sudodus sudodus 2894153728 okt 13 08:36 groovy-desktop-amd64.iso

$ sha256sum groovy-desktop-amd64.iso
3b92cb0d427998b5a7f58377d0204ef56e3f21e8748331bef4005f8f244e814f groovy-desktop-amd64.iso

```

It might work, and anyway your test result will be valuable information for squashing this bug.

[hr][/hr]
I think the old Dells will boot from

- **DVD**

- a **tweaked iso file** converted to msdos partition table using [FONT=Courier New]**xorriso**[/FONT] according to instructions from Thomas Schmitt in the [bug report #1899308](https://bugs.launchpad.net/ubuntu-cdimage/+bug/1899308)

- a **persistent live drive made with mkusb** with the settings

. 'usb-pack-efi' and
. 'msdos partition table'

[hr][/hr]
- a** 'nopersistent'** USB drive created by **mkusb-plug** *might* work. See the details at

. [bug report 1899308, comment #41 and #56](https://bugs.launchpad.net/ubuntu-cdimage/+bug/1899308) and
. [help.ubuntu.com/community/mkusb/plug](https://help.ubuntu.com/community/mkusb/plug)

---

### Post by sudodus on 2020-10-14
> **guiverc said:**
> Both a success, and failure ?

Boots & completed QA install on  (AM test)
- hp dc7700 (c2d-e6320, 5gb, nvidia quadro nvs 290)

 FAILS TO BOOT on
 - hp dc7900 (c2d-e8400, 4gb, intel 4 series integrated i915)

[I]I'm working on another issue currently, I'll look some more at that later..

Later edit:
[/I]------------

It no longer boots on (PM testing)
- hp dc7700 (c2d-e6320, 5gb, nvidia quadro nvs 290)
- hp dc7900 (c2d-e8400, 4gb, intel 4 series integrated i915)

here I'm bewildered? 

I ejected thumb-drive, re-inserted, flashing of thumb-drive indicates to  me (subjectively) it's being read, then ignored & hdd of 'recent'  QA-install loads (and fast-flashing stops on thumb-drive)

Box has been turned off, let sit awhile, and try again & nope; it won't boot again on dc7700.  It for sure did ~three hours ago (*the box didn't have a bootable installed OS before my earlier success!!*)

If I understand correctly, you tested **Lubuntu**, but I think the latest and greatest boot structure suggested by Thomas Schmitt is only present in **Ubuntu**, the current Groovy iso file '20201013.1' in the testing tracker, dated Okt 13 08:36 from zsync.

---

### Post by ajgreeny on 2020-10-14
I have now also installed the daily pending iso of Ubuntu from two days ago very successfully in KVM without any difficulties.
I again chose to install using UEFI firmware and so far it looks good and works well.

---

### Post by guiverc on 2020-10-15
> **sudodus said:**
> If I understand correctly, you tested **Lubuntu**, but I think the latest and greatest boot structure suggested by Thomas Schmitt is only present in **Ubuntu**, the current Groovy iso file '20201013.1' in the testing tracker, dated Okt 13 08:36 from zsync.

Yep.

I see you requested ([https://bugs.launchpad.net/ubuntu-cdimage/+bug/1899308/comments/31](https://bugs.launchpad.net/ubuntu-cdimage/+bug/1899308/comments/31)) me to test that... but I ran out of energy before doing it.

If you still want me to test 20201013.1 let me know.

I grabbed & tested 20201014 (main Ubuntu) and it responds identically to Lubuntu on 
- hp dc7700 (c2d-e6320, 5gb, nvidia quadro nvs 290)
- hp dc7900 (c2d-e8400, 4gb, intel 4 series integrated i915)

Refer [https://bugs.launchpad.net/ubuntu-cdimage/+bug/1899308/comments/40](https://bugs.launchpad.net/ubuntu-cdimage/+bug/1899308/comments/40)
I included a link to [http://iso.qa.ubuntu.com/qatracker/milestones/413/builds/221729/testcases/1303/results](http://iso.qa.ubuntu.com/qatracker/milestones/413/builds/221729/testcases/1303/results) where some details are recorded  (*I tried booting it more times that I bothered recording on iso.qa.ubu*)

In summary it booted first time on dc7700, but subsequently refused to boot. Subsequent re-tries were simple reboots, to turning off & back on, different USB ports, including various waits between retries (with box off, up to ~90 mins)

This is exactly the same behavior as I get with Lubuntu groovy daily (last two days anyway; before then I go NO boots whatsoever on dc7700).

---

### Post by sudodus on 2020-10-15
@guiverc,

1. I think your tests with the current Ubuntu Groovy iso file are enough for this purpose.

2. This is another test, that you should do with an iso file that makes the USB drive perform differently between the first and subsequent boot attempts: In the [bug report, comment #41](https://bugs.launchpad.net/ubuntu-cdimage/+bug/1899308) I am suggesting some methods to test in a way that should not change the content of the USB drive, and the result should be possible to reproduce: Use the boot option 'nopersistent'.

---

### Post by kansasnoob on 2020-10-15
So, back to testing on the Dell Latitude E6510 with Ubuntu daily 20201015 on a USB created by Start Up Disk Creator in Focal and still no dice so I added a comment here:

[https://bugs.launchpad.net/ubuntu-cdimage/+bug/1899308](https://bugs.launchpad.net/ubuntu-cdimage/+bug/1899308)

---

### Post by guiverc on 2020-10-15
I did more testing this morning... however i'm hopeful my issues with [1899308]("https://bugs.launchpad.net/ubuntu-cdimage/+bug/1899308") will be resolved when casper is bumped to 1.454 (current ISOs are using 1.452); ie. in the [1.454 changelog]("https://changelogs.ubuntu.com/changelogs/pool/main/c/casper/casper_1.454/changelog") are what I hope will fix it.  (1.454 was queued prior to [final freeze]("https://lists.ubuntu.com/archives/ubuntu-devel-announce/2020-October/001284.html"))

For Lubuntu purposes I've [posted on our discourse]("https://discourse.lubuntu.me/t/final-testing-of-ubuntu-groovy-gorilla-20-10/1668") (*I can always hope we'll get more testing*).  My (this) post is a mixture of details from bug report (*where loads of it goes above my head!*), plus a lot from IRC discussions (*I'm a fly on the wall in #ubuntu-release*).

@sudodus I hadn't read your comment #51 of this thread before my earlier testing today; I was completing tests I wanted to do yesterday but lacked time (ie. to prove it wasn't just `dus`)

I'll test a standard `dus` written ISO with boot option `nopersistent` when/if I can.  (*I no longer see it as high-priority unless 1.454 doesn't work like I hope it will*)

ps:  Thanks for your testing @kansasnoob  (*knowledge it impacts non-HP added weight!*)

---

### Post by sudodus on 2020-10-16
> **sudodus said:**
> I'm glad you found this before the release of Groovy.

So now there are problems not only with old HPs but also old Dells, and you can add more heat to the [bug report #1899308](https://bugs.launchpad.net/ubuntu-cdimage/+bug/1899308)

Please be sure to **test the current Ubuntu Desktop Groovy iso file when cloned** (for example via Startup Disk Creator or mkusb) in the old Dells:

Ubuntu Groovy version dated Okt 13 08:36 from zsync,

- '20201013.1' in the testing tracker
```

$ ls -l groovy-desktop-amd64.iso
-rw------- 1 sudodus sudodus 2894153728 okt 13 08:36 groovy-desktop-amd64.iso

$ sha256sum groovy-desktop-amd64.iso
3b92cb0d427998b5a7f58377d0204ef56e3f21e8748331bef4005f8f244e814f groovy-desktop-amd64.iso

```

It might work, and anyway your test result will be valuable information for squashing this bug.

[hr][/hr]
I think the old Dells will boot from

- **DVD**

- a **tweaked iso file** converted to msdos partition table using [FONT=Courier New]**xorriso**[/FONT] according to instructions from Thomas Schmitt in the [bug report #1899308](https://bugs.launchpad.net/ubuntu-cdimage/+bug/1899308)

- a **persistent live drive made with mkusb** with the settings

. 'usb-pack-efi' and
. 'msdos partition table'

[hr][/hr]
- a** 'nopersistent'** USB drive created by **mkusb-plug** *might* work. See the details at

. [bug report 1899308, comment #41 and #56](https://bugs.launchpad.net/ubuntu-cdimage/+bug/1899308) and
. [help.ubuntu.com/community/mkusb/plug](https://help.ubuntu.com/community/mkusb/plug)

> **kansasnoob said:**
> So, back to testing on the Dell Latitude E6510 with Ubuntu daily 20201015 on a USB created by Start Up Disk Creator in Focal and still no dice so I added a comment here:

[https://bugs.launchpad.net/ubuntu-cdimage/+bug/1899308](https://bugs.launchpad.net/ubuntu-cdimage/+bug/1899308)

@ kansasnoob,

It would be interesting to know if any of the suggested workarounds (that work for the old HPs with c2d CPUs) will work for your old Dells. I think ***DVD*** or ***persistent live drive made with mkusb*** are most likely to work.

On the other hand, maybe you do not intend to use 20.10 on these old Dells, but intend to stay with 20.04.x LTS. But I think this bug should be squashed or at least worked around until the next LTS version.

---

### Post by guiverc on 2020-10-16
> **sudodus said:**
> @guiverc,
..

2. This is another test, that you should do with an iso file that makes the USB drive perform differently between the first and subsequent boot attempts: In the [bug report, comment #41]("https://bugs.launchpad.net/ubuntu-cdimage/+bug/1899308") I am suggesting some methods to test in a way that should not change the content of the USB drive, and the result should be possible to reproduce: Use the boot option 'nopersistent'.

Today's  (2020-10-15) ISO was re-written to thumb-drive using normal `dus` in live mode.

Booted on 
- hp dc7900 (c2d-e8400, 4gb, intel 4 series integrated i915)

with 'nopersistent' added to kernel line at grub. 

It was shutdown (I ejected & re-inserted) thumb-drive.

It booted a second time as you expected (again using `nopersistent`) on
- hp dc7900 (c2d-e8400, 4gb, intel 4 series integrated i915)
Machine was shutdown.

It was then tested on (again using `nopersistent`)
- hp dc7700 (c2d-e6320, 5gb, nvidia quadro nvs 290)
and booted (again using `nopersistent).

Yep, the `nopersistent` option allows the thumb-drive to be re-used, as you believed.

---

### Post by brisch on 2020-10-16
I am a long time user of UBUNTU and have upgraded every cycle.
Started the latest cycle in May and have been updating every two days.
About a week ago I decided to install a latest test and ended up crashing in smoke like many others.
Used my usual way of starting an install (this I the way I do it) selecting the something else in the
install menu.  After several failures I went back to gparted and started with a fresh setup of the disk.
Still no luck so I decided to go at it in another way.
rather then selecting something else I chose a clean install including clearing the disk.
This one worked and now I am going to describe some of the things I found.
I found the discussion on the GUID partiltion table and how it arranges the disk structure.
This I my WAG  many of the computers have been set up for the disk for the user.
I found that comparing the older partition table I set up.
The GUID table was different so my predefined partition table did not work.
By allowing the install to define the disk structure it was not exactly like how I set
up the partition table.  Perhaps  people are trying to use their old disk structure
and grub-install will not work. It is possible that partition table uses the whole disk
and grub can't configure properly. What are your thoughts?

---

### Post by kansasnoob on 2020-10-17
The latest daily seems to have my Latitude's sorted out. First boot OK, second boot OK, and trying in yet another laptop it's still good so I'd call that "sorted out".

---

### Post by guiverc on 2020-10-17
Yeah, I agree with @kansasnoob.

Casper 1.455 has fixed Ubuntu *groovy* 2020-10-16.4, so with luck *flavors* will be fixed with tomorrow's daily.

Another win (unrelated to ISO booting, but with `calamares` so Lubuntu & Ubuntu Studio) was also fixed ~today; [https://bugs.launchpad.net/ubuntu/+source/calamares/+bug/1898501](https://bugs.launchpad.net/ubuntu/+source/calamares/+bug/1898501)  :)

---

### Post by sudodus on 2020-10-17
> **kansasnoob said:**
> The latest daily seems to have my Latitude's sorted out. First boot OK, second boot OK, and trying in yet another laptop it's still good so I'd call that "sorted out".

> **guiverc said:**
> Yeah, I agree with @kansasnoob.

Casper 1.455 has fixed Ubuntu *groovy* 2020-10-16.4, so with luck *flavors* will be fixed with tomorrow's daily.

Another win (unrelated to ISO booting, but with `calamares` so Lubuntu & Ubuntu Studio) was also fixed ~today; [https://bugs.launchpad.net/ubuntu/+source/calamares/+bug/1898501](https://bugs.launchpad.net/ubuntu/+source/calamares/+bug/1898501)  :)

+1

The current Ubuntu Desktop (standard Ubuntu) Groovy version dated Okt 17 08:30 from zsync,

- '20201017' in the testing tracker
```

ls -l groovy-desktop-amd64.iso
-rw------- 1 sudodus sudodus 2942062592 okt 17 08:30 groovy-desktop-amd64.iso

$ sha256sum groovy-desktop-amd64.iso
f572ff624215e00b398233be6a9e482d41b706c24266ed05bd019a6ab75bf53d groovy-desktop-amd64.iso

```
when cloned to a USB3 pendrive, can boot

- an old HP Elitebook 8560p (in BIOS mode) - This was problematic in the previous daily iso file, it booted only the first time. Now it booted successfully 3 times in a row. The 300K partition is preserved and the ext4 partition is created correctly (and preserved between boots).

- a middle-aged Dell Precision M4800 (in BIOS mode and UEFI mode) - Works as usual.

- a newer Lenovo V130 (in UEFI mode with secure boot) - Works since GUID partition table.

[HR][/HR]
I tested with a second USB drive, this time an SSD connected via a USB3 to SATA adapter and cloned from the iso file.

- I started booting the Lenovo V130 in UEFI mode with secure boot (and let it create the ext4 partition). The 300K partition is preserved and the ext4 partition is created correctly.

- Then I tested with the previously problematic HP Elitebook 8560p (in BIOS mode). It booted as it should.

[HR][/HR]
It looks like we have squashed this bug :-)

---

