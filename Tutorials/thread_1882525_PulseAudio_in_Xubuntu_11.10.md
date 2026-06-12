---
title: "PulseAudio in Xubuntu 11.10"
date: 2011-11-17
forum: Tutorials
---

### Post by Tinos on 2011-11-17
Hi

I just installed Xubuntu for the first time and getting audio to work was non-trivial so figured I'd post some tips. My situation is I have a 5.1 + mic sound card (Sound Blaster). Getting things to work in Ubuntu & Kubuntu was straightforward; but Xubuntu is harder (I'm with Torvalds [[Link]("http://digitizor.com/2011/08/04/linus-torvalds-ditches-gnome-for-xfce/")], though, that Xfce is the way to go).
[LIST=1]
[*]Make sure pavumeter is installed. It's the PulseAudio Volume Control.
[*]Use it to configure your sound-card to the right option. For me it's
Analogue Surround 5.1 Output + Analogue Stereo Input
which is a bit strange given the mic is mono. A simple stereo sound card is stereo duplex. pavumeter will be under Multimedia in the Applications Menu (top left).
[*]You need to make sure everything is configured correctly under the Alsa Mixer (also under Multimedia). You need to pick the relevant controls using the "Select Controls..." dialogue box.
[*]Make sure you check the boxes for "Analogue Source" and "Shared Mic/Line in". These have to be set to mic or else the mic won't work (this took me a while to work out). Microphones require a DC bias, so the distinction is important.
[*]Check the input and output is working correctly in pavumeter.
[*]You can set gmusicbrowser (which I actually quite like, despite no WMA support) to play/pause when you hit the Pause key on your keyboard by going
Settings>>Settings Manager>>Keyboard>>Application Shortcuts>>Add
Then the command is
gmusicbrowser -cmd PlayPause
And then hit OK and hit Pause/Break on the top-right of the keyboard. You can also set the thunar command to go with window key + e for  "Explorer" type behaviour.
[/LIST]

Now to get my Hantek oscilloscope working...

---

