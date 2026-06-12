---
title: "Bonobo Extreme (bonx6)"
date: 2012-12-13
forum: System76 Support
---

### Post by jaylittle on 2012-12-13
Alright so as I imagine most of you already know, System 76 has put out a new addition to their laptop line:  [The Bonobo Extreme (bonx6).](https://www.system76.com/laptops/model/bonx6) After spending the last few weeks drooling over this device and comparing it to my current panp9, I have decided to bite the bullet and buy one after watching [this video review on it](http://www.youtube.com/watch?feature=player_detailpage&v=faR4NiSGbtg#t=2855s). Anyway the machine looks amazing.  Even though my panp9 has been extremely awesome, I've decided that since my wife's Sony laptop is getting a bit long in the tooth, the time to upgrade has come and she'll be inheriting my panp9 as a result in addition to being transitioned over to Linux from Windows.

The primary motivation for buying this laptop over my existing panp9 was the inclusion of the Nvidia GPU. Ironically enough that was also my biggest motivation for not buying it.  The reason being is that after suffering with the Nvidia Linux driver for years on various machines I have come to dislike it a great deal.  That dislike was reaffirmed when I realized how well the Intel HD4000 in my panp9 worked in Linux. So giving the bonx6 a chance is actually a bit of a stretch for me. Prior to buying it I asked the S76 Sales Reps a few questions concerning issues I've had with the Nvidia Linux drivers in the past (the biggest two being the inability of the Nvidia driver to detect ACPI state changes without switching to a virtual console and back and the fact that I could never seem to add custom resolutions to the Nvidia driver config and get them to work - something the Intel driver allows to happen easily using the standard xrandr tool) and they said that these issues were not issues on the bonx6 and also said that the Nvidia driver has improved a great deal over the last six months. Maybe Linus' middle finger did the trick, eh?

Anyway - hopefully I'll have the machine by the first of the new year. It will take me some time to get it setup as I don't use Ubuntu and since this will be my first UEFI machine (yes it uses UEFI instead of the age old BIOS according to the review I linke above) transitioning my existing Arch Linux install is probably going to be tricky.  When I get it, I will be sure to detail and document my experiences in this thread.

So that brings me to my question:  Has anybody else purchased this machine?  If so, what do you think?  I look forward to hearing your thoughts on the matter.

---

### Post by bdensmore on 2012-12-13
I just got my Bonobo Extreme delivered a couple of hours ago. Haven't had a chance to use it yet but will post back with my thoughts on it once I get some use out of it.

I will say, It's a big machine, which is fine with me because I don't really travel much with a laptop. If you're looking for portability, this isn't the laptop for you though.

---

### Post by abeowitz on 2012-12-17
I got mine about a week ago.  So far, no major problems, but haven't dug deep.

I dumped Ubuntu/Unity since I loathe the interface, switched to Cinnarch.  In other words, no problems installing alternative Linux flavors.  So far, everything just works.  :)  But haven't tried the keyboard lights or fingerprint reader at all.

Got the Nvidia 670, just one, and figured I'd be able to upgrade later if I needed.  I'm upgrading from an Asus N73JQ, which had Nvidia 425M, so if that could handle Portal2, the 670GTX should do well.  (Wikipedia specs suggest its about 5X faster.)

Nvidia drivers work well, though dual screen can be a bit tricky sometimes.  Running full screen games or even Heaven benchmark, it will choose a screen on its own based on the resolution, rather than the main screen.  So, upon exit, I have to use Nvidia settings to switch back.  Likely a Cinnamon problem.

My Asus N73JQ was just as big, so I'm used to this size laptop.

USB 3.0 ports work well, unlike my Asus. :/

SATA-III ports work well, I get full speed out of my SSD drives.  :)  Drive slots can be a bit snug.

I do wish the mSATA port was SATA-III, but that's a limitation of the Intel HM77 chipset, not the Bonobo.  Anyone know if it's possible to software select which ports are SATA-III enabled?

