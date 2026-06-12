---
title: "How to create a surround-device using jack and alsa-plugin?"
date: 2013-03-13
forum: Ubuntu Studio
---

### Post by vitellotonato on 2013-03-13
Hi,

All new here and I need some help ;)

I am using jack together with brutefir  to listen to music for a rather long time now on a dualcore atom  machine. It handles up to eight channels without problems.

Now I  want to kick the receiver out of my home-cinema setup and go for the  brutefir way here as well. I just got a m-audio fasttrack ultra 8R, wich  works out of the box with jack. Very good. The problem now is, that I  use xbmc for video playback and xbmc simply has no option to output to  jack. I had a similar problem with my audio-player and solved it using  the alsa-bridge (alsa_in and alsa_out) to connect any alsa-based player  to jack. The alsa-bridge is using stupid amounts of processing-power to  convert even 48kHz input to 48kHHz output, which is total nonsense! I  could live with that since I only had two input-channels. My video-setup  will have up to six input-channels and I want to use the alsa-plugin  this time.

Now I easily managed to set up a virtual two-channnel  alsa-device which outputs to jack using /etc/asound.conf, but I can't  figure out the syntax to create a valid 5.1 surround-device which xbmc  needs. I used something like this and got two channels:

pcm.jack {
     type jack
     playback_ports {
         0 system:playback_1
         1 system:playback_2
         2 system:playback_3
          3 system:playback_4
     }
     capture_ports {
         0  system:capture_1
         1 system:capture_2
     2 system:capture_3
         3 system:capture_4

     }
 }

What I need is  all of the 6 channels to be available seperately in order to route them  through jack to brutefir and from there either directly to the outputs  of the interface or through jack again and from there to these outputs.

Is  there anybody around that would happen to know how to achieve this? I'd  be so happy!

Best regards and thanks in advance!

---

### Post by Sylos on 2013-03-16
Hello.

I've never tried what are you are attempting, but, on my many travels through alsa pages for other purposes I have seen some stuff on it. You might start here and see what you get:

[http://drona.csa.iisc.ernet.in/~uday/alsamch.shtml](http://drona.csa.iisc.ernet.in/~uday/alsamch.shtml)

Good luck.

---

