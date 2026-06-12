---
title: "Can you test booting into an nvme drive?"
date: 2019-11-16
forum: Ubuntu Development Version
---

### Post by sudodus on 2019-11-16
[SIZE=4]Introduction[/SIZE]

**nvme** drives, SSD drives connected via PCI Express, are getting more common becasue they can be faster than SSD drives connected via SATA.

I installed such drive, an m2 stick via a PCI Express card into my workstation, a Lenovo Thinkstation C30, that I bought second hand (refurbished). This solution [with an m2 stick via a PCI Express card] is much cheaper than buying a computer that is new enough to boot from nvme.

The nvme drive works and writes 2.4 times faster than my SSD connected via SATA. It can probably be faster when cooperating with newer interfacing hardware.

In this configuration it is not possible to boot directly into the nvme drive. The BIOS/UEFI system does not recognize it. But using Ubiquity in Xubuntu Focal I can make a boot partition in a SATA drive and from there boot into the root partition in the nvme drive. I can also run sudo update-grub from my main operating system in the SATA-SSD to get a working menuentry.

[SIZE=4]Tests on the to-do list[/SIZE]

- I have added the feature to recognize nvme drives to mkusb. It can create what seems to be a correct persistent live drive, but I cannot test it correctly, only via a boot partition in another drive. (I tested from another persistent live drive made with mkusb, and it could use the iso9660 partition and the casper-rw partitions in the nvme drive).

- I have also tested the installer Calamares of Lubuntu Focal. It does not recognize the nvme partition, and I did not see any [intuitive?] way to put the boot partition in another drive and the root partition in the nvme drive. Maybe there is a way, but direct testing in a computer that can boot from nvme is much better.

[hr][/hr]
So if you have a computer, that can boot from an nvme drive, and you can it use for testing (including editing and/or overwriting the nvme drive), please let me know, and we can talk about details of the testing.

---

### Post by VMC on 2019-11-17
I have a computer with nvme. I used it for quite some time. During that time my PC would reboot with no warning. Returned to Acer. They said it was fix. Turns out it was the nvme. I'm reluctant to even use it again.
But, when I was using it, only Windows saw it. Couldn't and still can't get Linux to see it, until I boot up Windows, use disk tools to shrink partition then Linux see's the unallocated partition. There's something off with my Acer nvme and Linux from a standing start. Windows needs to intervene first.

I'd like to help you, but getting to the physical location of the m.2 slot requires dismantling several pieces of hardware just to get to it. Your right about the speed.

---

### Post by sudodus on 2019-11-17
Hi VMC,

Interesting to read about your problems with nvme. It seems to me that your Acer computer was made before the manufacturer knew the technology well enough to make a robust system.

Have you looked for a new version of the UEFI/BIOS system? Maybe there is a new version, that makes your computer manage the nvme drive in a reliable way?

Anyway, I can understand that you are reluctant to tamper with nvme it that computer, so even if it would be nice to get your help with testing, I think it is better to wait and hope that someone has a computer that works in a reliable way with nvme.

---

