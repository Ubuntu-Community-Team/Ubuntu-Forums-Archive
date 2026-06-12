---
title: "Raspberry Pi 4B - 22.04 LTS First Boot Fails! HW Error"
date: 2022-08-10
forum: Server Platforms
---

### Post by tbnrc on 2022-08-10
Hi,

I'm trying to get Ubuntu Server 22.04 LTS onto my RPI 3 B+.

I'm using the RPI Imager to flash the SD card, and I select Ubuntu Server 22.04 arm64 (tried armhf as well, same problem). 

On first boot, it immediately goes into emergency mode. I can't get out of it.


I think there's a problem with the image because 20.04 LTS boots fine.

Any ideas?

UPDATE:

For some reason when flashing certain microSD cards the FAT partition isn't levelled "system-boot". This was causing the PIs to go into emergency mode. Verified on PI2, PI3 and PI3B+.

However, the PI4B (2GB) I'm using will not boot from images for arm64, server or desktop.

Server images result in the following error right at power up and the system hangs:

```
raspberrypi-clk soc:firmware:clocks: Failed to change fw-clk-arm frequency: -110
raspberrypi-clk soc:firmware:clocks: Failed to change fw-clk-arm frequency: -110
bcm2708_fb soc:fb: Failed to allocate GPU framebuffer (-110)
bcm2708_fb_pan_display(0,0) returns=-110
 
```

Desktop image just loads a black screen and stays there forever.

---

