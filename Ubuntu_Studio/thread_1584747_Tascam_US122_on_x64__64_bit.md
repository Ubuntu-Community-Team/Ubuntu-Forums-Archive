---
title: "Tascam US122 on x64 / 64 bit"
date: 2010-09-29
forum: Ubuntu Studio
---

### Post by Ventai on 2010-09-29
Hi, 

I'm having a bit of fun trying to install my US122 with UbuntuStudio64 10.04 :)

A forum member said in a previous post that some versions of the US122 do not work with Linux. 
Going through the usual Unbuntu community installation procedure [https://help.ubuntu.com/community/TASCAM_US-122;](https://help.ubuntu.com/community/TASCAM_US-122;) I've managed to get Linux to see the Tascam interface when running '# lsusb', however am having an issue on finding the alsamixergui package.
Is anyone aware that this means that my interface *should *eventually work with Linux? 

I'd really appreciate a response if anyone knows, as I have a lot hanging on whether this will work or not. . 

I've heard of Synaptic, and am getting the feeling this may help with the search of all the required Alsa packages.
Do they need to be specific to the version of Ubuntu? I've ensured I installed all x64 versions, but wasn't really paying full attention to the version. Hence, whenever running: -

# sudo apt-get install fxload alsa-base alsa-firmware-loaders alsa-tools alsa-tools-gui alsa-utils alsamixergui alien

.. it was saying lots of packages were missing, with the latest being alsamixergui.

---

### Post by gordintoronto on 2010-09-29
Yes, use Synaptic! It's found in System/Administration. Use "Search," not "quick search." When you find what you want, such as "alsamixergui" you can right-click on it, and select "mark for installation." You can select as many programs as you want, then click on "Apply" to actually install them.

If you have never run Synaptic, the first thing to do is select Settings/Repositories, and select everything except "source code" in the first two tabs. That will get you the partner, restricted and proprietary software. Then you need to "reload".

While you're in there, get the "restricted extras."

---

### Post by P4man on 2010-09-29
I dont even know what that tascam is, but let me just say that lsusb will detect any USB device (that isnt broken), but that doesnt  mean that there are working drivers for it. 

That said, the link you gave is completely obsolete. It written for ubuntu 6.06. Those packages shouldnt be needed anymore. Im afraid Im not in to ubuntu studio or MIDI enough to help much beyond that, but perhaps enter

```
aplay -l
```

in a terminal and see if it shows up there. If it does, then you will probably be able to get it working.

---

### Post by Ventai on 2010-09-29
Hello, 

aplay -l doesn't bring anything up, maybe that means it isn't going to work, hmm...




@gordintoronto
Thanks for the tips, loads of stuff seemed to get installed...

The alsamixergui package error has gone now :) 

However, when trying to run: -

sudo fxload -s /home/andy/alsa-firmware-1.0.19/ld2-ezusb.hex -I /usr/share/alsa/firmware/usx2yloader/us122fw.ihx -D /dev/bus/usb/002/002


I get: -

/home/andy/alsa-firmware-1.0.19/ld2-ezusb.hex: unable to open for input.


Again, any tips would be great! 

Cheers

---

### Post by P4man on 2010-09-30
The default download folder has changed. Its probably not in your home folder but in Downloads.  Replace "/home/andy/alsa-f..." with /home/andy/Downloads/alsa-f..".

---

### Post by Ventai on 2010-09-30
It's def in /home/andy/...

I'm thinking of using my internal digital sound card for now, which I can see via: - 

andy@VentaHome:~/alsa-firmware-1.0.19$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC887 Analog [ALC887 Analog]
Subdevices: 1/1
Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: ALC887 Digital [ALC887 Digital]
Subdevices: 1/1
Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 3: INTEL HDMI [INTEL HDMI]
Subdevices: 1/1
Subdevice #0: subdevice #0


I'm sure it'll play at 44.1k but I really need it to output at 24bit to go into a nice converter :)

Does anybody know how I can check to see if it outputs at 24 bit?

---

### Post by gordintoronto on 2010-09-30
I would be astonished if it output 24-bit. A 24-bit DAC costs more than $0.99....   For 1000000 00000000 00000000 to be the right distance from 0111111 11111111 11111111 means the high-order resistor is accurate to one-eight-millionth. (Yes, I intentionally made the first byte just 7 bits.)

What source material do you have which is 24-bit? Is there some reason you think you can hear a difference between 16-bit and 24-bit? My ears have never been *that* good.

---