### Post by P-I H on 2019-11-17
On my desktop with a MSI B350 Tomahawk motherbord I have used 2 NVMe drives. First I used a Samsung 960 EVO connected to the M.2 port on the motherbord. However I lost the screw to mount the NVMe. As a replacement I'm now using a Kingston SSDNOW A1000 480GB M.2 connected  to a DeLOCK PCI Express x4 Card.
The 960 EVO worked OK, there were no problem with installation or usage. Installation of Ubuntu work OK with my usual method, download of the ISO and copied to a USB drive with DD.
The same is the case the the Kingston drive on Ubuntu 19.10 and on a installation of Focal Fossa in Boxes
This is the specifications of the desktop
```
p-i@pi-MS-7A34:~$ inxi -Fz
System:    Host: pi-MS-7A34 Kernel: 5.3.0-23-generic x86_64 bits: 64 Desktop: Gnome 3.34.1 Distro: Ubuntu 19.10 (Eoan Ermine) 
Machine:   Type: Desktop Mobo: Micro-Star model: B350 TOMAHAWK (MS-7A34) v: 1.0 serial: <filter> UEFI: American Megatrends 
           v: 1.H0 date: 05/02/2018 
CPU:       Topology: 8-Core model: AMD Ryzen 7 1700 bits: 64 type: MT MCP L2 cache: 4096 KiB 
           Speed: 1377 MHz min/max: 1550/3750 MHz Core speeds (MHz): 1: 1377 2: 1377 3: 1377 4: 1377 5: 1378 6: 1378 7: 1377 
           8: 1375 9: 1376 10: 1375 11: 1378 12: 1374 13: 1377 14: 1376 15: 1377 16: 1377 
Graphics:  Device-1: Advanced Micro Devices [AMD/ATI] Ellesmere [Radeon RX 470/480/570/570X/580/580X/590] driver: amdgpu 
           v: kernel 
           Display: x11 server: X.Org 1.20.5 driver: amdgpu tty: N/A 
           OpenGL: renderer: Radeon RX 580 Series (POLARIS10 DRM 3.33.0 5.3.0-23-generic LLVM 9.0.0) v: 4.5 Mesa 19.2.1 
Audio:     Device-1: C-Media CMI8788 [Oxygen HD Audio] driver: snd_virtuoso 
           Device-2: AMD Ellesmere HDMI Audio [Radeon RX 470/480 / 570/580/590] driver: snd_hda_intel 
           Device-3: Advanced Micro Devices [AMD] Family 17h HD Audio driver: snd_hda_intel 
           Device-4: Logitech Webcam C250 type: USB driver: snd-usb-audio,uvcvideo 
           Sound Server: ALSA v: k5.3.0-23-generic 
Network:   Device-1: Realtek RTL8111/8168/8411 PCI Express Gigabit Ethernet driver: r8169 
           IF: enp30s0 state: up speed: 1000 Mbps duplex: full mac: <filter> 
Drives:    Local Storage: total: 903.59 GiB used: 84.71 GiB (9.4%) 
           ID-1: /dev/nvme0n1 vendor: Kingston model: SA1000M8480G size: 447.13 GiB 
           ID-2: /dev/sda vendor: Samsung model: SSD 850 EVO 250GB size: 232.89 GiB 
           ID-3: /dev/sdb vendor: SanDisk model: Ultra II 240GB size: 223.57 GiB 
Partition: ID-1: / size: 437.68 GiB used: 84.68 GiB (19.3%) fs: ext4 dev: /dev/dm-3 
           ID-2: swap-1 size: 980.0 MiB used: 24.9 MiB (2.5%) fs: swap dev: /dev/dm-4 
Sensors:   System Temperatures: cpu: 37.0 C mobo: 39.0 C gpu: amdgpu temp: 33 C 
           Fan Speeds (RPM): fan-1: 0 fan-2: 728 fan-3: 0 fan-4: 0 fan-5: 569 fan-6: 812 gpu: amdgpu fan: 1241 
Info:      Processes: 403 Uptime: 1d 21h 19m Memory: 15.65 GiB used: 6.60 GiB (42.2%) Shell: bash inxi: 3.0.36 
p-i@pi-MS-7A34:~$ 

```
However I have tried the Kingston NVMe and the PCI-Express card on an older computer with a Gigabyte GA-990FXA-UD3 motherboard and this didn't work.

---

### Post by sudodus on 2019-11-17
Hi P-I H,

Nice to read that it works for you with an nvme drive via a PCI Express card.

Am I understanding correctly, that

- the computer can boot from the nvme drive
- right now you have no system, that is available for testing

or would it be possible for you to do some testing in the computer where your nvme drive is working?

---

### Post by P-I H on 2019-11-17
It's no problem to boot from the NVMe drive, but this is my main computer and I don't want to do any testing that will force me to reinstall.
What kind of tests/information are you after?

Some information about the NVMe.
```
p-i@pi-MS-7A34:~$ sudo nvme smart-log /dev/nvme0
Smart Log for NVME device:nvme0 namespace-id:ffffffff
critical_warning                    : 0
temperature                         : 44 C
available_spare                     : 100%
available_spare_threshold           : 100%
percentage_used                     : 0%
data_units_read                     : 1&#8239;855&#8239;051
data_units_written                  : 2&#8239;756&#8239;190
host_read_commands                  : 19&#8239;857&#8239;806
host_write_commands                 : 26&#8239;339&#8239;101
controller_busy_time                : 85
power_cycles                        : 685
power_on_hours                      : 191
unsafe_shutdowns                    : 43
media_errors                        : 0
num_err_log_entries                 : 0
Warning Temperature Time            : 0
Critical Composite Temperature Time : 0
Temperature Sensor 2                : 44 C
Thermal Management T1 Trans Count   : 0
Thermal Management T2 Trans Count   : 0
Thermal Management T1 Total Time    : 0
Thermal Management T2 Total Time    : 0
p-i@pi-MS-7A34:~$
```

