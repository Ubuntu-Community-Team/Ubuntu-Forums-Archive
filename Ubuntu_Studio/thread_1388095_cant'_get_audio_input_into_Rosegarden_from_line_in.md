---
title: "cant' get audio input into Rosegarden from line in"
date: 2010-01-22
forum: Ubuntu Studio
---

### Post by duncanmaybury on 2010-01-22
Hi Folks
I have Karmic ubuntustudio, I am new to this wonderful world of Ubuntu/Linux
I want to use Rosegarden to trigger my Roland Sampler via midi and record the audio back into Rosegarden.
I was not getting any sound out when I fed it into my sound card(Audigy Platinum ex) from my sampler, I looked around and found the stuff about pulse being a potential problem, so I did this:

```
sudo apt-get install gstreamer0.10-alsa gnome-alsamixer
sudo apt-get purge gstreamer0.10-pulseaudio vlc-plugin-pulse pulseaudio
```Now I have sound coming through my system from my external sampler, using the gnome alsa mixer, great, thanks.
Rosegarden doesn't seem to be coming into contact with the audio input. I don't know how to feed it into rosegarden.
I'm not sure what 'system' is in the JACK screen.
When I play a track in Audacious and connect it to Rosegarden the signal shows up in rose garden.
So simply put, how do I get my signal into Rosegarden from the inputs on my sound card?
Attachment of JACK view.

---

