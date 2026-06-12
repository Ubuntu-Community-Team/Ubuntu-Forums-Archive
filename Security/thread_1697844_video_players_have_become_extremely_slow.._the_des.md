---
title: "video players have become extremely slow.. the description."
date: 2011-03-01
forum: Security
---

### Post by gullible_travels on 2011-03-01
Dear All,

A week back, I was streaming a video when suddenly I got a warning that a script was running. I closed the browser and then the computer became really slow.

I re-started my computer and had mounting problems. That is fixed now.

However, my vlc and other players are not functioning properly. Moreover, whenever I stream a video, it always gets stuck and becomes slow. This has been persisting for quite sometime now.

I would like you all the help me out to fix this one out. 

A new born Ubuntu user.:)

---

### Post by gullible_travels on 2011-03-01
My user.log.1 for Sunday 20th Feb reads:

```

Feb 20 11:17:46 adIFS-laptop pulseaudio[1570]: alsa-sink.c: ALSA woke us up to write new data to the device, but there was actually nothing to write!
Feb 20 11:17:46 adIFS-laptop pulseaudio[1570]: alsa-sink.c: Most likely this is a bug in the ALSA driver 'snd_hda_intel'. Please report this issue to the ALSA developers.
Feb 20 11:17:46 adIFS-laptop pulseaudio[1570]: alsa-sink.c: We were woken up with POLLOUT set -- however a subsequent snd_pcm_avail() returned 0 or another value < min_avail.
```

Any suggestions!!!

---

### Post by cariboo on 2011-03-01
Your log snippet was about a pulse problem, which should have nothing to do with your problem, did you do as the error said?

---

### Post by gradinaruvasile on 2011-03-01
Please elaborate on the "A script was running". Scripts are running all the time. What script was running then?

When the computer becomes slow, open a terminal and type "top" then press enter. See what process eats most cpu (if any).

Moreover, pls state how do you stream video? Watch video from the net via flash or other plugins or just watch videos from the local drives?

And as a rule of thumb, you should post your hardware specs (output of "lspci" in a terminal should do it). And the video drivers used (proprietary+version or default if you did not install anything).

---

### Post by gullible_travels on 2011-03-02
gradi,

I got a pop up saying that an unknown script was running while I streamed the video.. It was on the browser, so yes, plug-ins.. shockwave flash etc etc..

Hardware specs:

00:00.0 Host bridge: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub (rev 07)
00:02.0 VGA compatible controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
00:02.1 Display controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 2 (rev 03)
00:1c.5 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 6 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 03)
00:1d.3 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 93)
00:1f.0 ISA bridge: Intel Corporation ICH9M LPC Interface Controller (rev 03)
00:1f.2 IDE interface: Intel Corporation ICH9M/M-E 2 port SATA IDE Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 03)
00:1f.5 IDE interface: Intel Corporation ICH9M/M-E 2 port SATA IDE Controller (rev 03)
00:1f.6 Signal processing controller: Intel Corporation 82801I (ICH9 Family) Thermal Subsystem (rev 03)
01:00.0 Network controller: Intel Corporation Wireless WiFi Link 5100
04:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 02)

---

### Post by gullible_travels on 2011-03-02
Everytime I stream a video now, the video keeps breaking (no buffering issues) making the viewing extremely unpleasant... please suggest..

---

### Post by gullible_travels on 2011-03-02
doing as told... will post results in a while..

---

### Post by gullible_travels on 2011-03-02
cariboo907.. you made my day.. did as you told.. reinstalled the package.. and baam it works... thank you..

---

### Post by gullible_travels on 2011-03-02
hey guys false flag..
the video has started breaking again and the comp has become utterly slow.. took a while for this tab to open itself..the screen goes grey and then returns to normal but still the system is slow.. cariboo helpppp!!!

---

### Post by cariboo on 2011-03-02
Open a terminal and type:

```
top
```

to see what application is using all your cpu cycles. or got to System->Administration->System Monitor if you need a gui. Be aware that System Monitor has it's own overhead.

---

### Post by gullible_travels on 2011-03-03
hi cariboo907,

I did that and found that my browser uses very high CPU%..
Is there any solution to this..
I even updated my ALSA.. 
The problem still persists...

---

