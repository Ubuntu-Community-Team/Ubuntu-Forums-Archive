---
title: "MIDI Input + MilkyTracker?"
date: 2010-03-03
forum: Ubuntu Studio
---

### Post by tacticalbread on 2010-03-03
I've gotten MIDI input (from my USB controller) to work with pretty much everything I've tried, but it will not work with MilkyTracker. I patch the output of my MIDI controller to the input of MilkyTracker in AConnectGUI (the same way I did it with other programs) and still nothing. Playing the keyboard works just fine, so I know it's not a problem with MilkyTracker.

I had it working (briefly) at one point, but I've tried numerous times again, to no avail.

Any ideas what the problem could be?

---

### Post by AutoStatic on 2010-03-03
Which version of MilkyTracker? MilkyTracker acts a bit weird when it comes to MIDI, I have some issues with it too, I can't disconnect and reconnect MIDI connections with MilkyTracker, then  I have to restart the program to get MIDI working again.
But it should work, see attached screenshot.

---

### Post by tacticalbread on 2010-03-03
AS far as I know, the latest version, I installed it from the repositories.

And somehow I got it working, I guess by restarting MilkyTracker a few times.

Well, thanks for your help. :)

---

### Post by AutoStatic on 2010-03-03
You're welcome. It's got something to do with the MIDI implementation of MilkyTracker. I use a newer version than the one in the repo's ([0.90.85]("https://launchpad.net/~philip5/+archive/extra/+sourcepub/946246/+listing-archive-extra")) and MIDI is still a bit problematic.

---

### Post by Found on 2011-05-18
For everyone else who's trying to connect a midi keyboard to a milky tracker:

Versions earlier than 0.90.85 will not work (or work poorly). Download the latest version available a configure your routing via the tools of your sound driver. In my case it was ALSA and the tool is called aconnect (aconnectgui is also available for user interface).

find out your midi inputs by executing:
```
aconnect -li
```
and your inputs by typing:
```
aconnect -lo
```

Now you should be able to see what channel your device is using. In my case my AKAI LPK25 was on channel 20:0 and my Midi Through was on channel 14:0. If you want to use any other MIDI synthesizers (vkbd, qsynth i.e.) they will be in listed as well.

What you need to do is connect your midi device to the output software you're willing to use. You can also vreate multiple connections. Like so:

```
 aconnect 20:0 14:0 
```
This will make milkytracker receive midi signals from your device.

```
 aconnect 20:0 128:0 
```
And this will connect your device to any other synthesizers you might wanna use (note: channel 128:0 might be different for your system, look in aconnect -lo/ -li)

There is also a feature that supports keys velocity in milkytracker. Run it with -recvelocity command.

---

