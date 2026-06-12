---
title: "Dell Chromebook 11 (Candy-2015) - Hardware problems"
date: 2015-10-01
forum: Ubuntu/Debian BASED
---

### Post by christian83 on 2015-10-01
Hello everyone!,

I am new to this forum so I hope I am doing everything as the rules say! I just bought a Dell Chromebook 11 (Candy 2015 edition) and I managed to remove the WP screw and install Backbox on it. Since i heard that Backbox was based on ubuntu I thought the best place to ask would be here. The problem I have is the following:

- My touchpad does not work. (If I need to run some commands and post it here feel free to ask! I am quite new to Linux)
- It also seems that the speaker is not recognized (cannot play any audio with aplay, even with sudo rights)

I hope you guys can help me out!

Christian

---

### Post by tgalati4 on 2015-10-01
Welcome to the forums.

The Dell Chromebook may have some proprietary hardware without the necessary Linux modules needed to operate them.  

Open a terminal and post the following:

```
xinput list --long
```

For the sound:

```
aplay -l
```

A review of how the Dell Chromebook handles full Linux would be helpful.

---

### Post by christian83 on 2015-10-02
Hey!

Thanks a lot for the help! For the xinput command the results can be found in this pastebin:

[http://pastebin.com/X5hjKYJd](http://pastebin.com/X5hjKYJd)

The aplay - l command output was this:

**** List of PLAYBACK Hardware Devices ****
card 0: PCH [HDA Intel PCH], device 3: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: PCH [HDA Intel PCH], device 7: HDMI 1 [HDMI 1]
  Subdevices: 1/1
  Subdevice #0: subdevice #0


Hope this helps! 

Ps. Is the threadpost length unlimited? Otherwise I could paste it as inline code in a message here.

---

### Post by tgalati4 on 2015-10-02
Install *mplayer* and try to play a file:

```
sudo apt-get install mplayer2
mplayer anymp3filethatyouhave.mp3
```

The reviews seem to indicate that the built-in speakers are loud, and Intel HDA sound hardware is generic.  But, the sound devices show up as HDMI.  Try plugging your HDMI port into a TV and play some sounds.

Also, bring up *alsamixer* and play with the settings:

```
alsamixer
```

Your *xinput* output looks OK, however some Dell Chromebooks come with a touchscreen.  Does your notebook have a touchscreen?  If so, can you turn it off in BIOS?  Sometimes a touchscreen with interfere with the trackpad--it may require extensive tweaking to get both to work.

Try plugging in a USB mouse and see if it works normally.

---

### Post by christian83 on 2015-10-02
Thanks a lot for your response!:

I downloaded mplayer and when I played an MP3 I had no sound. However when I plugged in my monitor and played a sound, it did play a sound. So the soundcard is working, just for some reason it doesn't see my built in speakers as an output device.

About the xinput, I forgot to mention that the xinput already contained my wireless Microsoft mouse. It does work with that mouse. The Dell Chromebook I have doesn't have a touch screen by the way!

Christian

---

### Post by tgalati4 on 2015-10-02
Install all the *pulseaudio* tools and play with them, especially pulseaudio device chooser.

> 
padevchooser - PulseAudio Device Chooser
paman - PulseAudio Manager
paprefs - PulseAudio Preferences
pasystray - PulseAudio controller for the system tray
pavucontrol - PulseAudio Volume Control
pavumeter - PulseAudio Volume Meter


Disconnect the wireless mouse and run the xinput list again.  I think the mouse is intercepting the touchpad inputs.

---

### Post by christian83 on 2015-10-05
The pastebin link for the Xinput is here again:

[http://pastebin.com/zG7cSAxz](http://pastebin.com/zG7cSAxz)

I also installed the pulseaudio tools but it looks like it doesnt recognize my builtin speakers. (Only the HDMI ones), here a screenshot for it:

[IMG]http://i59.tinypic.com/dqnayr.png[/IMG]

---

### Post by Bucky Ball on 2015-10-05
*Thread moved to **Ubuntu/Debian BASED**.*

Welcome. Backbox may be based on Ubuntu but is not officially supported by Canonical or in the main areas here. 

Good luck.

---

