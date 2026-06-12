---
title: "Recording from external player"
date: 2007-12-23
forum: System76 Support
---

### Post by ajlewis2 on 2007-12-23
I did some recording from cassettes to my Darter a while back.  I used a cable from the headphone jack in the player to the microphone jack in the laptop.  It came out pretty good.  That was before I upgraded to Gutsy.

The recording comes out with lots of static.  I know this was not the case before.  The sound with the microphone seems fine in things like skype.  I'm wondering if this has to do with the new audacity rather than something in my sound system or in the mixer settings. I do get nice clear sound coming through the laptop when I turn the microphone output on. 

I am using Ubuntu with kubuntu desktop.  I also notice the following:

The switch on the side and the sound function keys only change up to 11% Volume according to the little meter on the screen.

In audacity when I record using the headset, it is very loud.  I think that is because the input setting is at max.  It is still much louder than it used to be with the input set at medium.  I can't seem to keep the setting at normal, but I guess that is an issue with audacity.  I mention it in case it might have to do with the static I'm getting when recording.

---

### Post by ajlewis2 on 2007-12-23
I cleared up the main problem by turning off the mic boost.  I probably did not have that up before when I was doing this.

I still haven't got the sound adjustment working using the function keys or the little thumb thing on the side of the machine.  This is in kde.  

Anita

---

### Post by thomasaaron on 2007-12-24
Hi, Anita.

I'm not sure how to do that in KDE. In gnome, you go to System > Prefs > Sound.
Then highlight the channel you want to the thumbwheel and keys to control at the very bottom of the GUI.

That's probably not helpful, though.

---

### Post by ajlewis2 on 2007-12-24
Yes, that is the same as selecting the Master Channel in the kde mixer.  I ran gnome-sound-properties and see that it is set for PCM.  In kde mixer the Master Channel is also PCM.  

I'll investigate more.  Your information was helpful, because it showed me where to look on the Gnome side.  

Thanks,
Anita

---

### Post by thomasaaron on 2007-12-24
Good. I don't know much about KDE.

That said, I do know we've run into key-mapping issues with it in the past. Hope that's not the case here.

---

### Post by ajlewis2 on 2007-12-24
Ok, I logged out and into Gnome.  I set the Master Channel to Front.  Then I played something on xmms and used the side thumb and the Fn keys to adjust the sound.  The indicator goes up from 0 to 100% as expected.

Back in KDE I have the Master also set for Front, but the volume indicator only goes between 0 and 11%. The mixer volume slider works to adjust the volume, but not the Fn or thumb.  So maybe this is a keymap issue.  

Would you like any xev output?  I guess you already know what that would be.  This can certainly wait; so just let me know if/when you want any sort of testing at my end.

Thanks,
Anita

---

### Post by asmiller-ke6seh on 2007-12-24
Be aware that static in an analog signal (such as comes from an audio cassette) can be caused by a bad cable, a bad plug, a bad solder connection in the plug, or even static from electrical devises being picked up in the cassette, cable, or plugs. To eliminate these as potential sources of static, it is a good idea to make sure that you have a new, well made, double shielded cable. If you are using any adapters, that could be a source of static, too - so get a cable that doesn't need adaption.

Next, make sure that you use the proper levels - it is better to use a higher volume on the output from the cassette than a higher volume on the recording device (your Darter) ... otherwise you are just amplifying the static, whatever it's source. Just be careful that you don't use too high a volume level from the cassette; start with the cassette volume set at the mid way volume point, and then bring up the record volume on your Darter until Audacity indicates the proper level (just under 0 dB at the peaks is probably best - you can always amplify in Audacity after recording is complete).

I hope this is helpful to you. (BTW, I hold an FCC Technician class license, and I used to be a sound engineer for a 100,000 watt FM radio station in Rochester, NY).

---

### Post by ajlewis2 on 2007-12-25
More info on the quality of recorded sound.

I have a fresh install of Ubuntu Gutsy as well as my usual install which has been upgraded to Gutsy in which I use KDE.

I went to the fresh install and installed audacity.  Quality of sound recorded through the mic. jack is excellent. 

I went back to the upgraded version and tried to record and it was not good quality even when I was sure to turn the volume down and to make sure the front mic is off.  I also tried putting the audacity config file from .audacity-data in the fresh install into the upgraded install.  That did not change the quality.

I look in /opt and find where the system76 drivers src is.  I see  sys76-alsa-1.0.14rc3.tar.gz which is from 4/19/07 and would then be in the old modules directory I assume.  That set of drivers is not in my fresh Ubuntu install in /opt/system76.  I do see in the /lib/modules directory for the kernel in use that the soundcore.ko file is 12/18 in the upgraded and is 10/14 in the fresh install.  So that set of modules must not have been upgraded yet.  I recall that I did have a module upgrade for the 2.6.22-14-generic kernel a little while ago.  

I'm just trying to rule out a sound module problem.  I guess I'll have to upgrade on the fresh install before I will be able to know for sure that it is not the modules.

The other thing is that on the fresh install I do not have my current /home partition mounted.  That also mounts my current /home and audacity doesn't work now with my current /home.  I can probably fix it to not mount the /home partition and make myself a new one on the root there.  Then I can try audacity on that install.  

These frequent upgrades are plus/minus--new proggies, new problems.  But mine are small compared to system76 tech support's, I imagine.

---

### Post by ajlewis2 on 2008-01-04
I found a small cylindrical item with the words "Signal Adapter" on it.  It has little microphone shaped images on either end of the cylinder.  There is a plug that fits into my microphone jack and a receptacle that the same sized plug can fit into.  

This item was in a little plastic bag and I guess it came with the Darter. I can't think of what else I got it with.  I just now tried that with recording from the external player and it sounds pretty good, I think.  

I'm curious if this item came with the machine.  

I'm also still wondering why the volume control on the side and the function keys for the sound don't work when I'm in KDE, but they work when I'm in Gnome.  But that is not a big deal since I can use the mixer to change sound level.  I saw another post where it said that KDE is not supported by System76; so I will stop pestering you about it. :-)

Anita

---

### Post by thomasaaron on 2008-01-07
Well, I'd like to have one of those, but one did NOT come with my Darter.

----

We've had a lot of reports of keymapping problems with KDE. That's probably why the volume knob doesn't work.

---

