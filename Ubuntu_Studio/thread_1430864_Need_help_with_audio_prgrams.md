---
title: "Need help with audio prgrams"
date: 2010-03-15
forum: Ubuntu Studio
---

### Post by chkneater on 2010-03-15
Hi, I'm using ubuntu 9.04 studio version.  I mostly want to use it for audio, but I can't get anything working.  I have a SBLive Platinum soundcard, but the LiveDrive hasn't been working so I'm using the mic input from my guitar.  I can play through the computer but it adds a LOT of gain to it and I'm not able to record AT ALL on anything, Audacious, Ardour.  I can't even get JAck running right.  I can get it to start, but I can't even get simple apps like the keyboard emulator to work even though it's connected to TIMIdity in the patchbay and the line is green.  I have been able to use the keyboard and JACK before.  CAn anyone help or point me to a GOOD tutorial or manuals I could download? I don't understand much of this audio stuff.  Thanx for your help!

---

### Post by cchhrriiss121212 on 2010-03-16
If you are going to record guitar you will need a preamp in order to get a decent sound. Try using patchage to connect a virtual keyboard to Zyn, without using the timidity connections.

---

### Post by trulan on 2010-03-16
Autostatic said (in another thread) he would upload a midi how-to to his youtube channel:
[http://www.youtube.com/user/autostatic3000](http://www.youtube.com/user/autostatic3000)

Here's the thread, I posted a somewhat lengthy explanation here:
[http://ubuntuforums.org/showthread.php?t=1428115](http://ubuntuforums.org/showthread.php?t=1428115)

I don't know what LiveDrive is, but it sounds like you either need to hook up your guitar into a line input or route it through an external mixer, so you can get the proper record level.

---

### Post by AutoStatic on 2010-03-17
> **trulan said:**
> Autostatic said (in another thread) he would upload a midi how-to to his youtube channel:
[http://www.youtube.com/user/autostatic3000](http://www.youtube.com/user/autostatic3000)
[Tiny Tutorial: Connecting a MIDI USB Keyboard to a Softsynth in Ubuntu]("http://www.youtube.com/watch?v=kBEzMC35gt8")

---

### Post by chkneater on 2010-04-01
From what I can tell, the purpose of the Live Drive is just to provide an area on the front of the computer to make MIDI connections and stereo and RCA input/outputs and control the volume from the front.  It's connected to the sound card with a ribbon cable.  The sound card itself can be used with out the Live Drive.  The card has the normal mic and line I/O and a digital in.  My expectation (naive as it was) was that with the full size stereo inputs on the Live Drive I could use the line out from my guitar amp and record that route.  I have had no luck getting any output using the inputs of the Live Drive.  Using the mic input on the card, I can get output through the system speakers and control the gain and boost in alsa mixer just fine.  However Audacious won't pick up anything and Jack will connect and I get no Xruns, but there is nothing being monitored or recorded.

---

