---
title: "mbox2 fra digidesign hjelp!!!"
date: 2010-04-05
forum: Ubuntu Studio
---

### Post by turbos4 on 2010-04-05
I'm trying too connect my mbox2 from Digidesign with ubuntu studio 9.10 Karmic

kernel : 2.6.31-9-rt



I have tried this way:

[http://www.zamaudio.com/?p=97](http://www.zamaudio.com/?p=97)

But when I start the computer after installing the new kernel, the lights don't work and I have no sound, out of the mbox2.

I have tried 2 times with diffrent kernel, but the same result.

attached text file with 'lsusb -v' with kernel 2.6.31-9-rt

Please help me :lolflag:

---

### Post by cchhrriiss121212 on 2010-04-06
This doesn't seem to be a linux friendly device, so it might take some patience to get it working. The link you gave was to a driver designed by someone, is this what you installed? You do not need to install a new kernel.

What does "aplay -l" give you?

---

### Post by turbos4 on 2010-04-07
I did create a new kernel, but it got worse. So i got back to det old one
2.6.31.9-rt

My 'aplay -l' gives

card 0: NVidia [HDA NVidia], device 0: ALC883 Analog [ALC883 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 1: ALC883 Digital [ALC883 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

But usb audio is not on the list.
but the mbox2 is in

SYSTEM>PREFRENCE>SOUND

On the box 'hardware'

I have internal soundcard (card0) and mbox (usb)

            Mbox_2
            1 output/1 input
            analog stereo duplex

How can i get it to work for me?

---

### Post by cchhrriiss121212 on 2010-04-07
Sorry, I did not read that link carefully. If you have tried to apply that patch to a kernel and alsa/jack does not see the device, then there is not much else you can do. Sell it and buy something compatible, m-audio are good for this.

---

### Post by turbos4 on 2010-04-07
I can see it inn sound controll panel.....

ok, then i hope someone else can help me!

thnxs for trying :)

---

### Post by turbos4 on 2010-04-25
Yes, have sound out of mbox2. But it's only when i log in to gnome.

I follow this to load module at startup.

[http://www.linuxquestions.org/questions/linux-general-1/usb-modules-not-loading-129657/](http://www.linuxquestions.org/questions/linux-general-1/usb-modules-not-loading-129657/)

This some of the page.

Got it working! As advised, created a startup script and placed it in /etc/rc.d/init.d named usbstart and another in /etc/rc.d/rc5.d named S07usbstart (startup link) and it works fine.
Below is the content of the script in case it is helpful to anyone else

#!/bin/bash

# USB start, workaround for usb modules not loading automatically at boot
# place one copy in /etc/rc.d/init.d and name it usbstart and one in 
#/etc/rc.d/rc5.d named S07usbstart
# ensure that the files in both have full r/w permissions in order to execute
# you can do this with chmod 755 S99usbstart and chmod 775 usbstart from each of 
#the directories where you placed the files.
# Note the above /etc/rc5/d refers to run level 5.  If you have a different run 
#level then change the 5 to whatever your current run level is.
# provided with no restrictions, modify as you wish, no warranty implied nor is 
#the author responsible for any problems caused by use of this script.


# loading usbcore

/sbin/modprobe usbcore

#loading usb-uhci

/sbin/modprobe usb-uhci

#loading human interface device

/sbin/modprobe hid

#mounting usbdevfs filesystem

mount -t usbdevfs none proc/bus/usb


#Done!

Named one usbstart and stored it in /etc/rc.d/init.d and chmod 755 usbstart to 
have the correct file permissions.

Put a copy and renamed it to S07usbstart in /etc/rc.d/rc5.d  Also chmod 755 
this one for correct file permissions. The S07 means start service seventh.  
This ensures that the usb subsystem is loaded before any devices which may need 
it. 


from dave37


Need som help to get sound of mplayer, vlc and so on.

---

### Post by AutoStatic on 2010-04-25
Hello turbos4, nowadays there is the file */etc/modules* that takes care of this. You can place modules that don't get loaded automatically in there.

I also checked the modules in the script:

```
jeremy@soushi:~$ modinfo usbcore
ERROR: modinfo: could not find module usbcore
jeremy@soushi:~$ modinfo usb-uhci
ERROR: modinfo: could not find module usb-uhci
jeremy@soushi:~$ modinfo hid
ERROR: modinfo: could not find module hid
```

I'm on 9.10 and each of those modules don't exist. And from the mount manpage: > Earlier, usbfs was known as usbdevfs.  Note, the real list of all supported filesystems depends on your kernel.

So actually, this script does nothing :( It tries to load modules that don't exist and mount a filesystem that is obsolete. So it's probably working because of the zamaudio patch.

---

### Post by turbos4 on 2010-04-27
```
jeremy@soushi:~$ modinfo usbcore
ERROR: modinfo: could not find module usbcore
jeremy@soushi:~$ modinfo usb-uhci
ERROR: modinfo: could not find module usb-uhci
jeremy@soushi:~$ modinfo hid
ERROR: modinfo: could not find module hid
```I'm on 9.10 and each of those modules don't exist. And from the mount manpage: 
 [/QUOTE]

I got same when i used this command.

But, i'm not using zamaudio, i'm using 2.6.31-9-rt ubuntu studio. And i use ice1712 conf in asoundconf.

why is it working then?

How to link player and recorder to alsa?

---

### Post by AutoStatic on 2010-04-27
> **turbos4 said:**
> why is it working then?Probably because the zamaudio patch made it into 2.6.31 or the ALSA devs wrote a patch/quirk themselves.

> **turbos4 said:**
> How to link player and recorder to alsa?Which player and which recorder? And how does your .asoundrc look like right now?

---

### Post by turbos4 on 2010-04-27
.asoundrc

pcm.ice1712 {
    type hw
    card 1
    device 0
}
pcm.channel1 {
    type plug
    ttable.0.0 1 # studio monitor front left...Delta 1
    ttable.0.1 1 # studio monitor front right...Delta 2
    slave.pcm ice1712
}
pcm.channel2 {
    type plug
    ttable.0.2 1 # studio monitor rear left...Delta 3
    ttable.0.3 1 # studio monitor rear right...Delta 4
    slave.pcm ice1712
}
pcm.channel3 {
    type plug
    ttable.0.4 1 # oscilloscope 1...Delta 5
    ttable.0.5 1 # oscilloscope 2...Delta 6
    slave.pcm ice1712
}
pcm.channel4 {
    type plug
    ttable.0.6 1 # headphone 1...Delta 7
    ttable.0.7 1 # headphone 2...Delta 8
    slave.pcm ice1712
}
pcm.ice1712_spdif {
    type plug
    ttable.0.8 1 # S/PDIF left...Delta 9
    ttable.1.9 1 # S/PDIF right...Delta 10
    slave.pcm ice1712
}
pcm.mon_mix {
    type plug
    ttable.0.10 1 # digital mix left
    ttable.1.11 1 # digital mix right
    slave.pcm ice1712
}
pcm.multi_send {
    type plug
    ttable.0.0 1 # studio monitor front left...Delta 1
    ttable.0.1 1 # studio monitor front right...Delta 2
    ttable.0.4 1 # oscilloscope 1...Delta 5
    ttable.0.5 1 # oscilloscope 2...Delta 6
    ttable.0.6 1 # headphone 1...Delta 7
    ttable.0.7 1 # headphone 2...Delta 8
    slave.pcm ice1712
}
pcm.hwout {
    type plug
    slave.pcm ice1712
}

---

### Post by turbos4 on 2010-04-27
Have also removed onboard soundcard from bios.....

---

### Post by turbos4 on 2010-05-01
Have updatet to ubuntustudio 10.04 i386.

Have sound when i loggon to gnome, but when i are logged in i have no sound.
When go to Pulse manager>tab:sample cache>mark:menu click and play i got sound.
But when i try mplayer, i have no sound.

Need some guided help please :)

---

### Post by ram130 on 2010-05-05
> **turbos4 said:**
> Have updatet to ubuntustudio 10.04 i386.

Have sound when i loggon to gnome, but when i are logged in i have no sound.
When go to Pulse manager>tab:sample cache>mark:menu click and play i got sound.
But when i try mplayer, i have no sound.

Need some guided help please :)

Was this an fresh install and what steps you followed exactly and does your mbox2 light up? i got a mbox2 mini

---

### Post by turbos4 on 2010-05-05
I have a fresh install with ubuntustudio 10.04.
Lyden kom med en gang på den nye distro.
dessverre bare ved oppstart og innlogging. Ser ut som den bruker pulseaudio.
Den la til snd-usb-audio, men mangler forsatt drivern.
My mbox2 light up. (MIC,MIC,USB) S/PDIF blinker.

sudo nano /etc/modprobe.d/alsa-base.conf

options snd-usb-audio index=0 vid=0dba pid=3000

Hvor jeg bruker id'en til mbox2 bak

---

### Post by ram130 on 2010-05-05
> **turbos4 said:**
> I have a fresh install with ubuntustudio 10.04.
Lyden kom med en gang på den nye distro.
dessverre bare ved oppstart og innlogging. Ser ut som den bruker pulseaudio.
Den la til snd-usb-audio, men mangler forsatt drivern.
My mbox2 light up. (MIC,MIC,USB) S/PDIF blinker.

sudo nano /etc/modprobe.d/alsa-base.conf

options snd-usb-audio index=0 vid=0dba pid=3000

Hvor jeg bruker id'en til mbox2 bak

So you are saying you get lights blinking on the mbox 2 at start up after adding that code to the .conf?

I'm not sure about the last thing you said about getting the mbox 2 behind.

---

### Post by turbos4 on 2010-05-08
I got that from Alsa forum and if u have 2 usb device 

for example
options snd-usb-audio index=0 vid=0dba,xxxx pid=3000,xxxx

and so on, if i got it right.

---

### Post by ram130 on 2010-05-08
> **turbos4 said:**
> I got that from Alsa forum and if u have 2 usb device 

for example
options snd-usb-audio index=0 vid=0dba,xxxx pid=3000,xxxx

and so on, if i got it right.

Still no go.. :(

---

### Post by ram130 on 2010-08-22
any updates on this?

---

### Post by simieon on 2010-09-02
BUMP!

i386 10.04 lucid, upgraded to have all the features of studio. intel 4xx series chipset.

im a complete linux newbie (just a few months using it), and me and my mate are finally rebuilding our "studio".
with buying new equipment out of the question, and the need to get a mbox2 pro factory fully working. (midi in, both mic ports etc). i could really use some help to make it work. 

because i know that (with my small knowledge of linux) this could be a lengthy process, i will offer the best i can in return. and should it end up fullo functional i will write a beginners guide to make it work. as well as translate the steps for our norwegian thread creator, into danish (very similar language and completely understandable for any norwegian).

ps. im a bit slow getting stuff, and might need a "dummies guide to"

thanks in advance.

---

