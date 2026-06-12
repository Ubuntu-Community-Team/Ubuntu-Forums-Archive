---
title: "[SOLVED] Audacity 1.3.5-beta configuration issue"
date: 2009-03-22
forum: Ubuntu Studio
---

### Post by tbj61898 on 2009-03-22
Hello all,
I wanted to share with you this Audacity troubleshooting, hope it helps some others.

I don't use Audacity on my everyday activity so I can't tell when the problem began.

That said: I start audacity, load a WAV then I press PLAY and a pop up came out: "can't play ... yada yada ... you playback device ...  yada yada... open preferences and set your playback device or adjust frame rate etc.."

I managed to open preferences and, in I/O Audio, I could surely browse Playback device but I just found:
- modem line
- phone line
- some other HDA reference to, still, the internal modem

Obviously none of them were suitable for my playback job.

I did some search on the net but all that came out is:
- remove audacity, remove audacity config file and reinstall
- reinstall ANSA and libasound
- launch aoss audacity (but I don't have such command... and to be honest I don't want it! ;-) just joking.
- reinstall some other things

Unfortunately none of them worked for me.

After some time I got a bit of luck and noticed that "/dev/dsp" was set up as recording device. 
Now some of You may notice this is just wrong, but if I'm just a noob on linux, I'm just lame on linux audio and that means I got NO IDEA of what /dev/dsp is and means. 

But I changed it to a recording line (any valid recording line), restarted Audacity and from that moment on... everything worked very well!

recap: I'm not an expert but it seems that /dev/dsp is a playback device. I don't know WHY and WHO set up /dev/dsp as recording line on Audacity but that caused big troubles with Audacity playback features. I change it to something else (a valid recording line) and that solved the problem.

Hope it helps!

Cheers,
Andrè :popcorn:

---

