---
title: "Jack turned into a mouse"
date: 2011-05-16
forum: Ubuntu Studio
---

### Post by dwftime on 2011-05-16
Last week I purchased a new video card (nvidia GTX 550 TI). I was running 10.10 and it didn't work. I took what I thought was the path of least resistance, since I already had 11.04 downloaded and on a flash drive, and did the upgrade. All seemed to work fine. I needed to reinstall the ubuntu-studio packages, which went fine. I then fired up jack and ardour. The strangest thing happened. The output had really low volume. I have a M-Audio Mobile Pre USB interface. It works, both input and output, it just has very little volume. I have to crank the mixer all the way up to even hear it. I have tried multiple things to no avail. Went directly into my monitors, same result. I even threw my Sound Blaster Live into the rig and ran it with jack. It works fine and the volume is as expected. I ran the Sound Blaster through the same channel on the mixer and it works great. This issue is isolated to the m-audio it appears.

I am kind-of at a loss here. I don't know how to proceed to fix this. I have tried multiple configurations in jack and nothing seems to eliminate the issue. I am now digging into drivers for the m-audio. Maybe a recent update has broken it. One other odd thing, when I run Meterbridge it shows the audio complete maxed out. Not sure if that is related. In Ardour there is no clipping according to the mixer.

I am not sure what to do at this point. I am considering downgrading everything. Any help would be greatly appreciated. I am in the process of finishing up an album and have been working on a video (hence the video card upgrade). I am sure it is something simple with jack or a driver issue that I am missing. Thanks.

---

### Post by sgx on 2011-05-16
Maybe try alsamixergui, in case it finds something your current
mixer is misrouting. There is also mudita24, an updated envy24control
mixer, for maudio products. Should be an easy compile. Or iys in
AVLinux 4.2

Try sending the audio to timemachine, or other jackd app with an audio input, in case there is an oddity in the ardour setup.
Cheers

---

### Post by dwftime on 2011-05-16
sgx,

Thanks for the reply. I tried plugging my guitar in and running rakarrack with no Ardour and then Hydrogen alone with the same results. The current envy24control isn't compatible with my interface. Looking into AVLinux now. Thanks again.

---

### Post by Pablo_F on 2011-05-17
@sgx 

Afaik, envy24control/mudita is for audio cards with the envy24 chipset (which are supported by the snd_ice1712 alsa module) including but not limited to some m-audio products. They are all PCI cards.

You can see the cards supported by this module here (search /1712):  

zless /usr/share/doc/alsa-base/driver/ALSA-Configuration.txt.gz

@dwftime

I am not sure if there is an alsa mixer for this card, but could you give the output of this informative command?

amixer

You could also try searching/asking in the alsa users mailing list because this seems like a problem either in hardware or in low level software. You seem to blame jack but I don't think so. You can also try speaker-test in a terminal. 

Cheers, Pablo

---

### Post by dwftime on 2011-05-18
I wanted to let you guys know that I solved this. alsamixergui only showed a master volume for pulse. I dug around (apt-cache search alsa | grep mixer) and found qamix. qamix jumped off the monitor, but after moving some things around and arranging workspaces I found the m-audio. All the audio was turned down. I turned it up while running jack and there it was. Very odd, I have never had to do that in a Jack setup before. Thanks to both of you. You gave me enough info to figure this out.

---

