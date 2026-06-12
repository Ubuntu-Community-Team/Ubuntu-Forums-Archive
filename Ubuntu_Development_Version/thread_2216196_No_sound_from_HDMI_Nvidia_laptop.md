---
title: "No sound from HDMI Nvidia laptop"
date: 2014-04-10
forum: Ubuntu Development Version
---

### Post by Johan Karl Johansen on 2014-04-10
Hello.

Running 14.04 beta with all updates available

Lspci gives:
```

00:00.0 Host bridge: Intel Corporation 3rd Gen Core processor DRAM Controller (rev 09)
00:01.0 PCI bridge: Intel Corporation Xeon E3-1200 v2/3rd Gen Core processor PCI Express Root Port (rev 09)
00:02.0 VGA compatible controller: Intel Corporation 3rd Gen Core processor Graphics Controller (rev 09)
00:14.0 USB controller: Intel Corporation 7 Series/C210 Series Chipset Family USB xHCI Host Controller (rev 04)
00:16.0 Communication controller: Intel Corporation 7 Series/C210 Series Chipset Family MEI Controller #1 (rev 04)
00:1a.0 USB controller: Intel Corporation 7 Series/C210 Series Chipset Family USB Enhanced Host Controller #2 (rev 04)
00:1b.0 Audio device: Intel Corporation 7 Series/C210 Series Chipset Family High Definition Audio Controller (rev 04)
00:1c.0 PCI bridge: Intel Corporation 7 Series/C210 Series Chipset Family PCI Express Root Port 1 (rev c4)
00:1c.1 PCI bridge: Intel Corporation 7 Series/C210 Series Chipset Family PCI Express Root Port 2 (rev c4)
00:1c.3 PCI bridge: Intel Corporation 7 Series/C210 Series Chipset Family PCI Express Root Port 4 (rev c4)
00:1d.0 USB controller: Intel Corporation 7 Series/C210 Series Chipset Family USB Enhanced Host Controller #1 (rev 04)
00:1f.0 ISA bridge: Intel Corporation HM76 Express Chipset LPC Controller (rev 04)
00:1f.2 SATA controller: Intel Corporation 7 Series Chipset Family 6-port SATA Controller [AHCI mode] (rev 04)
00:1f.3 SMBus: Intel Corporation 7 Series/C210 Series Chipset Family SMBus Controller (rev 04)
01:00.0 VGA compatible controller: NVIDIA Corporation GK107M [GeForce GT 650M] (rev a1)
03:00.0 Network controller: Intel Corporation Centrino Wireless-N 2230 (rev c4)
04:00.0 Ethernet controller: Qualcomm Atheros AR8161 Gigabit Ethernet (rev 10)
jkj@JKJ-Laptop:~$ 

```

But Aplay -l gives:
```
**** List of PLAYBACK Hardware Devices ****card 0: PCH [HDA Intel PCH], device 0: ALC663 Analog [ALC663 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: PCH [HDA Intel PCH], device 1: ALC663 Digital [ALC663 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```


I have a tv connected to the hdmi and picture is showing, but i can't find any hdmi options for sound.
It's not found when running alsamixer either. only got one soundcard showing there:  HDA Intel PCH.

Any ideas on how to get sound out through HDMI, have googled this for a week now without any luck.

---