### Post by Ventai on 2010-10-01
From what I understand 16bit audio is up-sampled to 24bit, and sounds more 'complete' - lending to an advantage of mixing in 24bit. .

---

### Post by P4man on 2010-10-01
You need 24 bit (arguably even 32 bit) if you are mixing.
For playback, AFAIK its useless. You are going to need a very highend amplifier, headphones (or audio set and an acoustic room) and a trainer ear for there to be a chance to hear a difference, and even then I wouldnt bet on it.

---

### Post by Ventai on 2010-10-01
A/B it - it's certainly audible. .

---

### Post by webusr1 on 2010-10-01
I've got Ubuntu Studio 10.04 wiht ASLA 1.0.21 which is much newer software load than all the work-arounds I see on getting the TASCAN US 122 working.

 uname -a
Linux ubuntustudio 2.6.32-25-preempt #44-Ubuntu SMP PREEMPT Fri Sep 17 22:21:55 UTC 2010 x86_64 GNU/Linux

cat /proc/asound/version 
Advanced Linux Sound Architecture Driver Version 1.0.21.

sudo lsusb
Bus 002 Device 004: ID 046e:555b Behavior Tech. Computer Corp. 
Bus 002 Device 003: ID 0557:2213 ATEN International Co., Ltd 
Bus 002 Device 002: ID 0557:8021 ATEN International Co., Ltd 
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 004: ID 0aec:3260 Neodio Technologies Corp. 7-in-1 Card Reader
**[COLOR=Blue]Bus 001 Device 002: ID 0644:8021 TEAC Corp. [/COLOR]**
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


My new TASCAM US-122mkII doesn't work either... I just purchased TASCAM US-122mkII because I found several folks that got them to work and it's much cheaper than the M Audio products. see these links...

