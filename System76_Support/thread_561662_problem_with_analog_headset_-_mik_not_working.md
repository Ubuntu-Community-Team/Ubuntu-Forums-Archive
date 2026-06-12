---
title: "problem with analog headset - mik not working"
date: 2007-09-27
forum: System76 Support
---

### Post by Canucktom on 2007-09-27
Hi guys,

I have a Gazelle Value with Feisty running and experience a weird problem with an analog headset.

When I plug it in, the earphones work nicely but the micro won't activate instead the laptop mic still works. I am quite sure it is not a hardware problem for a different headset worked without any hassles. And my headset funktions with another computer.

The microphone is not muted and I checked several threads for ideas but could not find anything that applied for my problem.

I want to use the headset with Gizmo as my only phonenumber, therefore I would be thankful for any tip.

Thanks,
Tom

---

### Post by thomasaaron on 2007-09-28
OK, I got it to work.

*GazV4
*7.04 Feisty Fawn
*Ran System 76 Driver (2.0.9)

NOTE: I do not have an analog headset. I used an external microphone that plugs into the mic jack and a set of analog headphones. There should be no difference.

If your analog headset does not work with the following configurations, make sure a) it has a standard jack, and b) there is no switch or controller setting on the headset that may be turning something off.


Sound Device Setup
1. Double-click the speaker icon in the upper left.
2.File > Change Device > HDA Intel (Alsa mixer)
3. Edit > Preferences (select all checkboxes)
4. Under Recording tab, turn "Capture" all the way up and unmute it
5. Under Playback tab:
    *Unmute headphones
    *Unmute PCM
    * Mute Front
    * Unmute Microphone
    * Mute PC Speaker
    * Everything else is muted
6. Under Switches Tab
    * Check Mono Capture
    * Everything else is unchecked
7. Under Options Tab
    * Channel Mode = 2ch

Sound Control Selections
8. Go to System > Preferences > Sound
9. * Sound Events = Autodetect
    * Music and Movies = Autodetect
    * Audio Conferencing playback = Autodetect
    * Audio Conferencing Sound Capture = ALSA - Advanced Linux...    
10. Default Mixer Tracks Device = HDA Intel (Alsa Mixer)
11. In the list box below, highlight "Headphone"

Sound Recorder
It is slightly hosed, but it is still usable if you know what to do.
12. Applications > Sound & Video > Sound Recorder
13.Click "Record" and say: "Ubuntu rules; Another very popular OS druels."
14. File > Save As. Save it wherever. (NOTE: The save button does not work the first time you record. You will have to use "Save As." The save button will work if you click it AFTER your first save.)
15. Now that you've saved, you can click your play button and enjoy listening yourself talk smack about other OS's in your usb headphones.

Hope this helps.

---

### Post by Canucktom on 2007-09-28
HI!

ok, I followed every single step.
Still the laptop microphone is used for recording and the headset micro does not work at all. I checked this by moving my finger over the micros, and it got very clear, where the sound came from.

So why does my laptop not recognize when the external micro is plugged in?

Tom

---

### Post by thomasaaron on 2007-09-28
I put my finger over the internal mic, turned away from the computer and spoke very softly into the external mic. Worked like a charm.

Try a different microphone.

---

### Post by Canucktom on 2007-09-28
I tried an older analog headset - same result.

---

### Post by thomasaaron on 2007-09-28
OK. 

Please post the output of...

cat /proc/asound/version

...and we'll revisit it on Monday. I'll double-check all my settings, etc...

Best,
Tom

---

### Post by Canucktom on 2007-09-28
ok, here you go:

cat /proc/asound/version

"Advanced Linux Sound Architecture Driver Version 1.0.14rc3.
Compiled on Sep 24 2007 for kernel 2.6.20-16-generic (SMP)."

does that help?

Have a good weekend,
Tom

---

### Post by Canucktom on 2007-10-05
Hi Tom,

did you have any new findings about my problem?

Tom

---

### Post by Canucktom on 2007-10-15
Hi!

at least somehow solved. 
Though not happy about it, I installed Windows xp on my old notebook, plugged in the headset and it worked just fine without any hassels.

bye,
Tom

---

### Post by thomasaaron on 2007-10-16
Well, that at least proves that it is a configuration problem and not a hardware problem.