### Post by SeijiSensei on 2014-04-10
You have a "hybrid" machine with both Intel and NVIDIA graphics.  Are you sure the NVIDIA adapter is in use?  It looks like just the Intel adapter is working.  Take a look at the [the Bumblebee Project](http://bumblebee-project.org/) which is designed to facilitate hybrid machines with NVIDIA adapters.  You might also be able to disable the Intel chip in the BIOS and use only the NVIDIA adapter.

Also you should install the proprietary NVIDIA driver using the "Additional Drivers" application in Ubuntu  if you have not done so already.  The proprietary driver is likely to provide better HDMI support.

I also suggest installing a copy of **pavucontrol**.  I've found it the most convenient way to manage the multiple audio outputs on my machine.

---

### Post by Johan Karl Johansen on 2014-04-10
Well if the intel adapter is working, why do i get video through hdmi, but not sound.

The poprietary driver is in use, but i've not tried the bumblebee driver.

Pavucontrol got no listing of hdmi either.

I have no option in bios to disable the intel chip :/

The laptop is btw a Asus N76v

---

### Post by Johan Karl Johansen on 2014-04-10
Tried to install bumblebee, ended up without video through hdmi aswell, the system did not find the external monitor. purged bumblebee after and is now as far as 1 post :/

---

### Post by SeijiSensei on 2014-04-10
Can you disable the Intel chip in the BIOS and force the machine to use the NVIDIA adapter?

---

### Post by whatthefunk on 2014-04-10
Could be a pulseaudio problem.  Pulse does a miserable job of detecting active HDMI audio channels.

Fortunately, you can manually add additional audio channels to your pulse audio files.

In the file /etc/pulse/default.pa, add the bolded line:

```
### Load audio drivers statically
### (it's probably better to not load these drivers manually, but instead
### use module-udev-detect -- see below -- for doing this automatically)
#load-module module-alsa-sink
#load-module module-alsa-source device=hw:1,0
#load-module module-oss device="/dev/dsp" sink_name=output source_name=input
#load-module module-oss-mmap device="/dev/dsp" sink_name=output source_name=input
#load-module module-null-sink
#load-module module-pipe-sink
**load-module module-alsa-sink device=hw:1,7**
```

The numbers 1 and 7 refer to you card number and the device number.  [This guide](https://wiki.archlinux.org/index.php/PulseAudio/Examples#Finding_HDMI_output) shows you how to find which number combination works on your system.

Once you find the right numbers and add the line to the default.pa file, you should be able to select the added audio channel in system settings (I dont use Unity so really cant help further...sorry.)

---

### Post by Johan Karl Johansen on 2014-04-11
**[COLOR=#000000]SeijiSensei[/COLOR]**: No, i can't disable the intel chip in bios.

         [**[COLOR=#000000]whatthefunk[/COLOR]**]("http://ubuntuforums.org/member.php?u=1202558"): If  you look at the guide you showed an the listing in my first post, you can see that i have no option called HDMI.

I seem to get stuck on the same place in every guide out there.

---

### Post by QDR06VV9 on 2014-04-11
> **Johan Karl Johansen said:**
> **[COLOR=#000000]SeijiSensei[/COLOR]**: No, i can't disable the intel chip in bios.

         [**[COLOR=#000000]whatthefunk[/COLOR]**]("http://ubuntuforums.org/member.php?u=1202558"): If  you look at the guide you showed an the listing in my first post, you can see that i have no option called HDMI.

I seem to get stuck on the same place in every guide out there.
Just to clarify are you using the legacy driver Nvidia-304.?
Sorry I just found your specs.
NVIDIA® GeForce® GT 650M  with 2GB/4GB DDR3  VRAM

---

### Post by Johan Karl Johansen on 2014-04-11
I\m using nvidia-331

Edit: 304 does not get past login witout bumblebee, with bumblebee I do not find the TV at all, no video no audio.

---

### Post by Johan Karl Johansen on 2014-04-13
bump :)

---

### Post by QDR06VV9 on 2014-04-14
[**[COLOR=#000000]Johan Karl Johansen[/COLOR]**]("http://ubuntuforums.org/member.php?u=821539")
Maybe just maybe! This is worth a shot.
[http://orkultus.wordpress.com/2013/04/20/how-to-nvidia-319-12-drivers-in-ubuntu-based-systems-with-bumblebee/](http://orkultus.wordpress.com/2013/04/20/how-to-nvidia-319-12-drivers-in-ubuntu-based-systems-with-bumblebee/)

---

### Post by Johan Karl Johansen on 2014-04-14
Nope, still only video.

---

### Post by QDR06VV9 on 2014-04-14
> **Johan Karl Johansen said:**
> Nope, still only video.

Sorry I don't mean to be demeaning here but will you check and see if you using the right config.
Please open pulseaudio-volume and on the configure tab take a screen shot if you would.
Here is a snap shot of mine.

---

### Post by Johan Karl Johansen on 2014-04-15
[IMG]https://dl.dropboxusercontent.com/u/83957590/Skjermdump%20fra%202014-04-15%2011%3A11%3A49.png[/IMG]
No problem, the only reason i still have too boot windows is this issue, so maybe we can fix it somehow

---

### Post by QDR06VV9 on 2014-04-15
> **Johan Karl Johansen said:**
> [IMG]https://dl.dropboxusercontent.com/u/83957590/Skjermdump%20fra%202014-04-15%2011%3A11%3A49.png[/IMG]
No problem, the only reason i still have too boot windows is this issue, so maybe we can fix it somehow
Do you have any other options in the profile dropdown?

---

### Post by Johan Karl Johansen on 2014-04-15
Yes, but none of them says hdmi or directs audio there

---

### Post by QDR06VV9 on 2014-04-15
I just did a check on certified hardware and yours dont show up [there]("http://www.ubuntu.com/certification/make/Asus/?query=Asus+N76v&category=Desktop&category=Laptop&category=Server&release=14.04&level=Certified")
I'm very sorry to have wasted your time. One other thought maybe check the new kernel [3.15RC1]("http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.15-rc1-trusty/")
Out side of anything else I'm lost for now.
Regards

---

### Post by sdowney717 on 2014-04-15
Try this too

[http://ubuntuforums.org/showthread.php?t=1801882](http://ubuntuforums.org/showthread.php?t=1801882)

[http://forums.fedoraforum.org/showthread.php?t=185519&page=3](http://forums.fedoraforum.org/showthread.php?t=185519&page=3)
> I got Audio over HDMI working after following Skeptic's hint on an Intel HD Audio chipset on my Dell Studio Hybrid. 

Fix: alsamixer, choose <S/PDIF D>, toggle Mute (00 at bottom turns green)
aplay /usr/share/sounds/alsa/Front_Center.wav
= OK aplay now goes through speaker.

No other configuration required. For the record it seems ubuntu does it this way: [https://bugs.launchpad.net/dell/+bug/174696](https://bugs.launchpad.net/dell/+bug/174696)

lspci -v | grep -i audio
A: 00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 04)

---

### Post by xc3RnbFO8P on 2014-04-15
You can try this:
> sudo gedit /etc/modprobe.d/alsa-base.conf
add this line and restart:
> options snd-hda-intel model=asus-mode4

---

### Post by Johan Karl Johansen on 2014-04-15
My aplay -l:
**** List of PLAYBACK Hardware Devices ****
card 0: PCH [HDA Intel PCH], device 0: ALC663 Analog [ALC663 Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: PCH [HDA Intel PCH], device 1: ALC663 Digital [ALC663 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0


I miss this:
[COLOR=#333333][FONT=Tahoma]card 1: NVidia [HDA NVidia], device 3: HDMI 0 [HDMI 0][/FONT][/COLOR]
[COLOR=#333333][FONT=Tahoma]Subdevices: 0/1[/FONT][/COLOR]
[COLOR=#333333][FONT=Tahoma]Subdevice #0: subdevice #0[/FONT][/COLOR]

---

### Post by QDR06VV9 on 2014-04-15
So did you get it working?

---

### Post by Johan Karl Johansen on 2014-04-16
Nope

---

### Post by kenny14 on 2014-06-08
Still nothing over this? I am having the same issue as thread starter. Even created a thread for it 

[http://ubuntuforums.org/showthread.php?t=2228574&p=13044414#post13044414](http://ubuntuforums.org/showthread.php?t=2228574&p=13044414#post13044414)

---

### Post by cariboo on 2014-06-08
@kenny14, seeing as you created another thread, and your problem doesn't concern Utopic, I'm going to close this thread.

---