Only problem I have is eSATA is only 1.5GBps, have not figured out why.  Seems consistent across other distros, yet I KNOW I have 3Gbps devices.  (Same for my N73JQ recently.  Might be a kernel regression?)

---

### Post by jaylittle on 2012-12-17
Abe, did you have to do anything special in regards to the bootloader on the machine?  As I understand it, the laptop uses UEFI instead of the age old BIOS.  I'm actually looking to transition the existing arch install I have on the panp9 to the bonx6 when it arrives so if you have anything to add that would be most appreciated.  A quick google shows me that Cinnarch comes with UEFI support out of the box.  That means it might prove to be a viable option if I choose to reinstall rather than transition the existing install.  I'm hoping to avoid that if at all possible though.

Also, how does the GPU react when you unplug the laptop and plug it back in?  Is it downclocking and upclocking as it should?  Traditionally I've had problems with that sort of thing with Nvidia drivers (typically resolved by switching to a virtual console and back to X).  In addition, have you had any luck setting up custom resolutions for the screen (mostly 16x9 stuff like 1024x576 for instance)?

---

### Post by abeowitz on 2012-12-18
Jaylittle,

I was able to move the drive from my Asus to the Bonobo and boot without any modifications or problems.  :)  (Both Nvidia)

The UEFI/BIOS supports traditionally partitioned disks and boot loaders like GRUB.

Have not tried UEFI boot/partitions on the Bonobo, but I do have a disk I can try.  :)

The BIOS has an option for Windows8 UEFI mode.  Guess what this does... ;)


Will check Nvidia/CPU power behavior tomorrow (Tues).

---

### Post by jaylittle on 2012-12-18
That's good to know.  This means moving to the new machine will be quite a bit easier than I anticipated as all I will need to do is switch video drivers :)  Thanks for the details Abe - they are most appreciated!

---

### Post by abeowitz on 2012-12-18
In the Nvidia-settings app, resolution of the LCD is limited to 1920x1080, however, if I force Heaven benchmark to 1024x576 it works, but is a bit stretched vertically bordered by black on left & right.

Not sure how to measure the power settings.  The Nvidia settings "Power Mizer" shows:

[[IMG]http://img109.imageshack.us/img109/3592/screenshotfrom201212181.png[/IMG]](http://imageshack.us/photo/my-images/109/screenshotfrom201212181.png/)

It says "Battery" even though it's plugged in.

It doesn't change if I unplug the laptop.

So, if you know a better way to check, lemme know.  :)

---

### Post by abeowitz on 2012-12-18
FWIW:

