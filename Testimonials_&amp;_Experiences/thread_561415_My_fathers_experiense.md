---
title: "My fathers experiense"
date: 2007-09-27
forum: Testimonials &amp; Experiences
---

### Post by olskar on 2007-09-27
Hi, I installed feisty on my fathers computer and he liked it a lot, even tough there were no sound and when he tried to install proprietary ati drivers from the proprietary drivers manager all went black. Of course he didnt want to use an OS without sound and hoped it would be solved in gutsy. The final release is now drawing closer and still no sound. He updates every day in hope to hear the "jungledrums" but still no luck..

I really dont know why there is no sound, hope it will be solved in gutsy+1...

---

### Post by dougfractal on 2007-09-27
So what happens when you

alt+f2
**gnome-sound-properties**

And run the tests.

in terminal 
lspci -nn | grep -i audio

---

### Post by lancest on 2007-09-28
You mean no startup Ubuntu sound? That will come soon. If you truly don't have sound it's very cheap to replace the sound card or do install from Alsa. (works every time for me)

sudo apt-get install build-essential
wget [ftp://ftp.alsa-project.org/pub/driver/alsa-driver-1.0.14.tar.bz2](ftp://ftp.alsa-project.org/pub/driver/alsa-driver-1.0.14.tar.bz2)
tar xjf alsa-driver-1.0.14.tar.bz2
cd alsa*
./configure
make
sudo make install
then reboot and see if it works. you may have to run

Code:

alsamixer

and set the volume levels

---

### Post by olskar on 2007-09-28
> **dougfractal said:**
> So what happens when you

alt+f2
**gnome-sound-properties**

And run the tests.

in terminal 
lspci -nn | grep -i audio

Get this when I run the tests, and I have filed a bug:
```
audiotestsrc wave=sine freq=512 ! audioconvert ! audioresample ! gconfaudiosink: Internal GStreamer error: state change failed.  Please file a bug at http://bugzilla.gnome.org/enter_bug.cgi?product=GStreamer
```

And this from your second request:
```
03:0a.0 Multimedia audio controller [0401]: Creative Labs SB X-Fi [1102:0005]
```

---

### Post by olskar on 2007-09-28
> **lancest said:**
> You mean no startup Ubuntu sound? That will come soon. If you truly don't have sound it's very cheap to replace the sound card or do install from Alsa. (works every time for me)

sudo apt-get install build-essential
wget [ftp://ftp.alsa-project.org/pub/driver/alsa-driver-1.0.14.tar.bz2](ftp://ftp.alsa-project.org/pub/driver/alsa-driver-1.0.14.tar.bz2)
tar xjf alsa-driver-1.0.14.tar.bz2
cd alsa*
./configure
make
sudo make install
then reboot and see if it works. you may have to run

Code:

alsamixer

and set the volume levels

I will try to install from alsa..don treally know how to replace the soundcard, it seems it is connected to a lot of things inside my computer..not lika a usual soundcard in other words

---

### Post by olskar on 2007-09-28
Just found this..
[http://opensource.creative.com/soundcard.html](http://opensource.creative.com/soundcard.html)
but its only for 64 bit :(

---

### Post by dougfractal on 2007-09-28
It doesn't look good  :-( from googleing "Creative Labs SB X-Fi ubuntu"


[http://ubuntuforums.org/archive/index.php/t-239981.html](http://ubuntuforums.org/archive/index.php/t-239981.html)
> As far as I know, ALSA does not support the Sound Blaster X-Fi cards AT ALL. And Creative's own [http://opensource.creative.com/soundcard.html](http://opensource.creative.com/soundcard.html) says "The X-Fi series of products are not supported under Linux. Closed-source drivers will be available for the X-Fi series of sound cards in the second quarter of 2007. These drivers will have full support for ALSA (playback, recording, mixer, MIDI, synthesis) and OpenAL 1.1 (with EAX effects)." ... However, this: [http://system76.com/product_info.php/cPath/2/produ](http://system76.com/product_info.php/cPath/2/produ) cts_id/173 clearly shows "7.1 Surround Creative Sound Blaster X-Fi Xtreme" as a configuration choice under the Sound option.

---

### Post by terry_gardener on 2007-09-29
i also have this problem with the x-fi soundcard and i am using the motherboards onboard sound at the moment. quite disappointed that creative only released the 64bit vers as i use the 32 bit ubuntu. hope thyey release the 32 but versions

---