TASCAM US-122L (Thought that might work, but looks old) [http://wiki.briata.org/doku.php?id=testing_us122l_under_linux](http://wiki.briata.org/doku.php?id=testing_us122l_under_linux)

This link states that loading  usx2yloader will make it work.
[http://ubuntuforums.org/showthread.php?t=1360736](http://ubuntuforums.org/showthread.php?t=1360736)

When I type "usx2yloader" Synaptic Packager Manager I two software packages:
alsa-firmware-loaders
alsa-firmware

I will try installing both packages nd post my results.

Also check out the info about TASCAM at the bottom of the page of the link.
[http://usb-midi-fw.sourceforge.net/](http://usb-midi-fw.sourceforge.net/)

Also see these links:
[https://help.ubuntu.com/community/TASCAM_US-122](https://help.ubuntu.com/community/TASCAM_US-122)
[http://ubuntuforums.org/showthread.php?t=431066](http://ubuntuforums.org/showthread.php?t=431066)

---

### Post by Ventai on 2010-10-02
Firstly I started to go through the following guide: -

[https://help.ubuntu.com/community/TASCAM_US-122](https://help.ubuntu.com/community/TASCAM_US-122)

There was a warning after doing setp 1: - 

# sudo apt-get install fxload alsa-base alsa-firmware-loaders alsa-tools alsa-tools-gui alsa-utils alsamixergui alien

I continued anyway. 
The issue with this guide appears to be that it doesn’t inform you about the initial packages you need to download. More about that later. 

The US122 should be plugged in before you do step 5.

When getting to step 6: -

# sudo fxload -s /path/to/ld2-ezusb.hex -I /usr/share/alsa/firmware/usx2yloader/us122fw.ihx -D /dev/bus/usb/002/003

To find out where the ld2-ezusb.hex file was downloaded type: find /home –name ‘ld2-ezusb.hex’ into the terminal, if that’s where your downloads go to. 

After running this line, the system was reporting back that the file was not available to open. At this point I started researching and it seemed I needed more packages. 

I then downloaded the following AMD64 (64 bit for Intel or AMD) packages: -

[http://packages.ubuntu.com/dapper/amd64/fxload/download](http://packages.ubuntu.com/dapper/amd64/fxload/download)
[http://packages.ubuntu.com/dapper/amd64/alsa-firmware-loaders/download](http://packages.ubuntu.com/dapper/amd64/alsa-firmware-loaders/download)

[http://packages.ubuntu.com/dapper/amd64/gnome-alsamixer/download](http://packages.ubuntu.com/dapper/amd64/gnome-alsamixer/download)


I went through the whole process again but was still getting the same error.
It was suggested by gordintoronto that I use Synaptic to get any other required packages: - 


“
Yes, use Synaptic! It's found in System/Administration. Use "Search," not "quick search." When you find what you want, such as "alsamixergui" you can right-click on it, and select "mark for installation." You can select as many programs as you want, then click on "Apply" to actually install them.

If you have never run Synaptic, the first thing to do is select Settings/Repositories, and select everything except "source code" in the first two tabs. That will get you the partner, restricted and proprietary software. Then you need to "reload".

While you're in there, get the "restricted extras."

“

I did this and all initial errors went. But then the system reported  that No ‘USX2Y-compatible cards found’ after doing step 7. After the alternate line the device still didn’t start (it prob would have helped to restart the system, but I was hibernating as didn’t want to lost any of the window / terminal / web page stuff I had open) I was about to give up. 

The last thing I was gonna try was the kind suggestion from webusr1 via a posted link: -

“
Wbm

I have the Tascam US-122 and could not get it to work for both in and out in Ubuntu. I could only record in (showed up as an input device).
In Ubuntu STudio it does work for both in and out.
In both cases I installed from Synaptic usx2yloader (2 different packages)
[http://usb-midi-fw.sourceforge.net/](http://usb-midi-fw.sourceforge.net/)
Try in synaptic a search for Tascam and see if yours shows up.
I'd just install those two usx2yloader, plug in, reboot and see what happens.

“

………………… but I just pluged in the Tascam last night (don’t think I rebooted) and the damn thing worked, ha.

Anyways – thanks guys!

---

### Post by Ventai on 2010-10-02
p.s.



This was after a large automatic Linux software update

---

### Post by webusr1 on 2010-10-05
I successfully loaded packages: alsa-firmware-loaders and alsa-firmware using Synaptic Packager Manager. However, after the install I was unable to find the file 55-tascam.rules. I did some more research and I can now see that I have to create this file so I can load it with the loader software. I believe this activity is called creating rules. I found an example of this procedure using Fedora here: [http://www.astro.caltech.edu/~mcs/tascam_us122/](http://www.astro.caltech.edu/~mcs/tascam_us122/)  Scroll down to the bottom of the page and see section Configuring udev to automatically load the firmware. I was under the impression that once the alsa-firmware-loaders and alsa-firmware was installed, the Tascam US-122 would work, but now I understand that the firmware has to be loaded to make it work.   ALSO, I have discovered that I purchased the TASCAM US-122mkII which is different from the TASCAM US-122 and TASCM US-122L. So, my new US-122mkII may not work at all since all info on the net is for mode US-122 and US-122L...   Ventai what model US-122 do you have?

---

### Post by webusr1 on 2010-10-05
Ventai, Here are the Binary package “alsa-firmware-loaders” for ubuntu lucid.  ALSA software loaders for specific hardware  A collection of software loaders for specific hardware:  .   cspctl - Sound Blaster 16 ASP/CSP control program   hdsploader - firmware loader for the RME Hammerfall DSP cards   mixartloader - firmware loader for Digigram's miXart board sound drivers   pcxhrloader - firmware loader for Digigram pcxhr compatible soundcards   sscape_ctl - SoundScape control utility and firmware loader   usx2yloader - firmware loader for Tascam USX2Y USB soundcards   vxloader - firmware loader for Digigram VX soundcards  [https://launchpad.net/ubuntu/lucid/+package/alsa-firmware-loaders](https://launchpad.net/ubuntu/lucid/+package/alsa-firmware-loaders)  Then there's the source: [http://www.alsa-project.org/main/index.php/Download](http://www.alsa-project.org/main/index.php/Download)

---

### Post by Ventai on 2010-10-06
Hello, 

Well, I guess it must be the original US122, as I understand the MkII doesn't work, as far as I know. 

Serial# 0143776

Not sure how else I can check. I think it may be the old one, I bought it 2nd hand and the guy said he'd had it a while . .

---

### Post by webusr1 on 2010-10-07
I've got the new one (us-122 mkII), but I'm still gonna work on it this weekend. I found the usbsnoop software on sourceforge that allows logging of the USB data, so I may load windoze XP with the tascam drivers and snoop the USB port and post the usb data log on web. The author on this web page: [http://www.pps.jussieu.fr/~smimram/tascam/]("http://www.pps.jussieu.fr/%7Esmimram/tascam/")  displays his output from usbsnoop for his us122. I will ask there and start there with my output. Hopefully I'll get lucky and make it work in Ubuntu Studio...

Thanks!

---

### Post by Ventai on 2010-10-07
Good luck with that Sir!

---