```
00:00.0 Host bridge: Intel Corporation 3rd Gen Core processor DRAM Controller (rev 09)
00:01.0 PCI bridge: Intel Corporation Xeon E3-1200 v2/3rd Gen Core processor PCI Express Root Port (rev 09)
00:01.1 PCI bridge: Intel Corporation Xeon E3-1200 v2/3rd Gen Core processor PCI Express Root Port (rev 09)
00:14.0 USB controller: Intel Corporation 7 Series/C210 Series Chipset Family USB xHCI Host Controller (rev 04)
00:16.0 Communication controller: Intel Corporation 7 Series/C210 Series Chipset Family MEI Controller #1 (rev 04)
00:1a.0 USB controller: Intel Corporation 7 Series/C210 Series Chipset Family USB Enhanced Host Controller #2 (rev 04)
00:1b.0 Audio device: Intel Corporation 7 Series/C210 Series Chipset Family High Definition Audio Controller (rev 04)
00:1c.0 PCI bridge: Intel Corporation 7 Series/C210 Series Chipset Family PCI Express Root Port 1 (rev c4)
00:1c.1 PCI bridge: Intel Corporation 7 Series/C210 Series Chipset Family PCI Express Root Port 2 (rev c4)
00:1c.2 PCI bridge: Intel Corporation 7 Series/C210 Series Chipset Family PCI Express Root Port 3 (rev c4)
00:1d.0 USB controller: Intel Corporation 7 Series/C210 Series Chipset Family USB Enhanced Host Controller #1 (rev 04)
00:1f.0 ISA bridge: Intel Corporation HM77 Express Chipset LPC Controller (rev 04)
00:1f.2 SATA controller: Intel Corporation 7 Series Chipset Family 6-port SATA Controller [AHCI mode] (rev 04)
00:1f.3 SMBus: Intel Corporation 7 Series/C210 Series Chipset Family SMBus Controller (rev 04)
01:00.0 VGA compatible controller: NVIDIA Corporation Device 11a1 (rev a1)
01:00.1 Audio device: NVIDIA Corporation GK104 HDMI Audio Controller (rev a1)
04:00.0 Unassigned class [ff00]: Realtek Semiconductor Co., Ltd. Device 5289 (rev 01)
04:00.2 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 0a)
05:00.0 Network controller: Intel Corporation Centrino Advanced-N 6235 (rev 24)
```
```

Module                  Size  Used by
fuse                   69213  3 
wacom                  42610  0 
uvcvideo               72788  0 
videobuf2_vmalloc       2469  1 uvcvideo
videobuf2_memops        2283  1 videobuf2_vmalloc
videobuf2_core         24073  1 uvcvideo
videodev              100860  2 uvcvideo,videobuf2_core
media                  10406  2 uvcvideo,videodev
joydev                  9992  0 
hid_logitech_dj        10190  0 
usb_storage            47385  1 
uas                    11120  0 
snd_hda_codec_hdmi     24529  1 
hid_generic             1114  0 
coretemp                6071  0 
kvm_intel             124718  0 
kvm                   374014  1 kvm_intel
crc32c_intel            1988  0 
ghash_clmulni_intel     4278  0 
aesni_intel            42082  0 
aes_x86_64              7556  1 aesni_intel
aes_generic            26139  2 aesni_intel,aes_x86_64
ablk_helper             1973  1 aesni_intel
cryptd                  8742  3 ghash_clmulni_intel,aesni_intel,ablk_helper
usbhid                 37036  1 hid_logitech_dj
arc4                    2040  2 
btrfs                 718583  2 
hid                    85974  3 hid_generic,usbhid,hid_logitech_dj
crc32c                  1769  1 
libcrc32c               1003  1 btrfs
zlib_deflate           20437  1 btrfs
iwldvm                171052  0 
mac80211              426350  1 iwldvm
nvidia               9340873  55 
iTCO_wdt                5256  0 
mxm_wmi                 1468  0 
iTCO_vendor_support     1930  1 iTCO_wdt
snd_hda_codec_realtek    61420  1 
microcode              12346  0 
evdev                  10267  17 
psmouse                71952  0 
serio_raw               4690  0 
pcspkr                  1900  0 
i2c_i801                9572  0 
snd_hda_intel          26181  5 
snd_hda_codec          98034  3 snd_hda_codec_realtek,snd_hda_codec_hdmi,snd_hda_intel
snd_hwdep               6429  1 snd_hda_codec
snd_pcm                75735  3 snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel
snd_page_alloc          7218  2 snd_pcm,snd_hda_intel
video                  11277  0 
acpi_cpufreq            5934  0 
iwlwifi               125182  1 iwldvm
mperf                   1300  1 acpi_cpufreq
r8169                  56872  0 
snd_timer              18935  1 snd_pcm
mii                     4092  1 r8169
snd                    60189  17 snd_hda_codec_realtek,snd_hwdep,snd_timer,snd_hda_codec_hdmi,snd_pcm,snd_hda_codec,snd_hda_intel
i2c_core               20708  3 i2c_i801,nvidia,videodev
lpc_ich                10610  0 
cfg80211              177109  3 iwlwifi,mac80211,iwldvm
ac                      2537  0 
soundcore               5443  1 snd
thermal                 8120  0 
mei                    32666  0 
rfkill                 15605  1 cfg80211
battery                 6774  0 
wmi                     8380  1 mxm_wmi
button                  4663  0 
processor              26856  1 acpi_cpufreq
loop                   18161  0 
vfat                   10120  0 
fat                    48403  1 vfat
ext4                  440435  2 
crc16                   1360  1 ext4
jbd2                   78802  1 ext4
mbcache                 6027  1 ext4
ehci_hcd               41817  0 
xhci_hcd               87083  0 
usbcore               150472  7 uas,wacom,uvcvideo,usb_storage,ehci_hcd,usbhid,xhci_hcd
sr_mod                 14824  0 
usb_common               955  1 usbcore
cdrom                  35521  1 sr_mod
sd_mod                 29560  7 
ahci                   21361  3 
libahci                20024  1 ahci
libata                167757  2 ahci,libahci
scsi_mod              133434  5 uas,usb_storage,libata,sd_mod,sr_mod

```

