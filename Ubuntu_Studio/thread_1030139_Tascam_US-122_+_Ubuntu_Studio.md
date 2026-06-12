---
title: "Tascam US-122 + Ubuntu Studio"
date: 2009-01-04
forum: Ubuntu Studio
---

### Post by Geo_V on 2009-01-04
Hi, 

I am new to Linux and istalled Ubuntu, which i found very attractive and would like to gradually make it my default operating system. However, i am facing a serious problem with my soung card "Tascam US-122" which can't be installed. I've read a few topics on the Internet saying that it can be installed and showing the way, but no matter how much i tried, i could not get it to work. I then installed Ubuntu Studio, but still with no success. This is a serious matter for me, being a musician, so if anyone actually "HAS" managed to install it, i would be very interested in knowing how. Hope someone has the answer.

Thanks,
George

---

### Post by Geo_V on 2009-01-04
I tried the installation i found on the following page 

[https://help.ubuntu.com/community/TASCAM_US-122](https://help.ubuntu.com/community/TASCAM_US-122)

The Server at Step 2 could not be found as my terminal said, so i downloaded the rpm file from this ftp site manualy 

[http://www.filewatcher.com/m/alsa-fi...09295.0.0.html](http://www.filewatcher.com/m/alsa-fi...09295.0.0.html)

and continued the proccess. Everything goes on well but when I reach Step 9 and try to load the sound card i recieve the message:

" no US-X2Y-compatible cards found "

Hope this piece of information helps somebody to guess the solution.

---

### Post by Geo_V on 2009-01-04
These are the results of the lsusb command just before Step 8 :

**Bus 005 Device 010: ID 1604:8007 Tascam US-122 Audio/Midi Interface**
Bus 005 Device 005: ID 145f:015a 
Bus 005 Device 004: ID 152e:2507 LG (HLDS) 
Bus 005 Device 003: ID 05e3:0605 Genesys Logic, Inc. USB 2.0 Hub [ednet]
Bus 005 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 003: ID 046d:c50e Logitech, Inc. MX-1000 Cordless Mouse Receiver
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

I then run the following command:

sudo fxload -s /home/x-pc2/usx2y-fw-0.1b/ld2-ezusb.hex -I /usr/share/alsa/firmware/usx2yloader/us122fw.ihx -D /dev/bus/usb/005/010

and then the "sudo usx2yloader" command which gives me the " no US-X2Y-compatible cards found" message. At this point also the "lsusb" command the results are :

Bus 005 **_Device 011_**: ID 1604:8007 Tascam US-122 Audio/Midi Interface
Bus 005 Device 005: ID 145f:015a 
Bus 005 Device 004: ID 152e:2507 LG (HLDS) 
Bus 005 Device 003: ID 05e3:0605 Genesys Logic, Inc. USB 2.0 Hub [ednet]
Bus 005 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 003: ID 046d:c50e Logitech, Inc. MX-1000 Cordless Mouse Receiver
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

I don't know, is this difference at the Device number right?

---

### Post by Cracauer on 2009-01-04
Here are the notes I kept after installing mine in Debian:

```

Making the US-122 work:
- ,package i alsa-firmware-loaders
- in debian it is misspelled us-112
- debian forgets to install the firmwares
   10  fetch http://ftp.mj2.org/pub/alsa/firmware/alsa-firmware-1.0.17.tar.bz2
    1  mkdir /usr/share/alsa/firmware
    2  mv usx2yloader  /usr/share/alsa/firmware
- plug out, plug in
- aplay -l
card 4: USX2Y [TASCAM US-X2Y], device 0: US-X2Y Audio [US-X2Y Audio #0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
- amidi -l
IO  hw:4,0,0  TASCAM US-X2Y MIDI 1

```

Hope this helps.

---

### Post by Geo_V on 2009-01-06
Hi Cracauer and thanks for the reply,

however it doesn't seem to work out. When i hit  package i alsa-firmware-loaders, the terminal says:
The program 'package' is currently not installed.  You can install it by typing: sudo apt-get install mailagent. I do this but at the next step when i try to donload the file "alsa-firmware-1.0.17.tar.bz2" with "wget" i get the message : "Resolving ftp.mj2.org... 64.240.156.196
Connecting to ftp.mj2.org|64.240.156.196|:80... failed: No route to host".

---

### Post by Geo_V on 2009-01-06
Hi Cracauer and thanks for the reply,

however it doesn't seem to work out. When i hit  package i alsa-firmware-loaders, the terminal says:
The program 'package' is currently not installed.  You can install it by typing: sudo apt-get install mailagent. I do this but at the next step when i try to donload the file "alsa-firmware-1.0.17.tar.bz2" with "wget" i get the message : "Resolving ftp.mj2.org... 64.240.156.196
Connecting to ftp.mj2.org|64.240.156.196|:80... failed: No route to host".

---

### Post by Geo_V on 2009-01-06
Sorry for the double post....:)

---

### Post by Cracauer on 2009-01-06
I'm sorry ",package" is my local script for package management.

Replace with
"apt-get install <packagename>".

Keep in mind my instructions were for Debian, (hopefully) small adjustments for Ubuntu might be required.

---

### Post by Geo_V on 2009-01-07
At last, success!

I managed to get the green light on following the instruction on this page: "http://alsa.opensrc.org/Tascam_US-122". So, the hard step is done i think, my card seems to be alive and working. The only problem now is that although it appears alive, it doesn't sound alive...no sound is produced. I'm working on it, but if anyone has any suggestion, please let me know...

Thanks.

---

### Post by Geo_V on 2009-01-07
Ok, it was the usb port, the us-122 doesn't support usb 2.0, it has to be changed to usb 1.1. I still can't figure out though why the sound card doesn't work with either Mozilla or Opera browser. The browsers keep playing the sound through the laptop speakers....Any ideas??

---

### Post by Cracauer on 2009-01-07
> **Geo_V said:**
> Ok, it was the usb port, the us-122 doesn't support usb 2.0, it has to be changed to usb 1.1. I still can't figure out though why the sound card doesn't work with either Mozilla or Opera browser. The browsers keep playing the sound through the laptop speakers....Any ideas??

You need to fiddle with asoundrc to make the new one the default soundcard.

---

### Post by Geo_V on 2009-01-07
Well, i've managed to get it installed 99%. There seems to be a little problem whenever i playback a file. When i pause it there's a continuous annoying "beep" coming up until i press play again. And i haven't yet figured out how to make my browser work with my sound card, cause when i watch a video on youtube for example, the sound comes through the onboard card of my laptop....Any ideas anyone??

---

### Post by Cracauer on 2009-01-07
> **Geo_V said:**
> Well, i've managed to get it installed 99%. There seems to be a little problem whenever i playback a file. When i pause it there's a continuous annoying "beep" coming up until i press play again. And i haven't yet figured out how to make my browser work with my sound card, cause when i watch a video on youtube for example, the sound comes through the onboard card of my laptop....Any ideas anyone??

You need to fiddle with ~/.asoundrc to make the new one the default soundcard.

---

### Post by Geo_V on 2009-01-07
I'm having a little trouble understanding what exactly this .asoundrc is doing and how it supposed to be done. I think the page you're talking about Cracauer is the following 

[http://www.alsa-project.org/main/index.php/Asoundrc#Where_does_asoundrc_live.3F](http://www.alsa-project.org/main/index.php/Asoundrc#Where_does_asoundrc_live.3F)

So i made a ".asoundrc" file in my home/pc/ directory in which i pasted the code:

pcm.!default {
	type hw
	card 0
	}

	ctl.!default {
	type hw           
	card 0
        }

Am i supposed to alter some values of the code in order to be functional cause im getting the following:

aplay -D default test.wav
test.wav: No such file or directory

---

### Post by Cracauer on 2009-01-07
try 
`aplay test.wav`

---

### Post by Geo_V on 2009-01-08
Still the same....

aplay test.wav
test.wav: No such file or directory

---

### Post by Cracauer on 2009-01-08
Dude!

---

### Post by thorgal on 2009-01-08
youtube means flash plugin. The flash plugin is a piece of cr...p. It only supports OSS or basic ALSA (I am not even sure of that). You cannot do anything from this perspective. All you can do is either fiddle around with the .asroundrc file, which is in itself a pain in the a..s or fool the flash plugin by emulating some /dev/dsp (aka OSS) device node. ALSA has an OSS emulation layer. If you have it installed, you can check whether /dev/dsp and /dev/mixer exist. If not, check whether the OSS emulation layer is loaded in the kernel :

```

lsmod | grep oss

```

If not, load it :
```

sudo modprobe snd-pcm-oss
sudo modprobe snd-seq-oss

```

check /dev/dsp again, try to play a youtube video.

Of course, if you are using pulseaudio, that's another story. You need to install libflashsupport. My experience with it is that it makes firefox unstable. In fact, I updated firefox to 3.1beta2 from getfirefox.com, tired of all these random crashes due to flash. It's much more stable but that's outside the Ubuntu reps. I don't care, it works with 3.1beta2. But god I hate all these flash stuff! even the add-on called flashblocker cannot prevent these stupid crashes.

mmmm, my rant was a bit out of scope ... :lol:

---

### Post by hpadrick on 2009-01-08
These are the steps I used to get mine working in regular Ubuntu.  Some of the needed apps are already installed in ubuntu-studio:

Install ubuntustudio-audio ubuntustudio-audio-plugings

Using the mediubuntu repos,install alsa-firmware alsa-firmware-loaders

plugin the US-122


For Plug and Play to work correctly: 

create a file in /etc/udev/rules.d/ named 55-tascam.rules with the following content:

BUS=="usb", ACTION=="add", SYSFS{idProduct}=="8006", SYSFS{idVendor}=="1604", RUN+="/bin/sh -c '/sbin/fxload -D %N -s /usr/share/alsa/firmware/usx2yloader/tascam_loader.ihx -I /usr/share/alsa/firmware/usx2yloader/us122fw.ihx'"

BUS=="usb", ACTION=="add", SYSFS{idProduct}=="8007", SYSFS{idVendor}=="1604", RUN+="/bin/sh -c '/usr/bin/usx2yloader'"

unplug then re-plugin in your us-122


To use your newly added card as the regular sound device open System->Preferences->Sound and from the drop downs select TASCAM US-X2Y


Hope this helps.

---

### Post by Geo_V on 2009-01-10
Thanks for all the answers guys. I've managed to make the US-122 my default sound card, but this "fiddling" thing with the ./asoundrc is really something i can't understand what it is and how it is done at all. If someone has the time to post a more helpful explanation on what is this ./asoundrc doing and some basic steps on how....it would be really helpfull....

And one more thing...whenever i listen to music (throught the US-122) and try to adjust my screen's brightness using the Fn+F6 buttons, the playback stops/freezes. I wonder if anyone has exprerienced something similar?

---

### Post by chilisenzacarne on 2009-01-26
> **Geo_V said:**
> Ok, it was the usb port, the us-122 doesn't support usb 2.0, it has to be changed to usb 1.1. I still can't figure out though why the sound card doesn't work with either Mozilla or Opera browser. The browsers keep playing the sound through the laptop speakers....Any ideas??

Check out this HowTo: [http://ubuntuforums.org/showthread.php?t=789578](http://ubuntuforums.org/showthread.php?t=789578) 
If you did all the soundtweaking to male it work nicely you need to intsallYou need to install Pulse-Audio-Device-Chooser (as desribed in the HowTo) and change the Playback preferences in the PulseAudioDeviceChooser Volume-Control 8as described in The HowTo to your external speakers or usb soundcard or whtaever you want to use to get the sound out of the damn machine ;-)
You can also check out my HowTo on sondproblems with Hardy and Intrepid and different programs like audacity ekiga skype, twinkle and so on on
[http://ubuntuforums.org/showthread.php?t=789578](http://ubuntuforums.org/showthread.php?t=789578)
It's in German though, but you may use Google-translation-tools on [http://www.google.de/language_tools](http://www.google.de/language_tools)
to translate it on the spot.
And thanks for your post regarding tascam us-122, i was looking for an advice before purchase. Want to say it once more: Great community behind Ubuntu, thank you all!

---

### Post by Cracauer on 2009-01-26
> **Geo_V said:**
> Thanks for all the answers guys. I've managed to make the US-122 my default sound card, but this "fiddling" thing with the ./asoundrc is really something i can't understand what it is and how it is done at all. 

Welcome to the club :)

---

### Post by Geo_V on 2009-02-13
Hello everyone again,

i've benn exclusively trying ubuntu now for a month and i can't get used to the fact that every audio or video playback freezes or stops very often such as:

1. when i playback a movie at some point the playback may freeze or acting like the speed was slowed down and the sound dissapears..

2. when i listen to radio online the playback will stop without reruming.

3. when i'm in youtube the sound card is not working at all but only the onboard card.

Is there something wrong with the communication of the US-122 with Ubuntu Studio?? Should i install a plugin or something??Please, if anyone knows a clue, post some help here cause i really liked the linux system...i wouldn't want to have to go back to windows again....

Thanks...

---

