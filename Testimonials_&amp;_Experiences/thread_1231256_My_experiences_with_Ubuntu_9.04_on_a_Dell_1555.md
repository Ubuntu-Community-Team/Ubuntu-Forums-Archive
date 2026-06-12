---
title: "My experiences with Ubuntu 9.04 on a Dell 1555"
date: 2009-08-04
forum: Testimonials &amp; Experiences
---

### Post by internaut on 2009-08-04
Hi there!
I have my new Dell 1555 for a week now running with Ubuntu 9.04 and wanted to share my experiences, because not everything worked completely out of the box and some problems still exist...

At first, here's my hardware configuration:

[LIST]
[*]Intel® Core 2 Duo-Prozessor P8600 (2,40 GHz, 3 MB, 1.066 MHz)
[*]4.096 MB 800 MHz Dual-Channel DDR2 SDRAM [2 x 2.048]
[*]512 MB ATI Mobility RADEON HD 4570
[*]320-GB-Serial ATA-Harddrive (7.200 1/min)
[*]Intel WiFi Link 5100-Mini (802.11 a/b/g/n, 1 x 2)
[*]15.6in Widescreen Full High Definition (1920x1080) WLED with TrueLife
[/LIST]

The first and most complicated thing was the display driver: After a fresh install and a apt-get update / upgrade and reboot, I could install the ATI driver from the Ubuntu repository, but I encountered as many graphic glitches so the system was unusable! After uninstalling the old driver, I installed the original ATI driver from [http://support.amd.com/us/gpudownload/Pages/index.aspx](http://support.amd.com/us/gpudownload/Pages/index.aspx) (I selected the HD 4550 series, as the 4570 is not listed yet) and installed it (sudo sh ./ati-driver...). After that, there were no glitches any more, but I encountered the problem described here with slow window resizing: [https://bugs.launchpad.net/ubuntu/+source/fglrx-installer/+bug/351186](https://bugs.launchpad.net/ubuntu/+source/fglrx-installer/+bug/351186) I installed the patch from [https://edge.launchpad.net/~ubuntu-x-swat/+archive/xserver-no-backfill](https://edge.launchpad.net/~ubuntu-x-swat/+archive/xserver-no-backfill) (**you have to reinstall the ATI driver strictly afterwarts, or the X server won't start!**). Now compiz and everything is finally working very fast. The only thing is, that the ATI driver is quite energy consuming and fans are running like hell... The energy saving stuff doesn't really work (see brightness control problem).

The second problem was, that the sound didn't work. This did the trick: [http://ubuntuforums.org/showpost.php?p=7372426&postcount=6](http://ubuntuforums.org/showpost.php?p=7372426&postcount=6) The sound comes out "quite quiet". Putting the "front" slider to the max in the Volume Control helped a bit...

A still remaining problem is, that the brightness control settings not work, or only randomly work... I added "blacklist video" to /etc/modprobe.d/blacklist.conf and it seemed like it worked, but a few reboots after that, it didn't again. I don't know what else to do...

Strangely, the card ready only worked the second time I used it... now it's ok.

Flash didn't work with Opera 9.6. I tried everything but then switched to Opera 10 beta everything works well and stable.

All in all, only the display driver thing was really annoying, the sound was fixed very easily and everything else (WLAN, external drives, second monitor, media keys) works out-of-the-box.

---

### Post by TKFT.44 on 2009-08-08
I just wanted to say thank you for posting this. It's amazing that we have the nearly the exact same computer specifications. (What color is yours? I got black. :) )

Anyway, the part about the patch for window resizing finally solved all my problems! I'll start using Ubuntu much more often than I used to!

Thanks very much.

---

### Post by headflux on 2009-08-09
HI Internaut,

Thanks for sharing your experiences.  I've just bought exactly the same Lappy as you (in shiny black casing), and whilst I didn't have the video card issues, I did have the no sound problem, which your post helped me fix.

Absolutely loving my new Dell

Thanks again

---

### Post by usrlinux on 2009-08-10
Oh! 
Even I bought the same book DELL 1555 (500 GB HD) and rest same as yours.....Faced the same issues on sound and brightness.... Fixed the sound issue...
But still consulting Prof Google to sort out brightness issue....

Further in addition to appending 
options snd-hda-intel model=dell-m6in /etc/modprobe.d/alsa-base file I changed all the drivers to 'ALSA' in system-->preferences-->sound

Restart

Typing
$alsamixer 
 
in 'Terminal' will initiate the alsamixer and you can change the volumes to any intensity you want......
Hope this will help

Please let me know if you are through with the brightness issues.....

DELL 1555
P8600, ATI Radeon HD4570, 4GB Mem, 500GB 5500rpm SATA, Duel boot Ubuntu/Vista

---

### Post by ravisghosh on 2009-08-13
Exactly same config here..

I'm yet to fix the graphic card.

I could not get wireless working. Whenever I try to connect, it asks for WPA password and on providing it, it keeps on asking again and again. Tried wifi-radar too but of no use..

---

### Post by headflux on 2009-08-14
> **ravisghosh said:**
> Exactly same config here..

I'm yet to fix the graphic card.

I could not get wireless working. Whenever I try to connect, it asks for WPA password and on providing it, it keeps on asking again and again. Tried wifi-radar too but of no use..


Hi Ravisghosh, Sounds obvious but have you checked to see whether the Proprietary Wireless Driver is activated? 

SYSTEM>ADMINISTRATION>HARDWARE DRIVERS

Just a thought.

---

### Post by harry2006 on 2009-08-14
i've been using Jaunty on brand new dell 1555 for last couple of weeks and its running fine...no issues at all...almost everything worked/works out-of-the-box...and yes after installing the prop hardware drivers compiz is driving me crazy...its rocking!!!

---

### Post by ravisghosh on 2009-08-14
> **headflux said:**
> Hi Ravisghosh, Sounds obvious but have you checked to see whether the Proprietary Wireless Driver is activated? 

SYSTEM>ADMINISTRATION>HARDWARE DRIVERS

Just a thought.

After scanning, it says "No proprietary drivers are in use on this system."

I have selected the third part softwares under software sources.

---

### Post by mip on 2009-08-19
I have the same laptop. Here are a few of the issues I have encountered:

[LIST]
[*] Screen resolution is lost when I restart the laptop (resorts to 1024x768 then I need to change it to 1366x768.)
[*] No Wifi. Restricted driver installed but not detecting networks.
[*] Graphics card is "Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller" are there Proprietary drivers available for this?
[*] Very loud system beep when I shutdown the laptop.
[/LIST]

Can anyone offer me any advice?

---

### Post by ravisghosh on 2009-08-19
> **mip said:**
> 

[LIST]
[*] Very loud system beep when I shutdown the laptop.
[/LIST]


Me too getting this loud system been on shutdown.

---

### Post by Arthur_D on 2009-08-19
Loud system beep is one of the things scheduled to be fixed under the "100 Paper Cuts" program. :)

---

### Post by Blokie on 2010-01-24
I've spent much of the weekend installing Karmic onto my Dell 1555, and have had pretty good success.

I'm down to 2 issues that are annoying me, as follows:

Brightness hotkeys not working (they didn't work at first, then for a couple of hours they worked, now they're back to not working.  All of the other hotkeys work (wifi toggle, volume up/down, mute etc.)  I've tried adding acpi_osi= to grub.cfg, but no luck.

[UPDATE] Got the brightness sorted with GRUB_CMDLINE_LINUX_DEFAULT="quiet acpi_backlight=vendor" for about 30 minutes, but now the controls appear on screen and show the brightness slider going up and down, but the actual brightness doesn't change!!!

Tearing during video playback (with any and all players tried (MPlayer, VLC, XBMC).  I've got the latest drivers from the ATI site, and am also running the nobackfill xserver-xorg.

Anyone got any ideas on the 2 issues above?

---

