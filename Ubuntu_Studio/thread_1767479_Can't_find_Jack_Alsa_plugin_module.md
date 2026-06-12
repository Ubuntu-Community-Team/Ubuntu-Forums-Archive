---
title: "Can't find Jack Alsa plugin module"
date: 2011-05-25
forum: Ubuntu Studio
---

### Post by mikee55 on 2011-05-25
Hi I installed Jack Alsa Module from Synaptic, and can't get it going. I want to record my stream from MPlayer, but can't find the right thread in Search to set this up. Can you help, please?

Mike:guitar:

---

### Post by Pablo_F on 2011-05-26
Hi Mike,

Skipping your question, mplayer has an excellent native jack support. 

If you want to try from a terminal: 

mplayer -ao jack /path/to/the/file

You can "jackify" mplayer permanently by editing ~/.mplayer/config and adding this line:

ao=jack,pulse

If jack is not active, mplayer will try pulseaudio (I am assuming you didn't disabled pulseaudio in your system).

There will probably be another configuration file for the mplayer gui. In my sistem I have ~/.mplayer/gui.conf and there is a line that reads:

ao_driver = "jack,pulse"

Cheers, Pablo

---

