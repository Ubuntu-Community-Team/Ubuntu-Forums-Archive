---
title: "boot from IMSM mdadm container array"
date: 2012-02-20
forum: Server Platforms
---

### Post by dubsides on 2012-02-20
Alrighty, so I'm trying to boot ubuntu off a intel matrix storage manager created array, and using mdadm since intel is now supporting it, and dmraid is no longer being developed.  (want to dual boot windows7 and ubuntu off different partitions on the same array).  (additional info - I'm using ubuntu precise daily build x64 from 2 days ago, and have tried with oneric, mint 12, etc...)

I am 99% of the way there, Windows7 boots fine using root by uuid in the menu entry of grub.  The problem in ubuntu is that the normal non-imsm mdadm arrays are assembling, the container itself is assembling, but I can't get the arrays contained in the container to assemble.  I have to wait for the boot to drop to busybox, run mdadm --assemble --scan then exit in order to get booted up. (additional info - also have to run bootdegraded=true as kernel parameter in grub2)

(additional info - here's the weird part -> if I run mdadm assemble scan from a chrooted environment where the arrays aren't assembled on boot, it assembles all of the arrays including the ones in the container, but for some reason the arrays in the container aren't being assembled when auto assembly happens at boot)

There is [one thread I've been able to find (here)]("http://ubuntuforums.org/showthread.php?t=1786916"), that describes this but it seems to imply that his situation was only because he was using a non ubuntu source for mdadm.

His solution was to add a script to init.d.  Is that necessary?  Does anyone know how to do a script that would work?

Is a potential factor that I'm updating initramfs using "-u" and not "-k all -u"?

So questions are:  should current versions allow mdadm to assemble imsm container arrays on boot?
and if so, what steps do I need to take to get the rest of the way there?

Thanks!!!

---

### Post by MAFoElffen on 2012-02-20
> **dubsides said:**
> Alrighty, so I'm trying to boot ubuntu off a intel matrix storage manager created array, and using mdadm since intel is now supporting it, and dmraid is no longer being developed.  (want to dual boot windows7 and ubuntu off different partitions on the same array).  (additional info - I'm using ubuntu precise daily build x64 from 2 days ago, and have tried with oneric, mint 12, etc...)

I am 99% of the way there, Windows7 boots fine using root by uuid in the menu entry of grub.  The problem in ubuntu is that the normal non-imsm mdadm arrays are assembling, the container itself is assembling, but I can't get the arrays contained in the container to assemble.  I have to wait for the boot to drop to busybox, run mdadm --assemble --scan then exit in order to get booted up. (additional info - also have to run bootdegraded=true as kernel parameter in grub2)

(additional info - here's the weird part -> if I run mdadm assemble scan from a chrooted environment where the arrays aren't assembled on boot, it assembles all of the arrays including the ones in the container, but for some reason the arrays in the container aren't being assembled when auto assembly happens at boot)

There is [one thread I've been able to find (here)]("http://ubuntuforums.org/showthread.php?t=1786916"), that describes this but it seems to imply that his situation was only because he was using a non ubuntu source for mdadm.

His solution was to add a script to init.d.  Is that necessary?  Does anyone know how to do a script that would work?

Is a potential factor that I'm updating initramfs using "-u" and not "-k all -u"?

So questions are:  should current versions allow mdadm to assemble imsm container arrays on boot?
and if so, what steps do I need to take to get the rest of the way there?

Thanks!!!
I'm no expert on IMSM.

Yes. IMSM seems to be a cha;;enge. I personally do software and hardware RAID's.  Have installed Intel Matrix Storage RAIDs on customers. 

Frustrating some times. With the one's I've installed, I updated the BIOS and hoped for the best.

Booting on RAID... On my own, where I had time to cut it apart and play with it... If I had more that 6 drives in an Array, then. there seems to be a timer during bootup, where if rime exceed, it failed.  I added " --verbose " to the boot options which slowed the bootup process long enough let it assemble the array.   

With hardware RAID the same. I had to change the spinup delay to least and to spinup more drives at a time. Funny on both the previous is that from the commandline, they came right up(!?!)

The other fix for both (on mine) was to limit the amount of drives to each array. That may have an affect to what is happening with you or...

On Intel Storage Matrix RAIDs, again, make sure the BIOS is up to date. There seems there might be another problem... And I see some IMSM buzz also affecting SUSE, Red Hat, Fedora, Gentoo, etc. Historically Intel's Intel fake raid support was for dmraid and not with using mdadm. dmraid is no longer supported, so Intel shifted to mdadm... (Adjustment period?)

I see work on the Linux Kernel Dev List to try to make this work better, especially this from last August, on this particular issue:
[http://www.spinics.net/lists/raid/msg34783.html](http://www.spinics.net/lists/raid/msg34783.html)
[http://permalink.gmane.org/gmane.linux.raid/35013](http://permalink.gmane.org/gmane.linux.raid/35013)

That boxes with mdadm/isw had some data bits/flags being checked during that bootup process, that in dmraid meant something, but not the same meaning in mdadm... <-- Was preventing the system from booting. I'm thinking that those patches were being submitted last August... Maybe Linux Kernel 3.2 or 3.3?

---

### Post by MAFoElffen on 2012-02-20
<<Double Post>>
...And this post was mirrored to my previous? Weird! Sorry

---

### Post by dubsides on 2012-02-21
I'm not trying to pollute this forum, but was thinking maybe server people would have better knowledge of how to do this.

I'm attempting with an up to date x64 precise alpha installation. [(mdadm 3.2.3-2ubuntu1 package details)]("http://packages.ubuntu.com/precise/mdadm")

Basically the issue is that the arrays in the imsm container will not assemble during boot.  The non imsm arrays and the container itself assemble fine before dropping to busybox, but not the single array I have in the container.

I have to run ```
mdadm --assemble --scan
``` when the boot drops to busybox in order to assemble the array, then exit and it boots fine.

I have searched everywhere I can think to look including [(the linux raid email list)]("http://news.gmane.org/gmane.linux.raid"), but can't find an answer.  I saw some info for gentoo and fedora about updating the kernel with genkernel and dracut, but not sure if that is relevant in ubuntu.

[(Here is my other post for reference (in installation))]("http://ubuntuforums.org/showthread.php?t=1928562"), mods feel free to do whatever you want, just looking for help,

Thanks!

will post a dmesg when i get home

---

### Post by dubsides on 2012-02-21
here is the relevant part of dmesg:

the weird thing is that the first reference I can find (and using a search function of the log) to partitions 126 & 127 (the container) is stopping them?

```
[    1.550176] mdadm: sending ioctl 800c0910 to a partition!
[    1.550212] mdadm: sending ioctl 800c0910 to a partition!
[    1.550297] mdadm: sending ioctl 1261 to a partition!
[    1.550328] mdadm: sending ioctl 1261 to a partition!
[    1.551033] mdadm: sending ioctl 800c0910 to a partition!
[    1.551065] mdadm: sending ioctl 800c0910 to a partition!
[    1.551144] mdadm: sending ioctl 1261 to a partition!
[    1.551173] mdadm: sending ioctl 1261 to a partition!
[    1.569572] mdadm: sending ioctl 1261 to a partition!
[    1.569603] mdadm: sending ioctl 1261 to a partition!
[    1.572035] usb 3-1: new low-speed USB device number 2 using uhci_hcd
[    1.572386] md: bind<sdb2>
[    1.575310] md: bind<sdb3>
[    1.594810] [drm] fb mappable at 0xD0142000
[    1.594839] [drm] vram apper at 0xD0000000
[    1.594867] [drm] size 9216000
[    1.594894] [drm] fb depth is 24
[    1.594921] [drm]    pitch is 7680
[    1.594998] fbcon: radeondrmfb (fb0) is primary device
[    1.755583] md: bind<sdd3>
[    1.767336] md: raid1 personality registered for level 1
[    1.767600] bio: create slab <bio-1> at 1
[    1.767648] md/raid1:md5: active with 2 out of 2 mirrors
[    1.767663] md5: detected capacity change from 0 to 750202781696
[    1.769373] md: bind<sdd2>
[    1.770863] md/raid1:md4: active with 2 out of 2 mirrors
[    1.770878] md4: detected capacity change from 0 to 244754276352
[    1.778744]  md4: unknown partition table
[    1.780627] input: Logitech USB-PS/2 Optical Mouse as /devices/pci0000:00/0000:00:1d.1/usb3/3-1/3-1:1.0/input/input2
[    1.780718] generic-usb 0003:046D:C00E.0001: input,hidraw0: USB HID v1.10 Mouse [Logitech USB-PS/2 Optical Mouse] on usb-0000:00:1d.1-1/input0
[    1.780735] usbcore: registered new interface driver usbhid
[    1.780736] usbhid: USB HID core driver
[    1.824086] usb 1-4.1: new high-speed USB device number 5 using ehci_hcd
[    1.827668]  md5: unknown partition table
[    2.012211] Console: switching to colour frame buffer device 240x75
[    2.016399] fb0: radeondrmfb frame buffer device
[    2.016401] drm: registered panic notifier
[    2.016407] [drm] Initialized radeon 2.12.0 20080528 for 0000:04:00.0 on minor 0
[    2.184084] usb 1-4.2: new low-speed USB device number 6 using ehci_hcd
[    2.227386] md: linear personality registered for level -1
[    2.228477] md: multipath personality registered for level -4
[    2.229458] md: raid0 personality registered for level 0
[    2.231241] async_tx: api initialized (async)
[    2.284664] input: Wireless Keyboard/Mouse as /devices/pci0000:00/0000:00:1d.7/usb1/1-4/1-4.2/1-4.2:1.0/input/input3
[    2.284765] generic-usb 0003:099A:7202.0002: input,hidraw1: USB HID v1.11 Keyboard [Wireless Keyboard/Mouse] on usb-0000:00:1d.7-4.2/input0
[    2.291778] input: Wireless Keyboard/Mouse as /devices/pci0000:00/0000:00:1d.7/usb1/1-4/1-4.2/1-4.2:1.1/input/input4
[    2.291936] generic-usb 0003:099A:7202.0003: input,hiddev0,hidraw2: USB HID v1.11 Mouse [Wireless Keyboard/Mouse] on usb-0000:00:1d.7-4.2/input1
[    2.296009] raid6: int64x1   2562 MB/s
[    2.364007] raid6: int64x2   3511 MB/s
[    2.364080] usb 1-4.3: new high-speed USB device number 7 using ehci_hcd
[    2.432008] raid6: int64x4   2517 MB/s
[    2.500014] raid6: int64x8   2225 MB/s
[    2.568005] raid6: sse2x1    5462 MB/s
[    2.636010] raid6: sse2x2    6955 MB/s
[    2.704005] raid6: sse2x4    9666 MB/s
[    2.704017] raid6: using algorithm sse2x4 (9666 MB/s)
[    2.704325] xor: automatically using best checksumming function: generic_sse
[    2.724004]    generic_sse: 11877.000 MB/sec
[    2.724018] xor: using function: generic_sse (11877.000 MB/sec)
[    2.724592] md: raid6 personality registered for level 6
[    2.724610] md: raid5 personality registered for level 5
[    2.724627] md: raid4 personality registered for level 4
[    2.727771] md: raid10 personality registered for level 10

**[SIZE="2"]here is where I run mdadm --assemble --scan  (note I am not cutting anything out of dmesg here[/SIZE]**

[   32.754704] scsi_verify_blk_ioctl: 114 callbacks suppressed
[   32.754707] mdadm: sending ioctl 1261 to a partition!
[   32.754709] mdadm: sending ioctl 1261 to a partition!
[   32.806888] mdadm: sending ioctl 1261 to a partition!
[   32.806904] mdadm: sending ioctl 1261 to a partition!
[   43.289496] mdadm: sending ioctl 800c0910 to a partition!
[   43.289518] mdadm: sending ioctl 800c0910 to a partition!
[   43.289556] mdadm: sending ioctl 800c0910 to a partition!
[   43.289574] mdadm: sending ioctl 800c0910 to a partition!
[   43.289613] mdadm: sending ioctl 800c0910 to a partition!
[   43.289631] mdadm: sending ioctl 800c0910 to a partition!
[   43.289668] mdadm: sending ioctl 800c0910 to a partition!
[   43.289686] mdadm: sending ioctl 800c0910 to a partition!
[   43.289721] mdadm: sending ioctl 800c0910 to a partition!
[   43.289739] mdadm: sending ioctl 800c0910 to a partition!
[   43.290530] md: md127 stopped.
[   43.293170] md: bind<sda>
[   43.293257] md: bind<sdc>
[   43.309895] md: md126 stopped.
[   43.310026] md: bind<sdc>
[   43.310113] md: bind<sda>
[   43.310980] md/raid0:md126: md_size is 250081280 sectors.
[   43.311958] md: RAID0 configuration for md126 - 1 zone
[   43.312955] md: zone0=[sda/sdc]
[   43.313940]       zone-offset=         0KB, device-offset=         0KB, size= 125040896KB
[   43.314930] 
[   43.315987] md126: detected capacity change from 0 to 128041615360
[   43.317971]  md126: p1 p2 p3 p4
[   49.792236] scsi_verify_blk_ioctl: 232 callbacks suppressed
[   49.793287] mdadm: sending ioctl 1261 to a partition!
[   49.794349] mdadm: sending ioctl 1261 to a partition!
[   49.854444] mdadm: sending ioctl 1261 to a partition!
[   49.855501] mdadm: sending ioctl 1261 to a partition!
[   49.945812] mdadm: sending ioctl 1261 to a partition!
[   49.946876] mdadm: sending ioctl 1261 to a partition!
[   49.998213] mdadm: sending ioctl 1261 to a partition!
[   49.999243] mdadm: sending ioctl 1261 to a partition!
[   50.129851] EXT4-fs (md126p2): INFO: recovery required on readonly filesystem
[   50.130848] EXT4-fs (md126p2): write access will be enabled during recovery
[   50.174446] EXT4-fs (md126p2): recovery complete
[   50.175527] EXT4-fs (md126p2): mounted filesystem with ordered data mode. Opts: (null)
[   52.189293] udevd[612]: starting version 175
[   52.190193] Adding 2047996k swap on /dev/sdd1.  Priority:-1 extents:1 across:2047996k 
[   52.213704] lp: driver loaded but no devices found
[   52.301886] EDAC MC: Ver: 2.1.0
[   52.307639] EXT4-fs (md126p2): re-mounted. Opts: errors=remount-ro
[   52.316368] EDAC i82975x: ECC disabled on both channels.
[   52.352610] EXT4-fs (md126p3): mounted filesystem with ordered data mode. Opts: (null)
[   52.391152] EXT4-fs (md126p4): mounted filesystem with ordered data mode. Opts: (null)
```

---

### Post by dubsides on 2012-02-22
ah - ha!!!

So I decided since the last thing that happened before busybox was scripts/init-premount was being run, that I should throw a script in there, now I'm all good to go!!!!!!!  

So I ```
sudo gedit /etc/initramfs-tools/scripts/init-premount/raidplease
```

add ```
exec mdadm --assemble --scan
```

save, make it executable 

then ```
sudo update-initramfs -k all -uv
```

and it booted right up!

Yay!  /now if I can just get fglrx to let it shut down :(

---

### Post by dubsides on 2012-02-22
Sorry for the duplicates mods!

/also had to add a ```
exec sleep 1
``` to the script, cause with ssds in raid0 things were happening a little too fast, ha

---

### Post by uRock on 2012-02-22
Duplicate threads merged. Please do not create duplicate threads.

---

### Post by dubsides on 2012-03-06
Just wanted to post my steps to do it for future reference and so anyone else can use it:

(This is primarily for dual booting Windows and Ubuntu off of the same Intel fake/soft/rom raid drive, on different partitions.  I had to do this because mdadm wouldn't recognize more than one drive created by Intel Matrix Storage Manager)

!!!also, way I got this to work well was to create the (Empty) Partitions to be used for ubuntu installation during windows installation...  mdadm wasn't as happy creating partitions on imsm arrays...  (ymmv)
.
```
#boot iso from grub2, edit grub2 entry and add option &#8220;nodmraid&#8221;
#MUST have a seperate /boot partition
#terminal in live:

sudo apt-get remove dmraid
sudo apt-get install mdadm
#depending on version of mdadm, the following two commands may not be necessary
sudo mdadm --assemble --scan
sudo mdadm -I -e imsm /dev/md/imsm0
#now install ubuntu using built in installer
#you will need to change following partitions/drives depending on your specs

sudo mkdir /target/
sudo mount /dev/md126p2 /target/
sudo mount /dev/md126p4 /target/home/
sudo mount /dev/sdd4 /target/boot/
sudo mount --bind /dev/ /target/dev/
sudo mount --bind /sys/ /target/sys/
sudo mount --bind /proc/ /target/proc/
sudo chroot /target

apt-get update
apt-get install mdadm
grub-install /dev/sda
#location of mdadm.conf may depend on version being installed, doublecheck before 
#following command
mdadm --detail --scan >> /etc/mdadm/mdadm.conf
sudo nano /etc/initramfs-tools/scripts/init-premount/raidplease
#add the following
exec mdadm --assemble --scan
exec sleep 1
#writeout
sudo chmod +x /etc/initramfs-tools/scripts/init-premount/raidplease
update-initramfs -k all -uv

#following are optional dependent on whether you want to use
#a tmpfs for your tmp folder, whether you want to install fglrx(ATI)
#and whether you want to install cinnamon
sudo add-apt-repository ppa:gwendal-lebihan-dev/cinnamon-stable
sudo apt-add-repository ppa:satyajit-happy/themes
sudo apt-get install cinnamon
sudo apt-get install fglrx xvba-va-driver libva-glx1 vainfo
sudo aticonfig --initial -f
sudo nano /etc/X11/xorg.conf
#add the following before "Section 'monitor'"
Section "Extensions"
    Option    "XVideo" "Disable"
EndSection
#writeout

#make /tmp a tempfilesystem in ram:  set this up in fstab
tmpfs                   /tmp                    tmpfs   size=512m       0 0

```

---