---

### Post by jaylittle on 2012-12-18
It looks like you are on the right portion of the Nvidia setup screen.  When you switch from AC to the battery, in theory the performance level should change (this behavior can vary based upon xorg config settings however).  When you switch from the battery to the AC it should change back.  If it doesn't change in either event, try switching to a virtual console and switching back.  If it changes then, it means that Nvidia still hasn't got their act together in regards to power management.  If it doesn't change even then, then it may mean that their power management has actually improved to the point where you have to run some sort of 3d application in order to force it to upclock. Not too shocking as I'm prepared to live with it.  Still a tiny bit disappointing though.

Edit:  Nevermind - the question is already answered.  The fact it doesn't update the power source in the window when you change it pretty much says it all.  Try switching to a virtual console and back and I bet you'll see it update :) <sigh> Oh well - I was prepared for this.  No biggie.

---

### Post by jaylittle on 2012-12-18
According to [the Arch wiki entry on Nvidia](https://wiki.archlinux.org/index.php/NVIDIA), the driver can detect the power source but only if the acpid daemon is installed and set to run on startup.  It might be worth trying to install that and see if it makes the driver more responsive to power state changes.  I doubt it, as I believe I've gone down that road before.... but it's worth a shot.  If you don't want to bother, don't worry too much.  I got the shipping notification on mine and it will be here on Friday. w00t!

---

### Post by abeowitz on 2012-12-18
Well, I installed the ACPId and laptop tools, but no luck, it still says 'battery' while on AC.

Kernel 3.8 is supposed to have better power management:

[http://www.phoronix.com/scan.php?page=news_item&px=MTI1MzQ](http://www.phoronix.com/scan.php?page=news_item&px=MTI1MzQ)

I get big laptops more as a portable desktop than battery life, so I don't pay attention to power settings much.

If you figure it out after you get it, please post.  Thanks.

It's a good laptop, I think you'll be happy with it.

---

### Post by jaylittle on 2012-12-18
Yeah I'll look it over the weekend and share anything I find.  I think the first thing I will do is check and see if it works in the Ubuntu install it comes with as that will give a good indication as to whether or not it can work.

Truthfully - it's not an issue with the kernel though - its Nvidia's drivers.  That's one of the things that was so great about my panp9 - it used hardware that had open source drivers for everything and the Intel HD4000 had none of these issues.  Of course it wasn't nearly as performant as the Nvidia card either :)  Yeah I'm definitely looking forward to the laptop.  Things like this can be worked around with little real effort, so they aren't a big deal in the grand scheme of things.

Thanks for the info.  It was most appreciated!

---

### Post by jaylittle on 2012-12-21
I received my bonx6 today.  Notes:

[1] Nvidia power state detection didn't work correctly in the out of the box Ubuntu install.

[2] I have no freaking clue how to configure the nvidia driver to use resolutions lower than 1920x1080.  I've been screwing with metamodes for two hours pulling my hair out and its a frigging nightmare.  All I want to do is to make the display use 1600x900 instead of 1920x1080.  Is this really so much to ask?

Apparently it is.

---

### Post by isantop on 2012-12-21
> **jaylittle said:**
> I received my bonx6 today.  Notes:

[1] Nvidia power state detection didn't work correctly in the out of the box Ubuntu install.

[2] I have no freaking clue how to configure the nvidia driver to use resolutions lower than 1920x1080.  I've been screwing with metamodes for two hours pulling my hair out and its a frigging nightmare.  All I want to do is to make the display use 1600x900 instead of 1920x1080.  Is this really so much to ask?

Apparently it is.

You should be able to use the built-in Displays tool in System Settings to turn the resolution down.

---

### Post by jaylittle on 2012-12-21
The only option it presents we with is 1920x1080.  That behavior was the same on Ubuntu as it was on Arch Linux.

---

### Post by Ayanzo on 2012-12-21
Hmm... I was hoping for a professional serval; is this still in the works?

In addition, does the bonobo extreme have full copper cooling like the serval did?

---

### Post by abeowitz on 2012-12-21
Ayanzo,

The current Bonobo Extreme is based on the Clevo P379EM/Sager NP9370, and there are a number of internal images and reviews on the net.  :)

