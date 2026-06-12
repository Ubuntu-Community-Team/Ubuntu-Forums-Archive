---
title: "full duplex issue w/ M-Audio Delta 2496, Ubuntu Studio 12.04"
date: 2013-08-27
forum: Ubuntu Studio
---

### Post by louh2 on 2013-08-27
1. I don't have full duplex.  I can either listen to tracks being played (mp3, etc) or I can listen to external devices (drum machine to mixer to line channel inputs).  Cannot listen to both simultaneously.  Digital faders do show movement to the mp3 output when set to listen to external ins, just can't hear it.

2.  Line (or h/w) inputs are mono.  Doesn't matter what I have running through the mixer.

---

### Post by tgalati4 on 2013-08-28
You have to set patches using your audio control panel.  They are not connected automatically.

mudita24 - ALSA GUI control tool for Envy24 (ice1712) soundcards

---

### Post by louh2 on 2013-08-28
Patches -- what do I use to create them?  I have qJackCtl, do I use  that?  If not, what do you propose I use as I see nothing about making  patches in Mudita24 or in any other mixer interface installed.

---

### Post by louh2 on 2013-08-28
Looks like I've figureds some of this out.  The mono issue seems to have been fixed by command line input from a post about a similar problem and I have created sockets for all of the ins/outs to all of the audio softwares I will be using in QJackCtl.  Connecting them up in a way that makes sense is going to take some time and experimentation.  It's not the progress distance I want now but it is progress.  Thanks for the suggestions.

---

### Post by tgalati4 on 2013-08-28
I have a delta-66 card and I use the envy24control to set the patches.  Jack uses a different framework to set the patches.  Basically, you need to connect the output streams to the input streams to form a "monitor" or "feedback" channel.  With cheap soundcards, there is normally a monitor channel built in with a volume slider, so you can hear your self talking on a voice call.

When you are recording in a studio, there are usually several ways to monitor the recording outside of the sound card.  You normally use those, so that you can dedicate all of your CPU cycles to accurately capturing the inputs.  Monitor channels are secondary in importance.  Use Ardour or Audacity and you can monitor the recording from there.

---

### Post by louh2 on 2013-08-28
From all that I have read mudita24 has taken the place of envy24ctl.  Unfortunately there is no patching that I can find in there.  I can manually select what I'm monitoring but this is pretty useless when recording and there is no midi connectivity at all.  How do you set patches then if using qjack is not preferred becaue I do not want the overhead as well?  I would post screen shots of mudita24 if it would help.

---

### Post by tgalati4 on 2013-08-28
I have my Delta66 card on an older distro, so I don't know the differences between envy24control and mudita24.  But there is a patchbay/router tab that you make your connections.  Just like a real, analog mixing board--but without the wires.  Once you have made your patches, you can save them in profiles--like recording, game-playing, music-playback, etc.

Doesn't mudita24 have a patchbay tab?

---

### Post by louh2 on 2013-08-28
Yes there is a patchbay tab with a line of faders, not at home right now so can't recall the names given to them, but there is no way to utilize them.  There are only a couple of settings there for each, ie mute, gang, that's about it.  There is no menu option to create/redirect connections like patches.  In fact there are no patch creation tools in any of the tabbed selections.  I have been through each and every section carefully looking for these.

---

### Post by tgalati4 on 2013-08-29
It's possible that your card doesn't support the patch bay feature.  The Delta2496 uses the same chipset as the Delta66, but the audio routing is different.

---

### Post by louh2 on 2013-08-29
So does that mean that I must use qjackctl for assignment of input and output?

---

### Post by tgalati4 on 2013-08-29
That might be your only option.  Some reading:  [https://help.ubuntu.com/community/HowToQjackCtlConnections](https://help.ubuntu.com/community/HowToQjackCtlConnections)

---

### Post by louh2 on 2013-08-29
Giving that a try, made all the patches for the various audio packages I want to use.  Thanks for all the suggestions and help.

---

### Post by louh2 on 2013-09-01
Well, as in my post regarding setting up of QJackCtl, that didn't solve the problem.  The problem was in not understanding how the card is setup.  There are analog inputs and outputs and there is a digital mixer that handles these.  I was trying to get analog inputs to provide both input and output which they cannot do.  So after a large amount of toying around with the connection options I found if I selected the digital mixer I could then use a software mixer/control utility like ALSA mixer to setup up inputs and outputs.  This did the trick.  I am able to monitor tracks that are playing and recording simultaneously now.  Finally able to get passed all this tedious stuff and get on with the fun!  Thanks again.

---