---

### Post by VMC on 2019-11-18
> **P-I H said:**
> On my desktop with a MSI B350 Tomahawk motherbord I have used 2 NVMe drives. First I used a Samsung 960 EVO connected to the M.2 port on the motherbord. However I lost the screw to mount the NVMe.  That very tiny screw is what I'm trying to find. Going to Micro Center to pick another nvme drive and will see if they have it. I just re-installed my nvme ssd, but mine is built into the motherboard. I think [COLOR=#000000]**sudodus** has an add-on nvme.[/COLOR]

---

### Post by jetsam on 2019-11-18
> That very tiny screw is what I'm trying to find.

If you have a local hardware store, try there first.  They should have a selection of machine screws at reasonable prices.  Ordering online, you're likely to get 100 and pay hidden shipping costs, or be forced to buy 1000 in an assortment... Plus you need to measure the screw to order the right one.  Just take the enclosure (or whatever) into the store, and you can test before you buy.

---

### Post by oldfred on 2019-11-18
Still not sure what size it really is, looks like M2, and search just finds other metric screws.
[https://www.google.com/search?client=ubuntu&channel=fs&q=nvme+screw+size&ie=utf-8&oe=utf-8](https://www.google.com/search?client=ubuntu&channel=fs&q=nvme+screw+size&ie=utf-8&oe=utf-8)

I like the second link is $7.99 but $144.19 for expert installation.

---

### Post by sudodus on 2019-11-19
> **P-I H said:**
> It's no problem to boot from the NVMe drive, but this is my main computer and I don't want to do any testing that will force me to reinstall.
What kind of tests/information are you after?


It is a good idea to avoid tampering with your main computer.

What I want is testing mkusb and Calamares:

- Test if the tool can make a complete installation into an nvme drive so that the computer can boot from it
- If it works, fine, that's it,
- Otherwise help debugging by repeated tests with modified versions of the tool until it works.

> 
- I have added the feature to recognize nvme drives to mkusb. It can create what seems to be a correct persistent live drive, but I cannot test it correctly, only via a boot partition in another drive. (I tested from another persistent live drive made with mkusb, and it could use the iso9660 partition and the casper-rw partitions in the nvme drive).

- I have also tested the installer Calamares of Lubuntu Focal. It does not recognize the nvme partition, and I did not see any [intuitive?] way to put the boot partition in another drive and the root partition in the nvme drive. Maybe there is a way, but direct testing in a computer that can boot from nvme is much better.


---

### Post by sudodus on 2019-11-19
> **VMC said:**
> That very tiny screw is what I'm trying to find. Going to Micro Center to pick another nvme drive and will see if they have it. I just re-installed my nvme ssd, but mine is built into the motherboard. I think [COLOR=#000000]**sudodus** has an add-on nvme.[/COLOR]

I was very cautious with that tiny screw, realizing that my old eyes might not see it, if I would drop it to the floor. 

Yes, I connected my nvme drive (an m2 stick) via a PCI Express card to the motherboard. (And my computer cannot boot from it, but can use it for the root partition when booted from another drive.)

> 
Still not sure what size it really is, looks like M2, and search just finds other metric screws.
[www.google.com/search?client=ubuntu&channel=fs&q=nvme+screw+size&ie=utf-8&oe=utf-8](https://www.google.com/search?client=ubuntu&channel=fs&q=nvme+screw+size&ie=utf-8&oe=utf-8)

I like the second link is $7.99 but $144.19 for expert installation.


I found useful links specifying that tiny screw via your search pattern. Thanks @oldfred :-)

---

### Post by jetsam on 2019-11-19
> I like the second link is $7.99 but $144.19 for expert installation. 

lol.  If you can find it locally in a bin of a hardware store or, better, your local makerspace, it would be less than a quarter.

...sorry to bust in, all.  I don't know what sub-forum this even is.  I just read about the screw on the feed...

As you were.
--jetsam

---

### Post by P-I H on 2019-11-19
The dimension of that tiny screw is related to the motherboard. There is certainly no standard size. The screw on my PCI-card has one size and the screw on the motherboard has a different size. The screw on the MSI motherboard isn't that common. I had the opportunity to find a replacement in a computer repair shop, but I didn't find one.
However there is an advantage to use the PCI-card as you are able to easily remove the NVMe disk in case you want to install different systems on different disks. The big drawback is the speed. Average read speed is in my case limited to about 1GB/s on the PCI-card.
@sododus
OK I can use my spare NVMe Samsung 960 EVO to do some testing. I normally use dd to copy an ISO to USB, but it's good to learn some more methods.

---

### Post by QIII on 2019-11-19
The M.2 nomenclature for the type of storage notwithstanding, I believe that "M2 screw" represents the size of the screw (M2.0 wafer head machine screw), which should have a thread length of about 1.5mm in most cases.  These can be bought by the gross.

---

### Post by sudodus on 2019-11-19
> **P-I H said:**
> 
@sododus
OK I can use my spare NVMe Samsung 960 EVO to do some testing. I normally use dd to copy an ISO to USB, but it's good to learn some more methods.

Good news :-)

