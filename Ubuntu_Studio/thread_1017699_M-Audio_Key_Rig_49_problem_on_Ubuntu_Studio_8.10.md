---
title: "M-Audio Key Rig 49 problem on Ubuntu Studio 8.10"
date: 2008-12-21
forum: Ubuntu Studio
---

### Post by Jormeliini on 2008-12-21
I have a problem with my usb-connected M-Audio Key Rig 49 midi keyboard. When I plug it in and power it up the lights on the keyboard light up and lsusb recognizes it:

Bus 002 Device 008: ID 0763:019b Midiman KeyRig 49

I can't get the keyboard connected to any software i.e. ZynAddSubFX as jack doesn't recognize it. I think it should be there in the qjackctl connections in a similar way as Virtual MIDI Keyboard, right? Nothing refers to M-Audio, Midiman, or a midi keyboard.

The keyboard seems to be working out-of-the-box on everyone else. Maybe I'm missing some basics here. The keyboard is not broken. It worked nicely with Windows when I used to have it installed.

Any help will be appreciated. Thanks in advance.

---

### Post by psidre.felix on 2008-12-21
I'm experiencing same issue with my m-audio ozone midi controller. I'm not real clear on whether I've missed a step with the firmware. I installed the 'madfuload' package and doing lsusb does show the ozone as: 
```

Bus 002 Device 009: ID 0763:2808 Midiman

```
I did this:
```

sudo madfuload -D /proc/bus/usb/002/009 -f /usr/share/usb/maudio/ma008100.bin --nowait

```
and this was what I got back in the terminal:

```
 
Segmentation fault

```

I made sure I have the .bin files and this is what I found:
```

psidre@XXXXXXXXX:/usr/share/usb/maudio$ ls
ma003101.bin  ma004103.bin  ma005101.bin  ma006100.bin  ma008100.bin

```

So yeah I'm stuck like chuck here and would love some help.

I'm running 8.10 intrepid 64-bit
ALC883 Analog

thanx,
psidre

---

### Post by Jormeliini on 2008-12-23
It's working now. The snd-usb-audio module was missing.

---

### Post by jmatties on 2009-06-12
> **Jormeliini said:**
> It's working now. The snd-usb-audio module was missing.
I have the same problem you had, how did you get the snd-usb-audio module?

---

### Post by Jormeliini on 2009-06-13
> **jmatties said:**
> I have the same problem you had, how did you get the snd-usb-audio module?

You'll need to build alsa from source. There are instructions in [http://www.alsa-project.org/main/index.php/Matrix:Module-usb-audio]("http://www.alsa-project.org/main/index.php/Matrix:Module-usb-audio"). In addition you may need alsa-firmware package which is installed in the same way as alsa-utils and alsa-lib.

Feel free to ask for more help if you are not familiar with building programs from source.

---

### Post by skywriter on 2009-06-24
Is there any problems with delay? What hardware must be used to prevent delays?

---

### Post by Jormeliini on 2009-06-24
> **skywriter said:**
> Is there any problems with delay? What hardware must be used to prevent delays?

I have not experienced problems with delay. Key Rig uses USB so you do not need any special hardware.

---

### Post by skywriter on 2009-06-24
> **Jormeliini said:**
> I have not experienced problems with delay. Key Rig uses USB so you do not need any special hardware.
I mean the hardware of computer. CPU, RAM? I think if the hardware were too weak you would experience problems with it's speed.

---

### Post by Jormeliini on 2009-06-26
> **skywriter said:**
> I mean the hardware of computer. CPU, RAM? I think if the hardware were too weak you would experience problems with it's speed.

You'll be fine if you can run your operating system and programs relatively smoothly. I haven't had problems even with my Athlon XP 2600+ and 768MB RAM running Ubuntu.

---

### Post by skywriter on 2009-06-28
I experienced that smooth work of Keyrig+QSynth without sufficient delay and without "clicks" and pauses is only possible when jackd is in "realtime mode". But in this mode computer becomes very slow and sometimes it freezes. I tested on Celeron 2.8 Ghz/1 GB RAM (built-in Azalia soundchip) running Ubuntu Studio 9.04.

Is there any advice how to optimize this configuration?

---

### Post by Jormeliini on 2009-06-29
> **skywriter said:**
> I experienced that smooth work of Keyrig+QSynth without sufficient delay and without "clicks" and pauses is only possible when jackd is in "realtime mode". But in this mode computer becomes very slow and sometimes it freezes. I tested on Celeron 2.8 Ghz/1 GB RAM (built-in Azalia soundchip) running Ubuntu Studio 9.04.

Is there any advice how to optimize this configuration?

There are plenty of things you can do. Could you be more specific? What have you done? Take a look at following link if you haven't done it already.
[https://help.ubuntu.com/community/UbuntuStudio]("https://help.ubuntu.com/community/UbuntuStudio")

---

### Post by dufft on 2009-08-23
> **Jormeliini said:**
> You'll need to build alsa from source. There are instructions in [http://www.alsa-project.org/main/index.php/Matrix:Module-usb-audio](http://www.alsa-project.org/main/index.php/Matrix:Module-usb-audio). In addition you may need alsa-firmware package which is installed in the same way as alsa-utils and alsa-lib.

Feel free to ask for more help if you are not familiar with building programs from source.

I ran into a problem with alsa-driver when using modprobe. I have no idea about what it does and how, so could you please help me?

```

root@dufft-laptop:/etc/alsa/alsa-utils-1.0.20# modprobe snd-usb-audio
WARNING: Error inserting snd_seq_device (/lib/modules/2.6.28-15-generic/kernel/sound/acore/seq/snd-seq-device.ko): Unknown symbol in module, or unknown parameter (see dmesg)
WARNING: Error inserting snd_rawmidi (/lib/modules/2.6.28-15-generic/kernel/sound/acore/snd-rawmidi.ko): Unknown symbol in module, or unknown parameter (see dmesg)
WARNING: Error inserting snd_usb_lib (/lib/modules/2.6.28-15-generic/kernel/sound/usb/snd-usb-lib.ko): Unknown symbol in module, or unknown parameter (see dmesg)
WARNING: Error inserting snd_page_alloc (/lib/modules/2.6.28-15-generic/kernel/sound/acore/snd-page-alloc.ko): Unknown symbol in module, or unknown parameter (see dmesg)
WARNING: Error inserting snd_timer (/lib/modules/2.6.28-15-generic/kernel/sound/acore/snd-timer.ko): Unknown symbol in module, or unknown parameter (see dmesg)
WARNING: Error inserting snd_pcm (/lib/modules/2.6.28-15-generic/kernel/sound/acore/snd-pcm.ko): Unknown symbol in module, or unknown parameter (see dmesg)
FATAL: Error inserting snd_usb_audio (/lib/modules/2.6.28-15-generic/kernel/sound/usb/snd-usb-audio.ko): Unknown symbol in module, or unknown parameter (see dmesg)

```What should I do?

---

### Post by Jormeliini on 2009-08-23
> **dufft said:**
> I ran into a problem with alsa-driver when using modprobe. I have no idea about what it does and how, so could you please help me?

That's strange. Did you get errors when compiling? If not I can't help you, sorry. Never had that kind of problems.

---

