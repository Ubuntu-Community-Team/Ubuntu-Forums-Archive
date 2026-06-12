---
title: "Fix internal mic for use with Skype"
date: 2011-04-17
forum: Tutorials
---

### Post by ZekeGraal on 2011-04-17
Well, those of you that have installed Skype on your favourite Ubuntu family distro may have run into this problem:

I have all of my audio devices up and running, but my microphone captures no sound input!

Thankfully, the solution is only one package and a slider drag away!

NOTE: I have only experienced this problem with built in microphones, but if your internal mic has a left and right channel, like on the Dell Studio laptop I own, you shouldn't have to worry about any of the contents of this guide. External mics should work without problems in Skype as long as you have chosen them as your default input device on your distro, not on Skype because if you have PulseAudio, it is the only choice on Skype.

Using the package manager for your Ubuntu distro, find the package 'PulseAudio Volume Control,' and install it.

If you are more familiar with the Terminal, you can run this instead:

sudo apt-get install pavucontrol

Next run that program. It should be under Menu->Multimedia-> Volume Control. (That is where it is on Kubuntu, I believe Ubuntu calls it 'Pulse Audio Volume Control' under the gnome menu. I switched to Kubuntu this year from Ubuntu, so I know where it is, but my main knowledge is KDE.)

Choose the 'Input Devices' tab. My netbook has the mic labeled as 'Internal Audio Analog Stereo, and yours may be different.

Now make sure the option 'Lock Channels Together' is not chosen. Drag the 'Front Left' slider all the way to the left. If the little bar below it doesn't move to indicate sound input, drag the 'Front Right' slider to the left instead.

There you go! Now you can log in to Skype and ring up the nice Echo Sound Test Service lady to see if it's working!

TROUBLESHOOTING F.A.Q.:

-Problem: My device is not shown under the 'Input Devices' tab!
-Solution: at the bottom, click on the dropdown box next to 'Show:' and select 'Hardware Devices'

-Problem: The Left and Right Front sliders move together!
-Solution: You did not disable the 'Lock Channels Together' option like I said to earlier.

-Problem: I am under the 'Input Devices' tab, and have chosen to show hardware devices, but there is still nothing there!
-Solution: Go to the 'Configuration' tab and choose 'Analog Stereo Duplex'

This is my first 'howto thing.' I've been running Linux for about a year and a half, so it's good for Linux noobies that need a simple fix.

Feel free to make any comments/suggestions.

~Zeke

---

### Post by redrummy on 2011-07-14
I've been banging my head against this one for a couple days with my AO751h and this fixed it. Thanks you! But what bizarre solution. :-s

---

### Post by Gatsby7 on 2011-07-16
Thanks a lot 4 your help! Works like a charm

---

### Post by Rodney9 on 2011-07-17
Thank You So Much !

---

### Post by danielsbrewer on 2011-07-18
But what are you suppose to do if a program, in this case Google hangout, keeps resetting the audio configuration to how it was by default i.e. locked L and R channels, hence stopping the microphone working every 30 seconds.

---

### Post by Boundless316 on 2011-08-06
> **danielsbrewer said:**
> But what are you suppose to do if a program, in this case Google hangout, keeps resetting the audio configuration to how it was by default i.e. locked L and R channels, hence stopping the microphone working every 30 seconds.

Indeed, I have the exact same problem and it's about to drive me bananas. I've tried disabling Echo cancellation (don't really use it anyway since I always use headphones) but that doesn't help. Is there a way to prevent applications from making changes to the sound settings?

---

### Post by danielsbrewer on 2011-08-08
To turn off autoadjust by google talIk plugin:
> cd ~/.config/google-googletalkplugin # get to google chat's directory
cp -p options options.bak # make a backup before changing stuff..
gedit options # edit the config file
If you don't have file named options in this folder create one..
Add following line to this file..
audio-flags=1 

This seems to work for me.

---

### Post by majedaly on 2012-05-21
Thanks, that solved my problem on Acer netbook

---

