---
title: "HDMI audio on Pangolin Performance laptop"
date: 2010-05-02
forum: System76 Support
---

### Post by Mooseknuckle on 2010-05-02
Hello, I just upgraded my laptop to 10.04, and I can't seem to get Audio to work over HDMI anymore. 

In the sound application, there is an analog output + HDMI output item, and just an HDMI output item, and none of them seem to carry sound to my television.   Before the update this worked.

Any clues?   Thanks so much!

---

### Post by Mooseknuckle on 2010-05-02
Ok I fixed this by going into alsamixer and unmuting one of the entries ('m') ...

---

### Post by fj401971 on 2010-07-15
Confirmed.  

Model: panp4n

HDMI audio works by doing the following....

Preferences >> Sound >> Hardware 

Select "Digital Stereo (HDMI) Output" Profile


Open a terminal.

Type the following:  alsamixer

Using the right key, select "S/PDIF 1"

Push the 'm' key to unmute that selection.

Exit out...should be working.

---

### Post by Groucho Marxist on 2010-07-16
> **fj401971 said:**
> Confirmed. 
 
Model: panp4n
 
HDMI audio works by doing the following....
 
Preferences >> Sound >> Hardware 
 
Select "Digital Stereo (HDMI) Output" Profile
 
 
Open a terminal.
 
Type the following: alsamixer
 
Using the right key, select "S/PDIF 1"
 
Push the 'm' key to unmute that selection.
 
Exit out...should be working.
 
Thank you for posting this! I'm definitely going to try it when I get back from my vacation.

---

### Post by v1ad on 2010-07-16
mark solved please.

---

### Post by Jozza The Wick on 2010-12-05
After following these instructions, I still can't get HDMI audio out through my monitor. I have unmuted the SPF channels in alsamixer and I know the monitor works because I use the same HDMI input (and cable) for my Xbox (and obviously get sound).

In 'Preferences >> Sound >> Output', I have two options, 'Internal Audio' and 'Internal Audio Digital Stero (HDMI)'. I assume the later needs to  be selected. However, even after this is done, the following command:

```
aplay /usr/share/sounds/alsa/Front_Center.wav
```

still plays output through the laptop speakers.

Anyone have any suggestions?

---

### Post by isantop on 2010-12-06
If you open an audio file, where does it play from.

You may also need to set your hardware profile. To check this, in the Sound Preferences Dialog, go to the Hardware tab. Click on the HDMI device, then ensure that "Profile for the selected device" is set to "Digital Stereo (HDMI) Output".

---

### Post by Jozza The Wick on 2010-12-06
isantop - my hardward profile is set correctly, to 'Digital Stero (HDMI) Output'. When I open an audio file, I usually use VLC (did you mean what application do I use to play the file?)

When the file is playing the sound comes out of the laptop internal speakers (or more usually the analog speakers I have plugged into the laptop headphone jack).

My audio is rather messed up at the moment - for example, the volume indicator on the panel, while allowing me to move the slider up and down, doesn't have any impact on the volume out the outputted audio at all.

I've tried to completely purge the audio systems (PulseAudio & Alsa) and restore to the installed defaults, but no luck - this is where I ended up. Is there any easy way to restore audio defaults in 10.04 before we deal with the HDMI issue? There may be too many unknowns with my current half-broken setup otherwise..

---

### Post by isantop on 2010-12-08
What model is your Pangolin. HDMI audio won't work on PanP4n, PanP5, and PanP6 models due to a limitation of Ubuntu. It will work in the next version of Ubuntu.

---

### Post by Jozza The Wick on 2010-12-09
I have a Panp4n, but a response from fj401971 earlier in this thread (and Mooseknuckle, who started this thread), seem to indicate that they got it working...

I'm using 10.04. By 'next version', do you mean 10.10, or the upcoming 11.04?

---

### Post by Jozza The Wick on 2010-12-14
Can someone from System76 confirm whether HDMI audio works on the Pangolin PanP4, under 10.04? Earlier posts in this thread seem to indicate it does.

If System76 testers can't get HDMI Audio working on Panp4 on Ubunt 10.04, could someone please clarify what version isantop is referring to?

Thanks very much to all! :D

---

