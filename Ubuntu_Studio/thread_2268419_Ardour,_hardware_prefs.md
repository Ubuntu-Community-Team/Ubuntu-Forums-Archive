---
title: "Ardour, hardware prefs"
date: 2015-03-08
forum: Ubuntu Studio
---

### Post by Francis_Dunnery on 2015-03-08
i can see preferences in ardour but it doesnt have any option to change sample rate or audio hardware. the system at present is recording in from the computer and sending the signal out of the computer. where is the switch to send the sound to my hardware.

---

### Post by khelben1979 on 2015-03-09
Are you looking for the possibility to switch to another sound hardware device being used by ardour?

---

### Post by Francis_Dunnery on 2015-03-09
Yes that's right. I cannot see where to change it. In other music programs it's usually in audio prefs. I looked through the menus and there's nothing there..... Or at least it seems there's nothing there. I've been wrong more than once in linux!!!!!

---

### Post by khelben1979 on 2015-03-09
I am pretty sure you need to change audio settings from your system, once that is done, the ardour program should use those settings. It's a bit difficult for me to say exactly what sound prefs application you need to start since it might be differences with different versions of Ubuntu. What version of Ubuntu are you using?

---

### Post by marseille2 on 2015-03-09
[[COLOR=#000000]khelben1979[/COLOR]]("http://ubuntuforums.org/member.php?u=443262") is right. **Set Jackd's sample rate** first ... then Ardour opens up at that rate and by default, it will automatically connect your hardware. You can then adjust connections for each track in Ardour's mixer.

----

**[SIZE=4]How-To[/SIZE]**

Check if Qjacktl settings have the sample and bit rate you want / correct if necessary. Close Qjacktl (also any other audio apps if they're running), and open the terminal. Make sure Jackd and Jackdbus are off.

```
$ killall Jackdbus Jackd
```

Then find your audio card(s) / device(s) with this command:

```
$ cat /proc/asound/cards
```

example output:


> 

0 [SB             ]: HDA-Intel - HDA ATI SB
                      HDA ATI SB at 0xfeb00000 irq 16

1 [HDMI           ]: HDA-Intel - HDA ATI HDMI
                      HDA ATI HDMI at 0xfea40000 irq 81

[B]2 [UA700          ]: USB-Audio - EDIROL UA-700
                      Roland EDIROL UA-700 at usb-0000:00:12.0-1, full speed[/B]

Tell Jackd to use your preferred sound card with a particular sample rate. Here's an example of Jackd using realtime, 44.1k, ALSA, and capturing (-C) input from card 2, and also sending output (-P) to card 2 (Edirol). 

```
$ jackd -d alsa -r41000 -C hw:2 -P hw:2
```

Note: you can send output to another card by giving the playback switch (-P) a related device number. The following example captures the Edirol, and sends sound to the onboard audio card "0":

```
$ jackd -d alsa -r41000 -C hw:2 -P hw:0
```

---

### Post by Francis_Dunnery on 2015-03-10
brilliant, i love it. the jack thing had me confused , now i know what it is. thank you. the terminal thing is kiler, it makes me feel like im darth vader ha ha

---

### Post by marseille2 on 2015-03-11
I completely understand!:D

---