Please tell me if you need [more] details in order to start testing.

---

### Post by jetsam on 2019-11-19
yes, but...  who needs a gross of screws?  What are you going to do with the other 143?  I guess you could start using them for odd projects, if you bought an m2 tap and had something to tap into...

...it doesn't matter much...  

There is an issue though in that there's more than one common threading for an m2 screw, and we're not certain it's an m2 even.  You need calipers and a thread gauge: about $140.00 for quality versions, maybe $40.00 for inexpensive but functional clones from China...

Edit: It's not just thread length, it's thread spacing...  you buy different taps for different screws with different thread spacing.  Using the wrong threaded screw is liable to strip the threads, break the screw, gum up the works.  Quite likely in this instance, you would strip the threads and make the screw non-functional.  It would vibrate loose in the case later, and roll around and annoy you 'till you found it three years later while dusting the fans...  Not a big deal, in the grand scheme of things ;)

---

### Post by P-I H on 2019-11-19
So far so good
Now it's only to select the NVMe drive and see if it's OK to boot.

---

### Post by P-I H on 2019-11-19
Now I will reboot to see if it's working.

---

### Post by P-I H on 2019-11-19
Worked to boot from the NVMe in legacy mode. Perhaps there is a setting in BIOS to boot from the EFI partition.
Perhaps this wasn't the usecase you wanted. When I start the installation I'm able to install Ubuntu to either sda, the Samsung 250GB SSD, or ScanDisk Cruzer Contour USB.

---

### Post by VMC on 2019-11-19
> **sudodus said:**
> It is a good idea to avoid tampering with your main computer.

What I want is testing mkusb and Calamares:

- Test if the tool can make a complete installation into an nvme drive so that the computer can boot from it
- If it works, fine, that's it,
- Otherwise help debugging by repeated tests with modified versions of the tool until it works.
Yes, I can install using  Calamares and it does boot. Unsure about meaning of 'mkusb'. I install ubuntu.iso using hybrid method into my usb flash, then boot into that usb, then install from Calamares into my m.2 ssd.

---

### Post by sudodus on 2019-11-19
> **P-I H said:**
> Worked to boot from the NVMe in legacy mode. Perhaps there is a setting in BIOS to boot from the EFI partition.
Perhaps this wasn't the usecase you wanted. When I start the installation I'm able to install Ubuntu to either sda, the Samsung 250GB SSD, or ScanDisk Cruzer Contour USB.
Thanks, this was an important part of what I wanted.

We can see that mkusb can clone a system that can boot, which is good.

There another task for mkusb: to create a **persistent live** system, which involves creating 5 partitions, and to boot the resulting system twice to make sure that it is persistent. You can create a file in the home directory for example by

```

echo 'Hello World' > hello

```

and after reboot check it with

```

cat hello

```

You can also check that the root directory will have the same size as the mount point of the `casper-rw`partition as seen by

```

df -h

```

I think it will work, but it will be valuable to really check it.

-o-

VMC has shown that it works to install Lubuntu with its installer **Calamares**. This does not work in my computer (does not see the nvme drive at all).

---

