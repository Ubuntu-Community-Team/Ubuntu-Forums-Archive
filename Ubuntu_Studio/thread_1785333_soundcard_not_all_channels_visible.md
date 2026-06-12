---
title: "soundcard not all channels visible"
date: 2011-06-18
forum: Ubuntu Studio
---

### Post by drfreq on 2011-06-18
Hello,

i have bought a soundcard for 15 €, it is a techsolo with 5.1 / 7.1, it  supports 6 Speakers to be connected. I have installed the drivers at  windows 7 and it is possible to access / route audio from within an  application like samplitude to the individual outputs, they are vissible  by the asio 4 all driver for example...

in ubuntu the sndcrd is installed automaticaly and the mixer shows all 6  possible channels of the 5.1 configuration mode. when i start jackd  server it is only possible to start 2 outputs (main outputs). if i start  qtractor or ardour and choose the alsa driver it also only shows me the  master output.

can someon advise how to make the other outputchannels visible? thanks

---

### Post by Pablo_F on 2011-06-18
First you have to look into the terminal output of this command:

```
arecord -l && aplay -l
```

Note the card and device numbers. Let me suppose (I can't check this) that there is only one card (which is called hw:0). It could have several so-called "devices", say it has two: hw:0,**0** and hw:0,**1**. 

Suppose that hw:0,0 is listed as a capture device and also as a playback device, i.e., it is a duplex device. And that hw:0,1 is only listed as a playback device. hw:1 is a playback only device. Each device has its own capture and/or playback channels. 

Probably, your card has at least two devices for playback and one of them is playback only.

If you are unsure, paste here the output of the command mentioned. 

Cheers! Pablo

PD: I almost forgot. In this case, I think that you can use alsa_out to have all the playback channels. Look at [this]("http://manpages.ubuntu.com/manpages/lucid/man1/alsa_out.1.html") 

Also, check jack official FAQ's . jackaudio.org

---

### Post by Pablo_F on 2011-06-18
Well, maybe alsa_out won't be useful after all. You are looking for a multi-playback playback device.

---

### Post by Flaggmann on 2011-06-18
Take a check on the alsa project web site and look for setting up an /etc/asound.conf file.
there is one created in the private hidden user folders, .asoundrc or something close to that. They have an example file like :
@@@@@@@@@@@@@@@@@@@
pcm.!default {
    type hw
    card 0
}

ctl.!default {
    type hw           
    card 0
}

pcm.mainboard- HDA NVidia {
    type hw               # Kernel PCM
    card 0        # Card name or number
    [device] 0         # Device number (default 0)     
    [subdevice] -1       # Subdevice number, -1 first available (default -1)
    mmap_emulation BOOL   # enable mmap emulation for ro/wo devices
}

pcm.HDA-Intel- HDA NVidia {
    type hw
    card 0
}

ctl.HDA-Intel- HDA NVidia {
    type hw           
    card 0
}

@@@@@@@@@@@@@@@@@@@

all you do is expand it by adding further lines and changing the numbers to reflect the extra additional ports you want.  normally you will see an hw: 0,0  0,1  but you modify it to 
show hw: 0,0 0,1 0,2 0,3 0,4 0,5 0,6   a second card would be hw: 1,0 1,1 1,2 1,3 1,4 1,5 1,6 etc. You will also know that the names like hw can be custom labels here as well, if you want something different use it, then save and restart the server to pick up the new names and ports. You will notice th names change in  jack connections and patchbay windows to what you put in these files. It is just another way to make it a bit more intuitive-- instead of hw, default, or pcmdev or HDA-Nvidia you might use SB128  or SBLive  etc.

see also  [http://www.gentoo-wiki.info/HOWTO_Surround_Sound](http://www.gentoo-wiki.info/HOWTO_Surround_Sound)


If you use the method where the file is in /etc/asound.conf it will be available to all users; so if you have a band with a number of different usernames they all will see the same thing on that machine. If you run something unattended with a system user rather than having anyone logged on, this will work also. If you opt to use the hidden home folder config file, then it will only apply to you when you are logged on.

---

