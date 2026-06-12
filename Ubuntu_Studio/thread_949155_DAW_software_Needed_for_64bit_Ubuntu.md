---
title: "DAW software Needed for 64bit Ubuntu"
date: 2008-10-15
forum: Ubuntu Studio
---

### Post by otz070 on 2008-10-15
I prefer Open Source or at least freeware though I know that with DAW software Free stuff is hard to find. (I like to spend my money on hardware rather than software, And i am also pretty much poor:() 

Should have vst support

Also is there a wrapper for winvsts to linuxvsts?

---

### Post by Stochastic on 2008-10-15
One word: Ardour
(it's better than pro tools)
VST Support is a little tricky as the vst_sdk cannot be redistributed by any open source project (acording to steinberg) so you need to manually download it and install it yourself - then possibly recompile any program that requires built-in support (though linking through jack to a vsthost is just fine for most).  Check out fst, dssi-vst, or jost for more info on that stuff.

There are other DAWs out there too, but Ardour is the king.

---

### Post by thorgal on 2008-10-16
[www.ardour.org](www.ardour.org) (Stochastic forgot the link)

you may also look into jackaudio.org
jack is the audio server for low latency and frame accurate operations like client synchronization, interoperability between jack audio clients (you can plug inputs and outputs of different applications like you would do with hardware gears). Ardour needs jack to run properly, it won't do anything useful out of the box if jack is not properly installed, configured and running. There is a lot of info in this forum about it.

---

### Post by otz070 on 2008-10-21
Awesome!:guitar:

I've heard about Ardour a couple years ago, then forgot about it, (The link probably got buried under my massive bookmark archive on my old computer. Need to do some system cleaning on there see what forgotton goodies lie within) I was stuck on windows at the time, hoping to someday get a Mac, Didn't happen. Those things are nice but for my requirements, EXPENSIVE. Now I have an almost working linux setup, just need to fill in the blanks!:)

---

### Post by markbuntu on 2008-10-21
Ardour is definitely the way to go with Rosegarden and Hydrogen for the midi, all nicely synced up together through jack. Just a few links to get you thinking:

[http://en.wikipedia.org/wiki/JACK_Audio_Connection_Kit](http://en.wikipedia.org/wiki/JACK_Audio_Connection_Kit)

[https://help.ubuntu.com/community/UbuntuStudio/GettingStarted](https://help.ubuntu.com/community/UbuntuStudio/GettingStarted)

[http://www.ubustu.com/globe/2007/05/29/how-to-configure-jack-in-ubuntu-studio/](http://www.ubustu.com/globe/2007/05/29/how-to-configure-jack-in-ubuntu-studio/)

[http://hubpages.com/hub/Recording-in-Linux-aka-Free-and-Open-Source-Digital-Audio-Workstation](http://hubpages.com/hub/Recording-in-Linux-aka-Free-and-Open-Source-Digital-Audio-Workstation)

[https://help.ubuntu.com/community/HowToQjackCtlConnections](https://help.ubuntu.com/community/HowToQjackCtlConnections)

[http://www.ubustu.com/globe/2007/09/19/how-to-sync-hydrogen-with-ardour/](http://www.ubustu.com/globe/2007/09/19/how-to-sync-hydrogen-with-ardour/)

---

