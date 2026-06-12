---
title: "Sudden loss of sound"
date: 2009-06-11
forum: System76 Support
---

### Post by ewg on 2009-06-11
Ubuntu 9.04, Sable

I was watching a streaming video from a newspaper when the sound just stopped. Now I have no sound on any application (rhythm box, movie player). 

Card is recognized:
**** List of PLAYBACK Hardware Devices ****
card 0: NVidia [HDA NVidia], device 0: ALC861 Analog [ALC861 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 1: ALC861 Digital [ALC861 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

I have previously used both ALSA and OSS. Now nothing works.

Thanks for any suggestions,

---

### Post by pmlxuser on 2009-06-11
have you tried rebooting your machine?? (sorry not thinking that you are dumb but sometimes thats all that is needed.)

---

### Post by ewg on 2009-06-11
Thanks for replying,
yes I have actually started and restarted a few times since this happened. Speakers are working. I can hear "pops" and other static when I turn the volume switch.

---

### Post by pmlxuser on 2009-06-11
i would try to uninstalling  gstreamer ** plugins and reinstall them.

---

### Post by thomasaaron on 2009-06-11
Make sure your PCM slider is all the way up. If it's down too low, you get popping sometimes.

---

### Post by ewg on 2009-06-11
Thomas...I'm getting popping but nothing else. Sound just stopped working watching a video and now nothing works.

Thanks,

---

### Post by thomasaaron on 2009-06-11
Can you disconnect your speakers and put in some headphones? Does that work?
Trying to determine if we need to look deeper into the Sable or into your speakers.

Also, make sure all settings are like they were BEFORE the sound went out.

---

### Post by jml on 2009-06-11
ewg,

Since the sound cut out while you were streaming a video, the two things I think about is a partially unplugged audio jack.  A partial connection would allow static and pops to come through but not sound.

A second thought is hardware failure.  I am not familiar with the sound card in the Sable, but is it possible to swap it out with a sound card that is known to be working?  Just my two cents.

Joe

---

### Post by ewg on 2009-06-11
Thanks for replies,
Disconnected speakers and then Plugged headphones into speaker jack and got nothing. Plugged them into front and got nothing. I have left all settings the same.

I don;t have another sound card available.

---

### Post by balloooza on 2009-06-11
Make sure *all* sliders are up, including that one, that might be irrelevant, can you report back that all are up, then try to play a sound, but tell me if all the sliders are up.

---

### Post by ewg on 2009-06-11
Yep, all sliders are up. PCM, line in and CD. Nothing.

---

### Post by balloooza on 2009-06-11
can you install pulse audio device chooser (I am on my mac, I do not know the exact package name, if you search synaptic you should find it, then start pulse volume control  (from the menus)

---

### Post by thomasaaron on 2009-06-11
Can you boot from a Live CD and see if sound works from there out of the box? If it does, it is a configuration problem. If not, hardware.

---

### Post by ewg on 2009-06-11
I'll see if I can track down a live CD. This will be awhile. I'll post when I'm done. 

Thanks,

---

### Post by synapsys on 2009-06-11
Sudden loss of sound for no reason while using device......hardware........

---

### Post by ewg on 2009-06-12
Found a live DVD (8.04) and the sound worked. I used system>preferences>Sound and played the teset for ALSA, OSS and pulse audio and they all worked through my speakers.

Next?

---

### Post by thomasaaron on 2009-06-12
Can you post screenshots of your volume control settings (that you get when you double-click your speaker icon). Capture each tab. Also, post a screenshot of System > Prefs > Sound.

I'll re-image a Sable and compare notes.

---

### Post by ewg on 2009-06-12
Sorry Thomas, I hope this is what you need. Not sure homw to get the image loaded. I also tried to 'attach' them.


/home/ewg/Desktop/Screenshot-Volume Control: HDA NVidia (Alsa mixer).png

/home/ewg/Desktop/Screenshot-Sound Preferences.png

---

### Post by ewg on 2009-06-12
Other 2 tabs you requested. Attached.

---

### Post by thomasaaron on 2009-06-12
OK. On System > Prefs > Sound, set all of those to Autodetect. Set the bottom one to HDA Intel (Alsa Mixer).

On your sound control panel (the one you get when you double-click your speaker icon), set it to HDA Intel (Alsa Mixer) as well.

---

### Post by ewg on 2009-06-12
Did that and rebooted but still no sound.
BTW: I don't have an HDA intel(ALSA) so I chose HDA nVidea(ALSA)

---

### Post by ewg on 2009-06-12
Thomas, found this in another forum.:....
fletchoid
May 1st, 2009, 07:39 AM
Found this solution in another thread. It worked for me (Creative Labs Audigy 2 soundcard) The Analog/Digital Output Jack function was reversed in an update.
To check, click on the speaker icon in top panel, then click on the volume control button. The mixer panel should open. Look for a 'switches' tab. If it's there then open and uncheck the 'Analog/Digital Output Jack'. If not there then click on 'preferences', scroll down and enable the Analog/Digital Output Jack switch, then go back and uncheck. Sound works fine now.
This is a totally stupid and un-necessary bug that could seriously turn people off Ubuntu. I spent hours trying to figure out what the heck went wrong with my upgrade to 9.04. The vast majority of people trying Ubuntu for the first time would have just deleted the whole OS from their computer, and NEVER tried Linux again. Too bad, it is such a fantastic OS once you get beyond some of the stupid little things that can go wrong.
--------------------------------------------------------

I do not have have an analog/digital but I checked 'digital' - recording and for whatever reason I now have sound. Very strange. Why did it all of a sudden stop working? Why did clicking a box related to recording give me playback sound? Seems like a nasty bug. I'll get back to you if problem happens again.

Thanks

---

### Post by thomasaaron on 2009-06-12
That is strange. I've not had any other reports of it. But good job finding the answer.

---

