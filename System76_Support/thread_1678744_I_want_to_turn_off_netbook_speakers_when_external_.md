---
title: "I want to turn off netbook speakers when external speakers plugged in."
date: 2011-01-30
forum: System76 Support
---

### Post by tc101 on 2011-01-30
I want to turn off netbook speakers when external speakers plugged in.  How do I do that?

---

### Post by kerry_s on 2011-01-31
from the icon, you change the output device.

you don't like the surround sound? :lolflag:

---

### Post by tc101 on 2011-01-31
Under Sound Preferences/Output Tab, there is only one device listed.  It is "Internal Audio Analog Stereo".  There is a radio button beside it, but the radio button does not respond when I click it.

I have some speakers plugged into the netbook, and they play, but they do not show up on the output tab under devices.  

This used to work fine.  When the external speakers were plugged in the speakers in the net book did not play.  I am not sure what caused the change.  Maybe some recent ubuntu upgrade.

---

### Post by Kirboosy on 2011-01-31
1. copy-paste the following command into the Terminal:
 ```
gksudo gedit /etc/modprobe.d/alsa-base.conf
``` 2. Using the gedit editor, add the following lines to the end of the /etc/modprobe.d/alsa-base.conf file:
 ```
# Keep snd-pcsp from beeing loaded as first soundcard
options snd-pcsp index=-2
alias snd-card-0 snd-hda-intel
alias sound-slot-0 snd-hda-intel
options snd-hda-intel model=dell-m27
``` 3. reboot and retest sound using headphones and speakers
 4. If the dell-m27 alsa-base.conf option does not work, please try one of the following, reboot your pc and retest sound using headphones and speakers.
 Only set ONE model option at a time in the alsa-base.conf file between EACH reboot. Do NOT mix several model options in the /etc/modprobe.d/alsa-base.conf file!
 295 STAC9200
296 ========
297 ref Reference board
298 oqo OQO Model 2
299 dell-d21 Dell (unknown)
300 dell-d22 Dell (unknown)
301 dell-d23 Dell (unknown)
302 dell-m21 Dell Inspiron 630m, Dell Inspiron 640m
303 dell-m22 Dell Latitude D620, Dell Latitude D820
304 dell-m23 Dell XPS M1710, Dell Precision M90
305 dell-m24 Dell Latitude 120L
306 dell-m25 Dell Inspiron E1505n
307 dell-m26 Dell Inspiron 1501
308 dell-m27 Dell Inspiron E1705/9400
309 gateway-m4 Gateway laptops with EAPD control
310 gateway-m4-2 Gateway laptops with EAPD control
311 panasonic Panasonic CF-74
312 auto BIOS setup (default)
 Make sure all channels are unmuted and set to 100% volume (after every reboot) in the gnome-alsamixer application.

Exert from [here]("https://answers.launchpad.net/ubuntu/+source/alsa-driver/+question/131239")


Is it ouputing to both speakers when its plugged in or does it not even detect the external speakers?

---

### Post by kerry_s on 2011-01-31
> **tc101 said:**
> Under Sound Preferences/Output Tab, there is only one device listed.  It is "Internal Audio Analog Stereo".  There is a radio button beside it, but the radio button does not respond when I click it.

I have some speakers plugged into the netbook, and they play, but they do not show up on the output tab under devices.  

This used to work fine.  When the external speakers were plugged in the speakers in the net book did not play.  I am not sure what caused the change.  Maybe some recent ubuntu upgrade.

no, on the bottom. see pic

---

### Post by tc101 on 2011-01-31
kerry_s I don't have the bottom line that I see in your pic.  See my attached pic.

---

### Post by tc101 on 2011-01-31
Caboose885, thanks for taking the time to show me how to do it by modifying the files.  I am not a power user, and I find that kind of complex and intimidating.  I am afraid I would break something.  I will try using the GUI to fix it first, but thanks for your help.

---

### Post by kerry_s on 2011-01-31
> **tc101 said:**
> kerry_s I don't have the bottom line that I see in your pic.  See my attached pic.

what ubuntu version you running? i'm using 10.10

---

### Post by tc101 on 2011-01-31
> what ubuntu version you running? i'm using 10.10

I'm 10.04.  
This started after the last update I did.  I wonder if they added some updates to my 10.04 version that were meant for 10.10.  Anyway, it seems they broke something.

---

### Post by Kirboosy on 2011-01-31
> **tc101 said:**
> Caboose885, thanks for taking the time to show me how to do it by modifying the files.  I am not a power user, and I find that kind of complex and intimidating.  I am afraid I would break something.  I will try using the GUI to fix it first, but thanks for your help.

What kind of netbook do you have?

---

### Post by tc101 on 2011-02-01
> What kind of netbook do you have?

Starling Netbook.  Got it about 3 months ago with 10.04 loaded on it.

---

### Post by kerry_s on 2011-02-01
> **tc101 said:**
> I'm 10.04.  
This started after the last update I did.  I wonder if they added some updates to my 10.04 version that were meant for 10.10.  Anyway, it seems they broke something.

i don't think so, sounds like standard pulse audio update, you can see in my pic what there moving towards.

before that i think you had to install a separate program, try installing "pavucontrol".

---

### Post by isantop on 2011-02-01
It's not likely that you received a Maverick update in Lucid. 

What do you get if you run the System76 Driver?

---

### Post by tc101 on 2011-02-01
> What do you get if you run the System76 Driver?

What is the System76 Driver and how do I run it?

---

### Post by Kirboosy on 2011-02-01
System76 Driver should be under System-->Admin-->System76 Driver

If its not there then try downloading and installing it from [here]("http://planet76.com/repositories/")

---

### Post by tc101 on 2011-02-01
> What do you get if you run the System76 Driver?
.

---

### Post by tc101 on 2011-02-01
I think the problem is that even though the external speakers are plugged into the headphone jack of the Starling, and working fine, the system doesn't recognize them.  Do these screenshots verify that?

---