### Post by sudodus on 2019-11-19
> **VMC said:**
> Yes, I can install using  Calamares and it does boot. Unsure about meaning of 'mkusb'. I install ubuntu.iso using hybrid method into my usb flash, then boot into that usb, then install from Calamares into my m.2 ssd.

The meaning with the test using mkusb is that it is possible to have a persistent live system not only in a USB pendrive, but also in a faster drive. I have tested that it works in SSD drives connected internally via SATA, externally via eSATA as well as via USB and also in memory cards. But I have not been able to test it in an nvme drive.

Thanks a lot for confirming that it works with Calamares :-)

This shows that it works, when the computer's UEFI/BIOS system and grub can see the nvme drive. The case in my computer is special because it is a fix in an old computer, and it is not urgent to make it work for that corner case.

---

### Post by P-I H on 2019-11-19
Run into some problem, which I don't understand. Used "default" on the previous settings in this case. Also tried to select MSDOS GPT and and the "efi" choice and got the same message.
I don't think this is related to the NVMe drive.

---

### Post by sudodus on 2019-11-19
> **P-I H said:**
> Run into some problem, which I don't understand. Used "default" on the previous settings in this case. Also tried to select MSDOS GPT and and the "efi" choice and got the same message.
I don't think this is related to the NVMe drive.

This is information about a complication: To make a drive when running in UEFI mode and trying to make the target drive bootable both in UEFI mode and BIOS mode. The problem is that grub-pc is not compatible with grub-efi (they cannot co-exist), but you are offered workarounds, that you may use.

You can continue and

- not bother with BIOS boot if you wish or

- later on select to use that image (alternative 3), which should make it possible to boot from the nvme both in UEFI mode and BIOS mode.

---

### Post by P-I H on 2019-11-20
OK,
I tried to boot the "primary" drive in non efi mode but didn't succeed. I also selected alternative 3, but I didn't try to boot that image. 
I have now rebuilt my PC and I'm not ready to do any further testing, in case there are no strong requirements to do so.

---

### Post by sudodus on 2019-11-20
> **P-I H said:**
> OK,
I tried to boot the "primary" drive in non efi mode but didn't succeed. I also selected alternative 3, but I didn't try to boot that image. 
I have now rebuilt my PC and I'm not ready to do any further testing, in case there are no strong requirements to do so.

Thanks for the testing :-)

I cannot require any testing, only ask for it, and the tests you have performed were very helpful. I draw the conclusion, that mkusb is not quite ready for an nvme drive as target. There is still some remaining bug, and it can wait to be fixed until someone is asking for the feature (to install a persistent live drive into an nvme drive).

---

### Post by sudodus on 2019-12-04
Now I have found a fairly new laptop with an nvme drive, where I can test things myself.

- It is a Lenovo V130 with a Samsung drive
- Windows was installed with the storage controller mode RST
- In order for Ubuntu to see the drive I had to change to the storage controller mode  AHCI
- I backed up Windows with Clonezilla

- I installed Xubuntu Focal alongside Windows.

It worked as it should. There is a menuentry to get easily into the UEFI/BIOS setup (to switch storage controller mode, so it was fairly easy to switch between Xubuntu and Windows).

- I installed persistent live Lubuntu Focal (yes, into the nvme drive, so the persistent live system is really fast).

It works as it should in this drive which can be seen at boot and by grub. See the attached screenshot.

---

### Post by lammert-nijhof on 2019-12-06
I installed Ubuntu 19.10 on ZFS on a NVME drive (Silicon Power 512GB) and it worked directly without any problem. I avoid using UEFI, since it has been invented by Microsoft to make out life hell. I dual boot and have an ext4 boot on one of my two HDDs and both work.

---

### Post by oldfred on 2019-12-06
UEFI was not invented by Microsoft.
It was from Intel originally as EFI. And adopted by Apple Mac when they changed to Intel chips. 
Then Intel turned it over to the UEFI Forum in 2005 and version 2 was released & original EFI renumbered to v1.
Windows did not adopt UEFI until 2012, but did implement UEFI Secure Boot which causes a lot of the controversy. You can just turn Secure Boot off.

