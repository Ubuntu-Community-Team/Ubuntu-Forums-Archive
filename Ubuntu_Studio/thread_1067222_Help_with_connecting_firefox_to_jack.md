---
title: "Help with connecting firefox to jack"
date: 2009-02-11
forum: Ubuntu Studio
---

### Post by beattyml1 on 2009-02-11
Hey, does anyone know how to connect firefox to jack
I got rhythmbox working with the following tutorial:
[http://ubuntuforums.org/showthread.php?t=554457&highlight=jack](http://ubuntuforums.org/showthread.php?t=554457&highlight=jack)
thanks:)

---

### Post by thorgal on 2009-02-11
firefox ? what do you mean exactly, the flash plugin ?
If you think about say avi, ogg, pls, m3u, etc, there are a couple of solutions: the mplayerplugin since mplayer can output to jack. Amarok can be called as well for say shoutcast playlist and can be controlled through the addon foxytune. You can also use other apps.

Now, flash stuff: it's the lame duck. I would say you could try oss2jack. That's the hard way but it works fine. Then there's the pulseaudio method. You will need the libflashsupport to have flash plugin output to PA. Then you need to have the PA modules that can communicate with jack. All this is tedious, and honestly, is it worth it ?

My personal setup:
I use jack on a machine dedicated to music prod. I have an pro PCI sound card indexed at hw:1 (ALSA indexing). Jack and clients use that one. The hw:0 is my onboard chip (Intel HDA crap chip) to which I connected a couple of el-cheapo speakers, just for the flashplugin. Doing so allows me to combine the best of both worlds without mixing things up because I don't want this flash crap to pollute my pro audio path and it prevents me from implementing the solutions mentioned above (which I did try and successfully used in the past but it was at the end not worth it).

good luck :)

---

### Post by Stochastic on 2009-02-12
> **thorgal said:**
> Now, flash stuff: it's the lame duck. I would say you could try oss2jack. That's the hard way but it works fine. Then there's the pulseaudio method. You will need the libflashsupport to have flash plugin output to PA. Then you need to have the PA modules that can communicate with jack. All this is tedious, and honestly, is it worth it ?

The only thing I can add to what thorgal said, is that the pulse audio method will most likely be what's adopted into Ubuntu down the road, if any easy setup is...

---

### Post by djwkd on 2010-10-02
You could also download the Windoze version of Firefox, run it under WINE, and set WINE's audio output to JACK.

---

### Post by omegvermelho on 2010-10-02
To run Flash (Assuming jackd is using Alsa driver) - libflashsupport-jack (its in the repos)

I also use Linux based PC (UbuntuStudio and KXStudio) for Audio production and i route everything through jack (qjackctl) ... you can have a track playing in youtube and play along with Guitarix + rakarrack + ardour and a couple more Apps...all running fine

---

### Post by oldmankit on 2010-10-26
Does anyone know which repo libflashsupport-jack is in?  I'm on Maverick and can't find it.

---

### Post by falkTX on 2010-11-10
> **oldmankit said:**
> Does anyone know which repo libflashsupport-jack is in?  I'm on Maverick and can't find it.

I've build it, but launchpad does not allow me to upload it (restricted content/copyright by adobe...)

here's a link for them
32bit - [http://kxstudio.sourceforge.net/repo/pool/free/libflashsupport-jack/libflashsupport-jack_0.0.0+git20090527-0falktx3_i386.deb](http://kxstudio.sourceforge.net/repo/pool/free/libflashsupport-jack/libflashsupport-jack_0.0.0+git20090527-0falktx3_i386.deb)
64bit - [http://kxstudio.sourceforge.net/repo/pool/free/libflashsupport-jack/libflashsupport-jack_0.0.0+git20090527-0falktx3_amd64.deb](http://kxstudio.sourceforge.net/repo/pool/free/libflashsupport-jack/libflashsupport-jack_0.0.0+git20090527-0falktx3_amd64.deb)

although i've compiled them, dont ask me how it works...

---