I re-tested on our shop Gazelle, and it still works fine.
You have something out of whack in your configuration. I know it can be fixed.
If you want to pursue it further with Ubuntu, you should probably send me some screenshots of your settings.

---

### Post by ajlewis2 on 2007-12-16
I have a problem with my headset as well.  I can fix it, but I wonder why it happens.  After booting and plugging in the headset, I do not record - either in Skype or with Audacity.

I am using Ubuntu with kubuntu-desktop; so the mixer is a tad different.  Here is what makes my microphone work.  Under Switches, turn it from Mic to Front Mic.  Close.  Open mixer again and change it back to Mic.  Then it records.

Now why is this?  Is there a way to set alsamixer this way and then use alsactl store to save the setting so that when I reboot, I have that already set?  I guess not, because it is already set to Mic when I boot and I have to set to Front Mic and then back again to get the headset mic.

---

### Post by riseringseeker on 2007-12-17
> **ajlewis2 said:**
> I have a problem with my headset as well.  I can fix it, but I wonder why it happens.  After booting and plugging in the headset, I do not record - either in Skype or with Audacity.

I am using Ubuntu with kubuntu-desktop; so the mixer is a tad different.  Here is what makes my microphone work.  Under Switches, turn it from Mic to Front Mic.  Close.  Open mixer again and change it back to Mic.  Then it records.

Now why is this?  Is there a way to set alsamixer this way and then use alsactl store to save the setting so that when I reboot, I have that already set?  I guess not, because it is already set to Mic when I boot and I have to set to Front Mic and then back again to get the headset mic.

I used to have to do pretty much the same thing with my Darter (change mic, and change it back) to be able to use skype.  Imagine my surprise and delight when I did a clean install of gutsy, and having gotten skype from skype, as opposed to medibuntu the mic not only worked, but recognized automagically whether or not I was using internal/external!

Then in an update I got an "updated" skype from medibuntu.  I was right back where I started, having to change mic settings again.  Using synaptic, I "reverted" to the skype skype, and problem solved!  I am now using the beta 2.0.0.27 version, and not only does it still work **much** better than the medibuntu version, it now supports video as well!

Maybe you should try uninstalling your skype, and then getting it from skype.com.  You don't really have anything to lose, other than a few minutes, and if it works, it'll save much more time that you are now doing the mic swap thing with.

For the current stable version of skype, click [here]("http://www.skype.com/download/skype/linux/choose/") (The feisty fawn version works fine).  For the beta version with video, click [here]("http://www.skype.com/download/skype/linux/beta/").

---

### Post by ajlewis2 on 2007-12-17
> **riseringseeker said:**
> 

Maybe you should try uninstalling your skype, and then getting it from skype.com.  You don't really have anything to lose, other than a few minutes, and if it works, it'll save much more time that you are now doing the mic swap thing with.


That is an excellent idea.  I am not sure which version of Skype I have, but I'll check tonight.

This does not solve the problem of rebooting and trying to record with Audacity, however.  The problem with the microphone/headset is the same with that program. It will be wonderful if a Skype upgrade/change fixes that.  I'll report back.

Thanks!

Anita

---

### Post by riseringseeker on 2007-12-17
> **ajlewis2 said:**
> That is an excellent idea.  I am not sure which version of Skype I have, but I'll check tonight.

This does not solve the problem of rebooting and trying to record with Audacity, however.  The problem with the microphone/headset is the same with that program. It will be wonderful if a Skype upgrade/change fixes that.  I'll report back.

Thanks!

Anita

Like I said, you have little to loose.  Skype by default is set to automatically control your mixer settings, so if skype is fired up, it may indeed mess with other programs - who knows?  I would like to hear if this fixes things for you though.

---

### Post by ajlewis2 on 2007-12-17
> **ajlewis2 said:**
> I'll report back.


I removed skype 1,3,x which I think I had got from skype.com some while back.  I installed skype 1.4.0 which it says if for Feisty.  It does not correct the sound annoyance.  I still need to turn on Front Mic and then turn it back to Mic for my headset to work properly to record.  

I also tried removing the ~/.Skype directory and letting it build a new one, but that did not correct the problem either.  

Anita

---