[https://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface](https://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface)

[https://en.wikipedia.org/wiki/Unified_EFI_Forum](https://en.wikipedia.org/wiki/Unified_EFI_Forum)

---

### Post by VMC on 2019-12-06
> **oldfred said:**
> ... You can just turn Secure Boot off.
...

For a long time I was weary of turning it off. MS put the fear in me. Then I came to my senses, and now its off. I think all Arch installs wont install with it on.

---

### Post by harry332 on 2019-12-07
However, if you are running Windows, even WIN 10, which is protected by Defender, a part of the operating system, you will need the Secure Boot.
Defender is helpless against firmware rootkits, bootkits, kernel and driver rootkits.
These may run right from the power on and stay hidden.
Secure Boot can protect against these malware.

Running WIN10 there is no harm using the Secure Boot, it is a good protection though.
The only issue I know appears when you try to make a clean installation with a bootable UEFI USB.
The UEFI/BIOS does not see the USB as a bootable UEFI device when formatted NTFS with a GPT Partition.
You cannot use FAT32, because new WIN10 ISO contains one file of 4.6 GB.
But there is a good workaround for this one also.

---

### Post by P-I H on 2019-12-26
I used mkusb to make a bootable USB drive. There were no problems to make the USB, but the installation on my new motherbord (ASUS ROG Strix B450-F Gaming) didn't succeed. I used Erase Disk and installed to /dev/nvme1n1. Installation of grub failed.

I made a bootable USB with dd and that installation went OK.

One difference was that the mkusb version booted into legacy, but the dd version booted into uefi. I'm quite sure that bios was set to uefi only before a started the installation with the mkusb version.
Before I started the installation with the dd version I checked the setting in bios. It was set to legacy+uefi and I changed it to uefi only.

---

### Post by sudodus on 2019-12-26
@P-I H,

Thanks for the heads up. I want to understand what went wrong so that I can make mkusb better.

1. I guess that you made a persistent live drive with mkusb. (I am rather sure that when you **clone** with mkusb and make a live drive without persistence, the result should be identical to what is made with any other cloning method (so identical to the result when you use dd).

2. I know since before, that there can be problems to install (create an installed system) from a persistent live system made with mkusb. One such problem is that the persistent live drive can be considered a target drive. A workaround in this case is to boot the persistent live system without persistence and with 'toram', which is one of the menu options in the current version of mkusb 12.3.8 (it was introduced in [mkusb 12.3.7](https://ubuntuforums.org/showthread.php?t=1958073&page=43&p=13905175#post13905175)). 

3. What you describe seems to be another problem affecting installing from a persistent live system made with mkusb. **Please tell me which version of Ubuntu or Ubuntu family flavour that you were using**, for example Ubuntu 18.04.3 LTS or Lubuntu 19.10 or Xubuntu Focal Fossa. I will try to repeat what you were doing and provoke the same failure in order to debug it.

4. Some UEFI-BIOS systems have a setting to 'try first' in one mode that you can select, and if it fails, to try booting in the other mode. I think this happened, maybe because the persistent live drive failed somehow with the bootloader. **Can you remember if you used the default method for grub, or if you selected 'usb-pack-efi' in the settings menu of mkusb?**

---

### Post by oldfred on 2019-12-26
The setting in UEFI for either legacy or UEFI is only for your installed systems. 

If Secure Boot is off, you normally get two boot options in UEFI boot menu for Ubuntu installer. One clearly UEFI:name & other name where second one is BIOS and name is a label or brand name of flash drive.

---

### Post by P-I H on 2019-12-26
@sudodus
1. I run mkusb on Ubuntu 19.10 and used mkusb to clone the 20.04 daily iso. I thought I should get the menu version, but I got the version with the icon as shown in the instruction on page
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)


4. I used the default method.

@oldfred
The installation where I cloned the iso with **sudo dd if=/home/p-i/Downloads/focal-desktop-amd64.iso of=/dev/sdd** 
worked as expected and after restart the new installation was booted from the /boot/efi partition on the first drive /dev/nvme0n1p1.

---

### Post by sudodus on 2019-12-26
@P-I H,

Which icon? Did you mean the second one of these attached pictures?

In that case it indicates that it booted in BIOS mode.

[s]Just to be sure: Are we talking about the installed Focal Fossa system in the case when you used mkusb to create a persistent live system with Ubuntu Focal Fossa in the USB drive and used that to install Ubuntu Focal Fossa into the nvme drive? Or am I jumping to conclusions?[/s]

Edit: If you really **cloned** with mkusb, it should create a drive that is identical to what is created by dd. Cloning means copying each byte from the iso file to the target drive without any modifications. Nothing added, nothing removed, nothing changed.

Edit 2: I have to think twice here. Sorry. I don't think that icon appears in installed systems, and not in a persistent live system created by mkusb-dus. So I think you are talking about a cloned drive, that is booting in BIOS mode.

Unless the USB pendrive hardware makes a difference, a cloned drive by mkusb and by dd should be identical and behave in the same way. mkusb uses dd under the hood when cloning. It is 'only' wrapping a safety belt around dd.

---

### Post by P-I H on 2019-12-26
The USB I booted with mkusb got the 2:nd image. It obviously booted in bios mode..
I run mkusb on Ubuntu 19.10 and on the usb was the daily iso of focal fossa. I expected to get the 1:st image, but got the 2:nd.

When I made the 2:nd usb with **sudo dd if=/home/p-i/Downloads/focal-desktop-amd64.iso of=/dev/sdd**
I used the same iso and in this case i got the 1:st image after I booted the usb.

---

### Post by sudodus on 2019-12-26
Yes, I see, and I don't understand why.

Please try again, this time with

- the same USB pendrive
- the same USB port on the computer
- the same settings in the UEFI-BIOS menu system
- **clone** from the same iso file

**You *should* get the same behaviour (booting into the same mode) both when using mkusb-dus and dd.**

**If you still get different results** I must conclude, that mkusb-dus is not cloning, when it should clone, and that is a **really serious bug**.

---

### Post by P-I H on 2019-12-26
OK, I will do this but I will use another target system /dev/sdb instead of /dev/ nvme1n1.
When I used /dev/nvme1n1 as target system it was formatted with the disk utility as a blank disk with zeroes as 2TB(GPT) and I will not do that this time. The target disk contains a focal fossa installation.

---

### Post by P-I H on 2019-12-26
The boot with the mkusb created "boot usb" worked OK. The only difference is the "blank" target disk. I will try that too.

---

### Post by sudodus on 2019-12-26
@P-I H,

I am looking forward to your test results ...

---

### Post by P-I H on 2019-12-26
The computer didn't like that the last installed disk was wiped. The only way to boot the system was from the sda drive. Have to rescue the installations.

---

### Post by P-I H on 2019-12-26
I don't think there is any problem with mkusb. I think the problem in some way is related to the wiped disk and that /boot/efi on /dev/nvme0n1p1 don't contain the correct information.

I have fixed the computer now.
I booted from the samsung ssd to Ubuntu 19.10 on nvme0n1 and made sudo grub-install /dev/nvme0n1 and sudo update-grub. Then booted to Ubuntu 20.04 on nvme1n1 and made
sudo grub-install /dev/nvme1n1 and sudo update-grub and the computer behaves as after the installation Ubuntu 20.04 on the smaller of the nvme drives.
However the computer has switched id:s on the nvme disks.

---

### Post by sudodus on 2019-12-26
Sorry for that extra trouble. I have done things like that too.

For that reason I avoid adventures in my main computer, and play with a secondary computer, dedicated for testing. Sometimes I can borrow a rather new computer, but my adventures take place in my own (older) computers most of the time.

---

### Post by sudodus on 2019-12-26
> **P-I H said:**
> I don't think there is any problem with mkusb. I think the problem in some way is related to the wiped disk and that /boot/efi on /dev/nvme0n1p1 don't contain the correct information.

I have fixed the computer now.
I booted from the samsung ssd to Ubuntu 19.10 on nvme0n1 and made sudo grub-install /dev/nvme0n1 and sudo update-grub. Then booted to Ubuntu 20.04 on nvme1n1 and made
sudo grub-install /dev/nvme1n1 and sudo update-grub and the computer behaves as after the installation Ubuntu 20.04 on the smaller of the nvme drives.
However the computer has switched id:s on the nvme disks.

I'm glad that you could fix the computer rather quickly, and I'm glad that there seems to be no problem with mkusb. Anyway, it is important to keep the eyes open and look into what might be a problem. So thanks a lot for this effort :-)

---

### Post by him610 on 2020-01-19
> Screw for M.2 Socket comes with motherboard. Contact company that produces your motherboard.
or search in your favorite browser for > where to obtain Screw for M.2 Socket

---