### Post by tbnrc on 2022-08-10
[COLOR=#000000]Hi,[/COLOR]

[COLOR=#000000]I'm trying to get Ubuntu Server 22.04 LTS onto my RPI 3 B+.[/COLOR]

[COLOR=#000000]I'm using the RPI Imager to flash the SD card, and I select Ubuntu Server 22.04 arm64 (tried armhf as well, same problem).[/COLOR]

[COLOR=#000000]On first boot, it immediately goes into emergency mode. I can't get out of it.[/COLOR]


[COLOR=#000000]I think there's a problem with the image because 20.04 LTS boots fine.[/COLOR]

[COLOR=#000000]Any ideas?[/COLOR]

---

### Post by TheFu on 2022-08-10
Did you validate the image?  sha256sum would be best.  The place where you got the image download should have the signatures available.

With a Pi v3, seems the 32-bit version is recommended because only 1 GB of RAM is possible, even though that Pi version has a 64-bit CPU.

I've never tried to run Ubuntu on any Pi.  I find most Ubuntu's bloated, including the server, so a purpose built pi distro for the specific purpose I need is what I use.

---

### Post by tbnrc on 2022-08-10
The RPI Imager validates the image after flashing (it's the official installer supplied by the RPI org that gets an RPI specific image from Canonical). Both the 32-bit and 64-bit images go to emergency mode for 22.04.

Just following the official instructions: [https://ubuntu.com/tutorials/how-to-install-ubuntu-on-your-raspberry-pi#1-overview]("https://ubuntu.com/tutorials/how-to-install-ubuntu-desktop-on-raspberry-pi-4#1-overview")

I flashed 64-bit 20.04 and it worked fine, but I really want 22.04.

I actually tried downloading the full arm64 installer from the Ubuntu website, but I can't run the installer since the RPI doesn't boot from USB.

---

### Post by oldfred on 2022-08-10
Please do not post same question more than once.
We all are volunteers and need to know what else has ready been suggested to avoid duplicate effort.

---

### Post by tbnrc on 2022-08-10
Sorry, I just didn't know which forum was more appropriate.

---

### Post by slickymaster on 2022-08-10
*Thread moved to **Server Platforms**.*

---

### Post by tbnrc on 2022-08-10
So I downloaded the manual install image. SHA256 was good. Flashed SD card using balenaEtcher. It still booted directly into emergency mode.

Attached is the output of journalctl -xb while in emergency mode. If there's a more knowledgeable pair of eyes that can see something that would help.

[ATTACH]290828[/ATTACH]

---

### Post by tbnrc on 2022-08-11
Soooooo, I've got my hands on a RPI 4 now... and none of the 22.04 LTS images work at all. They won't even boot. Not the server, or the desktop version. Just a black screen. Server version will say "cannot adjust soc clock speed (error -110)" or something?

---

### Post by TheFu on 2022-08-11
That tells me something in your process or shared hardware isn't working.  There are lots of people using r-pi v4 with Ubuntu over the last few months.

When I need to push a pi image onto a microSD, I use 'cp'.  Then at first boot, the installation loads into RAM and reformats the storage as needed while it asks a few setup questions.  r-pi OS installs aren't like x86 Ubuntu installs.

Any chance that your 3b+ or 4 pis had their firmware modified to only boot from USB or SATA devices?  I understand once that is done, the microSD boot won't work.

---

### Post by tbnrc on 2022-08-11
Sorry, what's 'cp'?

No, the PIs aren't modified in any way. They've always been operated from SD card. Raspbian and Manjaro (both installed with the rpi-installer) both flash and work fine on the SD card I have. Only Ubuntu won't work.

---

### Post by TheFu on 2022-08-11
> **tbnrc said:**
> Sorry, what's 'cp'?

No, the PIs aren't modified in any way. They've always been operated from SD card. Raspbian and Manjaro (both installed with the rpi-installer) both flash and work fine on the SD card I have. Only Ubuntu won't work.

'man cp' will explain.  Just point the target at the microSD device file.

---

### Post by tbnrc on 2022-08-11
Oh, you're just copying the image contents to the SD card?

---

### Post by TheFu on 2022-08-11
> **tbnrc said:**
> Oh, you're just copying the image contents to the SD card?

Sorta, but cp'ing them to the microSD device directly, not to a directory.  That's all those fancy tools do, if they work correctly.  I just skip the middleman and all the bugs that can be introduced.  You can use dd or ddrescue if you like that better, but everyone on Linux should know how to use cp, right?

---

### Post by tbnrc on 2022-08-11
The problem with that is I don't have another linux box to use cp other than the raspberry itself, lol. I could cp the card with manjaro or something and see what happens I guess.

In the meantime, I used Raspbian to update the firmware on both the 3B+ and the 4 on a hunch. Then I stuck Ubuntu on the card again. 

If I stick the card in the 4, nothing happens.  It shows the following line and just stays there forever:
```
[3.811677] raspberrypi-clk soc:firmware:clocks: Failed to change fw-clk-arm frequency: -110
```

If I stick it in the 3B+, it boots into emergency mode.

/facedesk

---

### Post by TheFu on 2022-08-11
You only have 1 computer and it isn't running Linux or BSD?  /s 
We live in completely different worlds. ;)

When I google that error, nothing directly related comes up, but it seems there's a firmware setting to be tweaked. I've barely needed to touch the hardware stuff in my Pis.  Just to force a resolution and for some paid vcodec licenses.

BTW, if raspian boots, you can use cp to copy the image to a different microSD.  Any Unix-like OS can be used, but you'll need to be 100% what the specific storage device filename is or it could be a really bad day - wiping the running OS or worse - is a common mistake.

---

### Post by tbnrc on 2022-08-11
Correct. Lol.  I'm going to cp it with Manjaro in a minute. I don't care if I wipe out the OS:D I've been wiping it for days trying to troubleshoot this thing.

---

### Post by tbnrc on 2022-08-12
Nope. Doesn't matter how I flash the SD card or if I do it from linux or windows.

Pi 3B+ always boots into emergency mode. Pi 4 doesn't boot at all.

I can't be the only person this is happening to.  I've got 2 seperate PIs (going to get some PI 2s from home later), but this is ridiculous. It's literally only Ubuntu doing this.

---

### Post by TheFu on 2022-08-12
> **tbnrc said:**
> Correct. Lol.  I'm going to cp it with Manjaro in a minute. I don't care if I wipe out the OS:D I've been wiping it for days trying to troubleshoot this thing.

What was the exact, cp command used and from which hardware?
On x86 Linux, it would be something like:
```
sudo cp /path/to/something/ubuntu.iso  /dev/sdZ
```

Note that I'm pointing at the entire device, not a partition. No need to pre-partition or format anything.  Just be 100% certain that /dev/sdZ points at the microSD you want to use.  BTW, you may have noticed that I always say microSD and you seem to always say SDcard.  Those aren't the same, physically and usually SDHC are slower. There is a minimal speed needed (documented in the PI stuff). In the olden Pi days, the SDHC needed to be slow enough, but with a r-pi v2 and later, there's a minimal speed.  It would be hard not to get one that is fast enough the last 5 yrs, but some people use 10 yr old stuff (I do).  Just be certain it is class 10 or faster.

---

### Post by tbnrc on 2022-08-12
Yes, that's right. I found a x86 ubuntu box in another lab. sudo cp ubuntu_blabla_arm64-raspi.iso /dev/sdc1 (from the file location).

I also used sudo dd if=ubuntu_blabla_arm64-raspi.iso of=/dev/sdc1 bs=1M

It's a Class U1/C10 microSDHC that was previously running Raspbian on the RPI 3B+.

Once flashed, I can read the contents of the mSD fine. 256MB main partition with "writable" second partition containing the folder structure. I can set up the wifi credentials in the network-config file. It all reads fine on the x86 system after flashing.

I've also found a third RPI 3, same problem on that one as well. Boots right into emergency mode.

---

### Post by TheFu on 2022-08-12
```
sudo cp ubuntu_blabla_arm64-raspi.iso /dev/sdc[s]1[/s]
```
is wrong!

```
sudo cp ubuntu_blabla_arm64-raspi.iso /dev/sdc
```
would be correct, assuming that sdc is correct at all.  It could be and would make sense, but I'm not there to validate it.  I typically use **dmesg -w** to watch new storage connected and see the device name given.

There's a huge difference between writing to the entire device and writing to a partition.

---

### Post by tbnrc on 2022-08-12
Just retried as you indicated to make sure (verified sdc was correct). Same results. 3/3B+ boot to emergency. 4 does not boot at all.

There doesn't appear to be any difference with the flashing methods. Even tried another SD card. No joy.

---

### Post by TheFu on 2022-08-12
They wouldn't appear to be different, but it is vastly different in where data is written.  None of the prior attempts that used sdc1 was ever going to work. None of them.

Something else is wrong. At least that has been eliminated.

---

### Post by tbnrc on 2022-08-12
Sure, and I retried that. I'm just saying RPI Imager, balenaEtcher, cp and dd flashes all fail in the same way on every rpi I have my hands on, on multiple SD cards. How is that possible if there's nothing wrong with the image?

The only image I've been able to boot is 20.04 on the 3 and 3B+, but not on the 4.

The 22.04 image fails on every device.

---

### Post by TheFu on 2022-08-13
> **tbnrc said:**
> Sure, and I retried that. I'm just saying RPI Imager, balenaEtcher, cp and dd flashes all fail in the same way on every rpi I have my hands on, on multiple SD cards. How is that possible if there's nothing wrong with the image?

The only image I've been able to boot is 20.04 on the 3 and 3B+, but not on the 4.

The 22.04 image fails on every device.

Ok, I've freed up a r-pi v2.
Pulled the ubuntu-22.04.1-preinstalled-server-armhf+raspi.img.xz and sha256sums down, 
Validated the sha256sums match ... with 
```
    $ egrep $(sha256sum ubuntu-22.04.1-*raspi.img.xz)  ubuntu-22.04.1-*6
```
decompressed the image:
```
   $ unxz ubuntu-22.04.1-*img.xz
```
and forced it onto a 32G microSD card:
```
   $ sudo cp ubuntu-22.04.1-preinstalled-server-armhf+raspi.img /dev/sdc
   $ sync
```

Verifyed that there is full file system in the target microSD:
```
$ sudo fdisk -l /dev/sdc
Disk /dev/sdc: 29.8 GiB, 32010928128 bytes, 62521344 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 0x34ec70f0

Device     Boot  Start     End Sectors  Size Id Type
/dev/sdc1  *      2048  526335  524288  256M  c W95 FAT32 (LBA)
/dev/sdc2       526336 7196707 6670372  3.2G 83 Linux
```
Looks fine to me.
Gotta love wildcards and tab-completion. If you don't know how to use either, learn. No need to type very much.

Now I just need a way to hook the pi up to some external stuff and boot it.  That will be the hardest part, I suspect. I have a KVM switch, but no open slots.  Seems this is gonna be harder than I thought.  I'll need an hour, probably.  Was doing my weekly patching too, so that needs some attention.

---

### Post by TheFu on 2022-08-13
Ok, found a microUSB power thingy, finally.

Booted.  It came up.
Was provided with a login prompt
username: ubuntu
password: ubuntu

Was forced to change the password immediately and was provided with a login prompt.  I forget to hook up networking, so the device didn't get an IP. My mistake.  Connected a CAT6 cable that feeds into a GigE switch and enabled the port. The network came up without any action on my part. I use ssh and have already exchanged keys for the normal OS that device runs (that is hooked into all sorts of network things here through ssh connections), so I'm not willing to do that.

Anyway, 22.04.1 is up and working on my raspberry pi v2. Let me go to that system and run a few reports as proof. Claims aren't exactly useful. Proof is better. Seems there are some upgrades needed, including a new kernel.  I'd forgotten how slow a pi v2 is without a custom OS version tailored for the HW.  This one typically runs OSMC with a music server - not GUI stuff.

The new kernel is taking much longer to install than I'd have thought. It has been 10 minutes already and that 1 package is showing 70%.  Patching all my other systems, over 10, takes 10 minutes ... before doing all the reboot stuff, if needed.  I need to reboot some of my VM servers, which this desktop runs inside (and this browser), so look back in 30 min for some HW/OS reports that I'll run on the r-pi.

Also, I'm seeing a number of undervoltage warnings that I don't see with OSMC. I use a powered 10W USB hub for this Pi, but think each USB port is limited to only 2A.

I'm at a loss for what could be happening on your side.

---

### Post by TheFu on 2022-08-13
Ok, had to deal with a few crappy 22.04 things before posting the report.  Some are just my personal issue with things that don't work on my network correctly like systemd-resolved which fails to work for far too many people, including me.  Plus, I'd forgot to purge nano. Can't stand that editor - heck, it isn't really even worthy of that name.
Onto the proof:
```
$ inxi -Fxxz
System:
  Kernel: 5.15.0-1013-raspi armv7l bits: 32 compiler: gcc v: 11.2.0 Console: tty 1
    Distro: Ubuntu 22.04.1 LTS (Jammy Jellyfish)
Machine:
  Type: ARM System: Raspberry Pi 2 Model B Rev 1.1 details: BCM2835 rev: a01041 serial: <filter>
CPU:
  Info: quad core model: ARMv7 v7l variant: cortex-a7 bits: 32 type: MCP arch: v7l rev: 5
  Speed (MHz): avg: 600 min/max: 600/900 cores: 1: 600 2: 600 3: 600 4: 600 bogomips: 230
  Features: Use -f option to see features
Graphics:
  Device-1: bcm2708-fb driver: bcm2708_fb v: kernel bus-ID: N/A chip-ID: brcm:soc
  Device-2: bcm2835-hdmi driver: N/A bus-ID: N/A chip-ID: brcm:soc
  Display: server: No display server data found. Headless machine? tty: 240x75
  Message: GL data unavailable in console. Try -G --display
Audio:
  Device-1: bcm2835-audio driver: bcm2835_audio bus-ID: N/A chip-ID: brcm:bcm2835_audio
  Device-2: bcm2835-hdmi driver: N/A bus-ID: N/A chip-ID: brcm:soc
  Device-3: C-Media Audio Adapter (Unitek Y-247A) type: USB
    driver: cmedia_hs100b,snd-usb-audio,usbhid bus-ID: 1-1.3.3:11 chip-ID: 0d8c:0014
  Sound Server-1: ALSA v: k5.15.0-1013-raspi running: yes
Network:
  Device-1: bcm2835-sdhci driver: N/A port: N/A bus-ID: N/A chip-ID: brcm:soc
  IF: eth0 state: up speed: 100 Mbps duplex: full mac: <filter>
  Device-2: Microchip (formerly SMSC) SMSC9512/9514 Fast Ethernet Adapter type: USB
    driver: smsc95xx bus-ID: 1-1.1:3 chip-ID: 0424:ec00
  IF: eth0 state: up speed: 100 Mbps duplex: full mac: <filter>
Drives:
  Local Storage: total: 29.81 GiB used: 2.8 GiB (9.4%)
  ID-1: /dev/mmcblk0 model: JB1RT size: 29.81 GiB serial: <filter>
Partition:
  ID-1: / size: 29.03 GiB used: 2.67 GiB (9.2%) fs: ext4 dev: /dev/mmcblk0p2
Swap:
  Alert: No swap data was found.
Sensors:
  System Temperatures: cpu: 48.7 C mobo: N/A
  Fan Speeds (RPM): N/A
Info:
  Processes: 131 Uptime: 11m Memory: 993.8 MiB used: 226.9 MiB (22.8%) gpu: 76 MiB Init: systemd
  v: 249 runlevel: 5 Compilers: gcc: N/A Packages: 687 apt: 683 snap: 4 Shell: Bash v: 5.1.16
  running-in: tty 1 inxi: 3.3.13

```

It's a r-pi v2.  Yawn. Running Ubuntu Server 22.04.1.

I suspect that showing your commands would have quickly pointed out the issue. I do see a few things that experienced people would "just know" that could cause problems to someone new to Unix.

---

### Post by tbnrc on 2022-08-15
Picked up an RPI 2 from home.  I'm now working with a 2, a 3, a 3B+ and  4B. Basically the whole product line.

Verifying the images with sha256. In this case I'm using CertUtil on Windows with the command:
```
CertUtil -hashfile ubuntu_22.04.1_*version*.img.xz sha256
```

Desktop: 680c2c1770b53d90e825fd9a40178f605af47acfff681ad5f68d38094d1c32eb (good)
Server armhf: 342fb581ce11208c26f35675acafdc3d56ac2838b1297a508e602f88606903f1 (good)
Server arm64: 5d0661eef1a0b89358159f3849c8f291be2305e5fe85b7a16811719e6e8ad5d1 (good)

Moving over to Linux and verifying nothing went wrong copying them over with a USB stick:

```
echo "342fb581ce11208c26f35675acafdc3d56ac2838b1297a508e602f88606903f1 *ubuntu-22.04.1-preinstalled-server-armhf+raspi.img.xz" | shasum -a 256 --check
echo "5d0661eef1a0b89358159f3849c8f291be2305e5fe85b7a16811719e6e8ad5d1 *ubuntu-22.04.1-preinstalled-server-arm64+raspi.img.xz" | shasum -a 256 --check
echo "680c2c1770b53d90e825fd9a40178f605af47acfff681ad5f68d38094d1c32eb *ubuntu-22.04.1-preinstalled-desktop-arm64+raspi.img.xz" | shasum -a 256 --check

```[COLOR=#000000][FONT=&amp]

Still good.

Decompressing the images:

[/FONT][/COLOR]```
[COLOR=#000000][FONT=&amp]$ unxz ubuntu-22.04.1-*img.xz[/FONT][/COLOR]
```[COLOR=#000000][FONT=&amp]

Writing image to 32GB Class 10 mSD:

[/FONT][/COLOR]```
$ [COLOR=#000000][FONT=&amp]sudo cp ubuntu-22.04.1-preinstalled-server-armhf+raspi.img /dev/sdc
$ sudo sync[/FONT][/COLOR]
```[COLOR=#000000][FONT=&amp]

[/FONT][/COLOR][COLOR=#000000]Verified that there is full file system in the target microSD:

[/COLOR]```
[COLOR=#000000][FONT=&amp]sudo fdisk -l /dev/sdc
[/FONT][/COLOR][COLOR=#000000]Disk /dev/sdc: 29.74 GiB, 31914983424 bytes, 62333952 sectors
Disk model: MassStorageClass
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 0x34ec70f0

Device      Boot     Start     End       Sectors     Size     Id    Type
/dev/sdc1   *        2048      526335    524288      256M     c     W95 FAT32 (LBA)
/dev/sdc2            526336    7196707   6670372     3.2G     83    Linux[/COLOR]
```[COLOR=#000000]

Testing mSD card in the following:

PI2: Boots to BusyBox
PI3: Boots to BusyBox
PI3B+: Fails to boot
PI4B: Fails to boot

This is a worse result than last week [/COLOR]:(. Checked again with a 16GB Class 4 mSD card. Same result for all units.

Checking the arm64 image next, but the PI2 can't run that one by default.

---

### Post by TheFu on 2022-08-15
Class 4 is too slow.  Use a class 10 MicroSD or faster.  There were documented issues with slow cards not working.

---

### Post by tbnrc on 2022-08-15
Yeah, I have 3 cards, Class 4, Class 10, and I tested a U3 last week.

The Class 4 was in the PI2, which makes sense. Otherwise I'm on the Class 10. The Class 4 is just stupid slow to load.

arm64 version:

PI2: N/A
PI3: Boots to emergency mode
PI3B+: Boots to emergency mode
PI4B: Fails to boot, "cannot adjust soc clk".

---

### Post by tbnrc on 2022-08-15
There seems to be an error while booting up the PI4 with the armhf image before booting to emergency mode.

[TIMEOUT] /dev/disk/by-label/system-boot

Followed by a handful of DEPENDENCY failures.

Seems like the issue causing the emergency mode, but how is this happening on a fresh flash?

Looking at the image in linux:

/writable/etc/fstab contains the following:
```
LABEL=writable / ext4 discard,errors=remount-ro 0 1
LABEL=system-boot /boot/firmware vfat defaults 0 1
```

/writable/boot/firmware/cmdline.txt contains the following:
```
net.ifnames=0 dwc_otg.lpm_enable=0 console=ttyAMA0,115200 console=tty1 root=/dev/mmcblk0p2 rootfstype=ext4 elevator=deadline rootwait
```

If I try to
```
mount -a
```
in emergency mode. It says cannot mount: /boot/firmware: Can't find LABEL=system-boot.

---

### Post by TheFu on 2022-08-15
I'm out of ideas.  Looks like some other people will likely see this thread and hopefully, they will have some ideas.

Are you re-imaging the OS after each attempt? I ask because at first boot, Ubuntu seems to attempt to resize the file systems, and if that is where the fault lies, taking it to another Pi immediately won't work.

Since I don't have a r-pi v4 (too expensive for me), someone else will need to run that down.  I planned to get one, but the first runs had that USBc flaw, so I was waiting for the 2nd run and they sold out of the lower-end versions, which is all I'd need/want.

---

### Post by tbnrc on 2022-08-16
Ok. I've figured out (most) of the problem.


I got another Class 10 16GB SD Card from home.  For some reason, when I flash an image (both armhf and arm64) onto the 16GB card, the two volumes are labelled "writable" and "system-boot", but when I flash an image onto a 32GB card, the two volumes are labelled "writable" and "268MB Volume". Why? Something about this image doesn't like 3/4 of my SD cards.


So what I did for the 32GB card was to clear the FAT32 volume label, and assigned the label "system-boot" manually using mlabel.


This fixed the emergency mode boot for the PI2, PI3 and PI3B+. Yay!


However, even with the correct volume labels set, a first boot on a PI4 fails with arm64 server images. It throws the error below and the system hangs. 


```
raspberrypi-clk soc:firmware:clocks: Failed to change fw-clk-arm frequency: -110
raspberrypi-clk soc:firmware:clocks: Failed to change fw-clk-arm frequency: -110
bcm2708_fb soc:fb: Failed to allocate GPU framebuffer (-110)
bcm2708_fb_pan_display(0,0) returns=-110
 
```

arm64 desktop image throws no errors, and just stays on a black screen forever.

---

