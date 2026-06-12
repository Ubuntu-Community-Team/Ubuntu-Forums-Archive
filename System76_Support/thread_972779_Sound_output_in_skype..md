---
title: "Sound output in skype."
date: 2008-11-06
forum: System76 Support
---

### Post by Guille Damke on 2008-11-06
Hello,

I have installed skype in 8.04 64 bit in a Pangolin Performance panp4n following this thread [http://ubuntuforums.org/showthread.php?t=432295](http://ubuntuforums.org/showthread.php?t=432295) using this > sudo apt-get install ia32-libs lib32asound2 libasound2-plugins; wget -O skype-install.deb [http://www.skype.com/go/getskype-linux-ubuntu-amd64;](http://www.skype.com/go/getskype-linux-ubuntu-amd64;) sudo dpkg -i skype-install.deb  Skype runs but I have no output audio when pressing "Make a sound test". Also it gives the message "Problem with Audio Playback" if I try the test call. On the other hand, I can hear sounds from other sources and I can record audio in the Sound Recorder ( I already checked the "Record" option in sound options). Anyway, I think my problem is for listening than recording. I have the device "HDA Intel (ALSA Mixer) active (the default), I tried the other ones, with no success.

By the way, the camera works.

Please, as usual, all suggestions are welcome,
Guille.

---

### Post by thomasaaron on 2008-11-06
I don't have a lot of time at the moment to go over that tutorial, but here is our suggested method of installing restricted codecs (and Skype).

[http://knowledge76.com/index.php/Installing_Restricted_Formats](http://knowledge76.com/index.php/Installing_Restricted_Formats)

Go to System > Prefs > Sound, and make sure everything is set to Pulse Audio. Does that fix it?

---

### Post by Guille Damke on 2008-11-07
Hello thomasaaron,

I tried what you suggested, after playing with the skype options, I got sound in the left channel yesterdat, but today I still have the same problem. I installed some of the pulse audio packages (as the Pulse Audio device chooser) but Skype was not working either. Finally, I run the system76 restore option and after rebooting I have lost the sound in all my system!!!

If anyone else knows how to restore the sound in the system, please help me.

Regards,
Guille.

---

### Post by raedbenz on 2008-11-07
i would say to right click on the speaker icon on the top tool bar and open volume control, and try to change the hardware device.

---

### Post by Guille Damke on 2008-11-07
Hello raedbenz, 

I already tried it, iI was thinking that I was making a mistake there, the options there seem to be right and it still does not work, I don't even have sound when ubuntu starts. Thank you anyway.

Anyone has other idea? 

Guille

---

### Post by Guille Damke on 2008-11-07
Update,

Although sound Skype is still not working (in Ubuntu 8.04), I have reinstalled ALSA packages and my system sound is working again! If someone has this problem, I have followed this guide > [http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449)

Now, the problem is that I still have NO SOUND in Skype! (last night it worked, but with the same options now it is not working, and no other option in skype for sound works either).

Does anyone has an idea to do sound in Skype to work??

Guille.

---

### Post by Guille Damke on 2008-11-08
Update 2:

I have figured out that reinstalling ALSA does not list all the switches in the Volume Control (obviously I have checked ALL the boxes-options listed there). When I do a recovery using the system76 driver, I can see all the original options in the Volume Control again (which eventually allow Skype to work and to capture sound), but after the recovery I have no sound. I feel like I am running in a loop...

How can I restore the full sound options? My sound card is being detected, this is its model:
```
$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC662 Analog [ALC662 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: ALC662 Digital [ALC662 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 6: Si3054 Modem [Si3054 Modem]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

```
$ lspci -v
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
	Subsystem: CLEVO/KAPOK Computer Unknown device 0806
	Flags: bus master, fast devsel, latency 0, IRQ 22
	Memory at f4600000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>

```

Guille

---

### Post by sirebral on 2008-11-08
Not sure if you are using PulseAudio.  I still have that.

Try these settings:

---

### Post by Guille Damke on 2008-11-08
Hi sirebral:

I wish I had these "Pulse Audio" option in skype, I just don't have it :(


I have pulse set in System-> Preferences -> Sound (I have alsa in the fifth box because I don't see a similar option like in the previous four boxes).

Which options do you have in the fifth box of System->Preferences->Sound?
Thank you.
Guille

---

### Post by Guille Damke on 2008-11-10
Hello,

Update3:

I have more news. I have recovered the settings I had after loosing all the audio, I ran a script that I found in my system which installed ALSA driver 1.0.17 instead of 1.0.16 (which probably was installed when I updated ALSA? or is 1.0.16 the default one in the Pangolin?) After that, I ran the system76 recovery driver and I have all the original switches back again and working.

The problem is still skype, it can work if NOTHING ELSE is using the sound system (i.e. Firefox), which is annoying... I have no "pulse audio" option inside skype (you can check a screenshot in my previous post), so the only configuration that works is :
Sound in & sound out: HDA Intel (hw:Intel,0)
Ringing: HDA Intel (plughw:Intel,0)

Does anyone know how I can make skype to work while other programs are using audio too? 

I attached the options of my volume control. I am using ALSA as my device in volume control since all the "pulse audio" options either for Playback and Capture only have a "master" option, and alsa includes many options.

Guille.

---

### Post by furiousmanatee on 2008-12-23
i have this problem too. - "problem with audio playback" in skype and dont seem to have pulse option in skype --options --sound 

im running 
ubuntu 8.04 updated 64 bit system
nvidia sound card and restricted drivers

sound on everything else seems jubley. skype used to work just fine bar some initial microphone teething problems, i dont even use it too much but lost my phone last night and was very frustrated when trying to use skype to see if anyone had found it. any feedback would be greatly appreciated thanks

---

### Post by thomasaaron on 2008-12-23
I don't think you're going to have a Pluse option in Hardy. That's for Intrepid.

I believe you should be set to ALSA in Hardy. 

Please provide more detail about how you have your sound device set up in Skype.

Also, I'm traveling until next Monday and don't have a computer with Hardy installed on it. So, if there are any 76-ers out there that can describe their Skype setup, I'd much appreciate it.

---

### Post by furiousmanatee on 2008-12-23
thanks for the speedy reply 
just found another thread which seems to have sorted it by killing pulse. 

[http://ubuntuforums.org/showthread.php?t=974556&highlight=skype+audio+output](http://ubuntuforums.org/showthread.php?t=974556&highlight=skype+audio+output)

would you know of some way to stop pulse booting to start with to avoid having to type commands every time? or more info on pulseaudio or where to find it?

im on an MSI L735 laptop, all sound settings set to alsa which seems to work well 

enjoy your travels

---

### Post by thomasaaron on 2008-12-23
You could probably create some start-up scripts to run those commands automatically when you log in. You'd probably want to put it in /etc/acpi/start.d (or something like that).

---

### Post by theTOman on 2008-12-23
Hi

I use 8.04, on a Pangolin and it's ALSA all the way and Skipe works perfectly well.

BUT, you are right! -If another software is using sound, I get the "problem with audio-playback" message.

So, switch everything back to ALSA, and, before opening Skype, make sure no oher apps can grab the attention of the sound card.

---

### Post by theTOman on 2008-12-23
Hi

I use 8.04, on a Pangolin and it's ALSA all the way and Skype works perfectly well.

BUT, you are right! -If another software is using sound, I get the "problem with audio-playback" message.

So, switch everything back to ALSA, and, before opening Skype, make sure no other apps can grab the attention of the sound card.

---

### Post by Guille Damke on 2008-12-26
Hey,

I remember that when running 8.04 I found a thread with a tip where you added a file in your home (I think it was named .soundrc) with some commands on it. After rebooting, it gave you the "pulse" audio option in Skype. That worked for me, since the sound input is still the "HDA Intel (hw:Intel,0)", but only output uses pulse, and it allows you to use skipe as other applications are using sound also.
If I find the thread I will post it here, also I'll try to remember how I put it to run.
Guille.

---