[http://www.lpc-digital.com/sager-np9370-features.html](http://www.lpc-digital.com/sager-np9370-features.html)

---

### Post by jaylittle on 2012-12-21
So I've moved on from the resolution issue.  The screen is more than large enough to make using 1920x1080 more than bearable so I'm cutting my losses.  Ironically using the IncludeImplicitMetaModes nvidia driver option gives games access to all of the display modes I want to use on the desktop.  Experimenting with setting a custom metamode as a default seems to create a situation in which my desktop pans back and forth.

Some more thoughts:

This machine is truly beautiful.  Well built, high quality.

I'm still getting used to the touchpad but managed to get right click functionality configured in a way that I ought to be able to live with it.

Love the keyboard backlighting!

I've seen netbooks smaller than the power brick.  On a side note, I would love it if the portion of the cord that goes from the brick to the laptop itself was a bit longer.

Transitioning my arch install was extremely simple.  All I had to do was install the nvidia drivers after removing the intel ones and then recreating my xorg.conf file with the nvidia-xconfig utility.

---

### Post by abeowitz on 2012-12-22
To get the SDCard slot working on Arch:

```
wget https://bugs.launchpad.net/bugs/971876/+attachment/2991730/+files/rts_bpp.tar.bz2 
tar jxf rts_bpp.tar.bz2
cd rts_bpp
make 
make install
depmod
modprobe rts_bpp
dmesg 
```

**dmesg** should show similar to the following:

```
[11345.682579] Initializing Realtek PCIE storage driver...
[11345.682608] --- 14:32:38 ---
[11345.682791] Resource length: 0x10000
[11345.682935] Original address: 0xf7200000, remapped address: 0xffffc900064a0000
[11345.682941] pci->irq = 18
[11345.682943] rtsx_acquire_irq: chip->msi_en = 0, pci->irq = 18
[11345.713810] scsi8 : SCSI emulation for Realtek BarossaPlusPlus card reader
[11345.714217] rts_bpp: waiting for device to settle before scanning
[11346.712463] scsi 8:0:0:0: Direct-Access     Generic- xD/SD/M.S.       1.00 PQ: 0 ANSI: 0 CCS
[11346.713091] Bad LUN (0:1)
[11346.713244] Bad target number (1:0)
[11346.713371] Bad target number (2:0)
[11346.713532] Bad target number (3:0)
[11346.713620] sd 8:0:0:0: [sdk] Attached SCSI removable disk
[11346.713647] Bad target number (4:0)
[11346.713748] Bad target number (5:0)
[11346.713887] Bad target number (6:0)
[11346.713979] Bad target number (7:0)
[11346.714016] rts_bpp: device scan complete
[11353.115872] sd 8:0:0:0: [sdk] 31275008 512-byte logical blocks: (16.0 GB/14.9 GiB)
[11353.116099] sd 8:0:0:0: [sdk] Cache data unavailable
[11353.116105] sd 8:0:0:0: [sdk] Assuming drive cache: write through
[11353.116548] sd 8:0:0:0: [sdk] Cache data unavailable
[11353.116553] sd 8:0:0:0: [sdk] Assuming drive cache: write through
[11353.117549]  sdk: sdk1

```

Note that I couldn't get it to compile at first.  I tried this:

**yaourt -S rts5229**

And after that, the above instructions worked.

Now you can remove it.

**yaourt -R rts5229**

---

### Post by jaylittle on 2012-12-30
So I've spent some time with the laptop and it's almost perfect except... this damn Clickpad.  Sell a laptop with real mouse buttons next time please.  This clickpad can't handle the stress put on it by gaming. Clicking down will cause it to stick from time to time and sometimes it REALLY stays stuck (which causes the OS to register it as you constantly clicking).  If I could switch out the clickpad for the trackpad on my panp9, this would be the perfect machine.  As it stands now, I'm now remapping the mouse buttons to keyboard buttons in games to keep from ripping my hair out.

Note: I'm going to attempt working around this by disabling Clickpad functionality completely and relying upon tap for what I need.  *gulp*

---

### Post by jaylittle on 2012-12-30
Abe,

I found using the package for the driver in AUR to be a bit easier:

[https://aur.archlinux.org/packages/dkms-rts_bpp/](https://aur.archlinux.org/packages/dkms-rts_bpp/)

:)

---

### Post by robjective on 2012-12-30
> **jaylittle said:**
> So I've spent some time with the laptop and it's almost perfect except... this damn Clickpad.  Sell a laptop with real mouse buttons next time please.  This clickpad can't handle the stress put on it by gaming. Clicking down will cause it to stick from time to time and sometimes it REALLY stays stuck (which causes the OS to register it as you constantly clicking).  If I could switch out the clickpad for the trackpad on my panp9, this would be the perfect machine.  As it stands now, I'm now remapping the mouse buttons to keyboard buttons in games to keep from ripping my hair out.

Note: I'm going to attempt working around this by disabling Clickpad functionality completely and relying upon tap for what I need.  *gulp*

I saw your previous post that you had gotten it configured more to your liking and I was coming back today to ask what you had done and saw this.  I agree with you.  I can only get right-clicks to register about 1 in 8 times.  I can work around the problem when web-browsing by doing a ctrl-click for a new window, but right-clicking a file for properties or to rename is frustrating.  I hope it's a software bug that can be addressed.

I'm also having trouble with the touchpad turning off while typing.  I have the box ticked, but my cursor wanders from the box that should have focus.

One last thing...I hope someone comes up with a cord to extend the lead from the power brick another two feet.

Other than that, machine is a very solid build and love the volume of the audio output on this thing.

---

### Post by jaylittle on 2013-01-01
> **robjective said:**
> I saw your previous post that you had gotten it configured more to your liking and I was coming back today to ask what you had done and saw this.  I agree with you.  I can only get right-clicks to register about 1 in 8 times.  I can work around the problem when web-browsing by doing a ctrl-click for a new window, but right-clicking a file for properties or to rename is frustrating.  I hope it's a software bug that can be addressed.

I'm also having trouble with the touchpad turning off while typing.  I have the box ticked, but my cursor wanders from the box that should have focus.

One last thing...I hope someone comes up with a cord to extend the lead from the power brick another two feet.

Other than that, machine is a very solid build and love the volume of the audio output on this thing.
I agree on both the length of the cord and the audio volume.  As for the clicking - I'm still having issues with it and its getting quite frustrating.  Turning off the "click" functionality of the trackpad seems to be almost impossible.  It's mostly turned off after I run the following shell script:
```
#!/bin/bash

synclient ClickPad=0
synclient ClickFinger1=0
synclient ClickFinger2=0
synclient ClickFinger3=0
synclient TapButton1=1
synclient TapButton2=3
synclient TapButton3=2
synclient RTCornerButton=0
synclient RBCornerButton=0
synclient LTCornerButton=0
synclient LBCornerButton=0
```
Hope this helps... note:  This will enable tap to click along with two and three finger taps for right and middle clicks respectively. Your desktop environment may override some of these settings from time to time, namely the TapButton ones.  So be sure you have the DE setup to emulate those settings.  All DEs that I've tried don't seem to even acknowledge much less modify any of the click settings.

---

### Post by Ayanzo on 2013-01-25
I just got my bonobo extreme for my company to do some development, but so far I'm not that impressed with the out of box experience. My serval pro 7 'just worked' while my bonobo extreme required configuration just to get my extra drives (secondary and caddy) configured. I thought by going sys76 we were taken care of, especially if my manager is forking over more than 2k for the configuration?

The major issue I have is that some laser USB mice and bluetooth connected mice appear to not work out of the box.

This is a basic functionality, lsusb shows the device is enumerated, but apparently it's not properly handled.

```
<6>[ 6048.708266] usb 3-2: new full-speed USB device number 28 using xhci_hcd
<6>[ 6048.726866] usb 3-2: New USB device found, idVendor=046d, idProduct=c52b
<6>[ 6048.726873] usb 3-2: New USB device strings: Mfr=1, Product=2, SerialNumber=0
<6>[ 6048.726876] usb 3-2: Product: USB Receiver
<6>[ 6048.726879] usb 3-2: Manufacturer: Logitech
<6>[ 6048.732239] logitech-djreceiver 0003:046D:C52B.0007: hiddev0,hidraw0: USB HID v1.11 Device [Logitech USB Receiver] on usb-0000:00:14.0-2/input2
<3>[ 6048.732526] logitech-djreceiver 0003:046D:C52B.0007: logi_dj_probe:logi_dj_recv_query_paired_devices error:-32
<4>[ 6048.732698] logitech-djreceiver: probe of 0003:046D:C52B.0007 failed with error -32
```

on my Serval (which I updated to 12.10)


```

<6>[21902.037715] usb 2-1.2: new full-speed USB device number 19 using ehci_hcd
<6>[21902.133230] usb 2-1.2: New USB device found, idVendor=046d, idProduct=c52b
<6>[21902.133244] usb 2-1.2: New USB device strings: Mfr=1, Product=2, SerialNumber=0
<6>[21902.133252] usb 2-1.2: Product: USB Receiver
<6>[21902.133261] usb 2-1.2: Manufacturer: Logitech
<6>[21902.141279] logitech-djreceiver 0003:046D:C52B.001D: hiddev0,hidraw0: USB HID v1.11 Device [Logitech USB Receiver] on usb-0000:00:1d.0-1.2/input2
<6>[21902.144649] input: Logitech Unifying Device. Wireless PID:1025 as /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.2/2-1.2:1.2/0003:046D:C52B.001D/input/input20
<6>[21902.144957] logitech-djdevice 0003:046D:C52B.001E: input,hidraw1: USB HID v1.11 Mouse [Logitech Unifying Device. Wireless PID:1025] on usb-0000:00:1d.0-1.2:1

```

What's really strange was after an afternoon of configuring (plus setting up build environments). I decided to plug in a normal, old, laser logitech mouse, found it working, and proceeded to plug in the problem bluetooth-usb mouse. Lo and behold it works? UPDATE: upon rebooting, it breaks again, plugging in the old laser mouse and re-plugging in the blue-tooth unifier mouse does not re-create the 'magic' solution. It also appears that all of my logitech unifier based devices don't work either.

old laser logitech:
```
<6>[ 3164.210402] input: Logitech USB Optical Mouse as /devices/pci0000:00/0000:00:14.0/usb3/3-2/3-2:1.0/input/input15
<6>[ 3164.210803] hid-generic 0003:046D:C018.001A: input,hidraw0: USB HID v1.11 Mouse [Logitech USB Optical Mouse] on usb-0000:00:14.0-2/input0
<6>[ 3170.907663] usb 3-2: USB disconnect, device number 11

```

I have no issues with the hardware, i'm just lamenting on the service that's provided as opposed to me just buying the hardware and putting ubuntu on it. Side note, it appears that fprint is not installed by default.

---

### Post by isantop on 2013-01-28
> **Ayanzo said:**
> I just got my bonobo extreme for my company to do some development, but so far I'm not that impressed with the out of box experience. My serval pro 7 'just worked' while my bonobo extreme required configuration just to get my extra drives (secondary and caddy) configured. I thought by going sys76 we were taken care of, especially if my manager is forking over more than 2k for the configuration?

We don't configure secondary drives by default becuase of the large vareity of ways that customers want them configured. That said, I'll forward your comments on for future consideration.

> **Ayanzo said:**
> What's really strange was after an afternoon of configuring (plus setting up build environments). I decided to plug in a normal, old, laser logitech mouse, found it working, and proceeded to plug in the problem bluetooth-usb mouse. Lo and behold it works? UPDATE: upon rebooting, it breaks again, plugging in the old laser mouse and re-plugging in the blue-tooth unifier mouse does not re-create the 'magic' solution. It also appears that all of my logitech unifier based devices don't work either.

Are you using a Unifying receiver? Try a different port. We've had a couple of reports of Unifying receivers not working on USB 3 ports, so try the USB 2 port.

---

### Post by abeowitz on 2013-01-28
Now that you've mentioned it, I've also had trouble with my Logitech wireles trackball with unifying receiver.  It had trouble through an external USB 3.0 hub as well (SIIG 6port + card reader).

It behaves like a weak radio link, but is pysically close enough.  Moving the unifying receiver to another port seemed to work well.

When I get a chance, I'll try to find a pattern to it.

---

### Post by Nerdfest on 2013-02-03
I find the front left corner of my Bonobo 6 gets very hot, but not a lot of hot air gets blown out the back by the fans. Is this normal behaviour?

---

### Post by paulbuede on 2013-02-04
I have been really enjoying my bonx6.  I also upgraded from a Serval Pro.  This thing is super fast.  It handles Linux Steam nicely and all.  I went to install some games like Alien Arena, which would not work, but then today I saw there was an update, so I updated and it works now.  I think the Alien Arena was a DGA mouse thing (after some googling).  I have been trying to get Enemy Territory running, tried doing it manually and got no sound and no mouse support.  Then I checked synaptic and of course it was there, so I installed from there, now i have sound but the mouse hasn't improved.  Seems some of these SDL games have issues with DGA mouse drives or something?  I have no idea what I am talking about and probably poorly paraphrasing... anyway, can anyone replicate this?  I get to the first screen after launching et, and it wants me to put in my name and enable punkbuster etc etc, as soon as I move the mouse it slides down to the right and I can't get it back...

---

### Post by Ayanzo on 2013-02-07
> **Nerdfest said:**
> I find the front left corner of my Bonobo 6 gets very hot, but not a lot of hot air gets blown out the back by the fans. Is this normal behaviour?


Depends on what's hogging your CPU. I run full builds that use all my memory and 100% of all 4 cpus (8 hyper threaded).


In respect to the usb mouse issue. Yes, this is usb3.0 releated. Using a 2.0 hub on a 3.0 port or 2.0 port will yeild no problems.

---

