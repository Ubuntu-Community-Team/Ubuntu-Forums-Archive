---
title: "Can't get Focusrite Saffire 6 Usb to work"
date: 2014-10-13
forum: Ubuntu Studio
---

### Post by german-toledochile on 2014-10-13
Hello

I just installed yesterday Ubuntu Studio with dual-boot so now i have windows 7 and linux in the same PC.
Actually i'm a complete newbie in linux, first time ever i'm trying it and everything seems great. Except that i can't get my Interface SAFFIRE 6 USB to work here. Ubuntu doesn't recognize it as a soundcard.
I did my research and some people didn't have any problems just connecting it by USB out of the box. Other people recommended to update the kernels. I tried this and had a big kernel pannic!, tried to uninstall it but still had the same kernel panic. So i had to re install ubuntu studio from scratch :( . I also lost a lot of hard drive space doing this (i don't know why).

So the thing is that i hate Windows and really want to give a chance to Linux. But i can't work without my sound interface. I'm a professional musician and need to record audio and midi, also mix, mastering, etc.... If Saffire 6 doesn't work, i'll have to go back to Windows and forget about Linux forever :-( .

Please, any help?, thanks in advance and sorry for my english mistakes. My native language is Spanish.

---

### Post by jejeman on 2014-10-13
Give
```
lsusb
aplay -l
cat /proc/asound/cards
```

---

### Post by german-toledochile on 2014-10-13
ok this is what i got

> germanpianista@GermanLinux:~$ lsusb
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 003: ID 1235:0010 Novation EMS 
Bus 006 Device 002: ID 04d9:1133 Holtek Semiconductor, Inc. 
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
germanpianista@GermanLinux:~$ aplay -l
**** Lista de PLAYBACK dispositivos hardware ****
tarjeta 0: Intel [HDA Intel], dispositivo 0: ALC1200 Analog [ALC1200 Analog]
  Subdispositivos: 0/1
  Subdispositivo #0: subdevice #0
tarjeta 0: Intel [HDA Intel], dispositivo 1: ALC1200 Digital [ALC1200 Digital]
  Subdispositivos: 1/1
  Subdispositivo #0: subdevice #0
germanpianista@GermanLinux:~$ cat /proc/asound/cards

---

### Post by jejeman on 2014-10-13
Which one of these USB devices is Saffire?
ALSA didn't recognized Saffire.
Where is the output from the last command?
Is Saffire plugged in/turned on?
Give
```
uname -r
lsb_release -drc
```

---

### Post by german-toledochile on 2014-10-13
yes, is connected. 
Actually it doesn't have an ON/OFF switch.... it should automatically turn on a green light, which now is always off.

this is what i got with the command you gave me

> germanpianista@GermanLinux:~$ uname -r
3.13.0-37-lowlatency
germanpianista@GermanLinux:~$ lsb_release -drc
Description:    Ubuntu 14.04.1 LTS
Release:    14.04
Codename:    trusty



---

### Post by jejeman on 2014-10-16
That is strange about the light. Is the green lite showing power or sync with PC?
Anyway, every device that is functional should be listed by lsusb command. So, does device works? Is the cable ok? Did you tried other USB port? Don't use USB3 ports.

edit:
I see that this device registers as 1235:0010 Novation EMS, so it is functional.
Give 
```
lsmod | grep snd
```

---

### Post by german-toledochile on 2014-10-16
Thank you so much for replying! 
this is what i got now

> snd_usb_audio         153525  3 
snd_usbmidi_lib        25070  1 snd_usb_audio
snd_hda_codec_realtek    61438  1 
snd_hda_intel          52306  3 
snd_hda_codec         192906  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13602  2 snd_usb_audio,snd_hda_codec
snd_pcm               102040  5 snd_usb_audio,snd_hda_codec,snd_hda_intel
snd_page_alloc         18710  2 snd_pcm,snd_hda_intel
snd_seq_midi           13324  0 
snd_seq_midi_event     14899  1 snd_seq_midi
snd_rawmidi            30095  2 snd_usbmidi_lib,snd_seq_midi
snd_seq                61560  2 snd_seq_midi_event,snd_seq_midi
snd_seq_device         14497  3 snd_seq,snd_rawmidi,snd_seq_midi
snd_timer              29433  2 snd_pcm,snd_seq
snd                    69189  25 snd_hda_codec_realtek,snd_usb_audio,snd_hwdep,snd_timer,snd_pcm,snd_seq,snd_rawmidi,snd_usbmidi_lib,snd_hda_codec,snd_hda_intel,snd_seq_device,snd_seq_midi
soundcore              12680  1 snd



The green light shows connection with the PC, i know everything is Ok becouse i can use the interface normally in windows 7. But in LINUX it won't do anything. So i know that the cable is ok and the device works.

So i've been looking everywhere i can think off info about this issue.. no answer... Some people even were trying to help me in the IRC chat, but still nothing happens. I'm so frustrated now... Becouse i'll have to go back to windows and won't be able to use Linux. If i can't work with my interface i think there's nothing for me here :-(

---

### Post by bulevardi on 2014-10-17
How are you connecting with Linux? Do you use Jack or Qjackctl?
Maybe some of the settings are wrong configurated?

---

### Post by richierich1986 on 2014-10-18
From one sound engineer to another, save yourself the pain of trying to use Linux for professional audio purposes. I've gone through this with different audio interfaces, including yours, but it just doesn't play well with Linux. Yes, you can get certain cards to work and I did as well, but apart from Ardour and Alsa Modular Synth, which are quite awesome, there isn't much to work with in terms of plugins. Sure there are enough of them, but don't expect to use them in a professional setting. The quality just isn't all that great.

On top of that, Windows is just going to give you an easier time and will let you actually focus on what you intended to do in the first place, create something.

I believe Linux will get there, truly, but it just isn't yet. You can see things are changing, as for example photo editing gives you more and very professional options on Linux. Audio just needs more manufacturer support on the hardware side.

---

### Post by mikeh789 on 2014-10-19
please try the 14.10 iso. you can try it live. that kernel version should (as i read) support your device "out of the box".. you can then decide if the easiest way to move forward is to install 14.10, or install a mainline kernel .deb, or a ppa for a newer kernel.. 

[http://cdimage.ubuntu.com/ubuntustudio/dvd/pending/](http://cdimage.ubuntu.com/ubuntustudio/dvd/pending/)
[http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.17.1-utopic/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.17.1-utopic/)

cheers, and good luck.. and be sure you let focusrite know you would like support for linux

---

### Post by zeljko3 on 2014-10-19
> **mikeh789 said:**
> please try the 14.10 iso. you can try it live. that kernel version should (as i read) support your device "out of the box".. you can then decide if the easiest way to move forward is to install 14.10, or install a mainline kernel .deb, or a ppa for a newer kernel.. 

[http://cdimage.ubuntu.com/ubuntustudio/dvd/pending/](http://cdimage.ubuntu.com/ubuntustudio/dvd/pending/)
[http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.17.1-utopic/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.17.1-utopic/)

cheers, and good luck.. and be sure you let focusrite know you would like support for linux

Yes, it's working OTB, thank you! \\:D/

---

### Post by Cipector on 2015-08-09
Hi i have 14.04 trusty only ubuntu, not ubuntu studio, and i can see and use saffire usb 6 only for play not for record.
tried also 14.10 ubuntu studio but is the same.
does anybody know how to record with usb saffire 6?

---

