---
title: "playback and input problems in recording programs"
date: 2009-10-27
forum: Ubuntu Studio
---

### Post by lastcigaretteme on 2009-10-27
Hello All,                          
 I am a newbie in the Linux world but have been using Ardour, JACK, and Hydrogen on my Mac for several years. I love the program and was excited to try it (and many others) in the Linux world. But I'm having audio input and playback problems in recording programs, including Ardour, Hydrogen, Audacity, and even the basic Sound Recorder. Audio playback is working fine through other programs, Firefox, Amarok and other mp3 players, Movie Player, and Open Movie Editor.
 I'm running Ubuntu Studio on Ubuntu 8.04, Hardy Heron. The computer is an Acer Aspire 5100 laptop. I'm using the computer's internal sound card for now. I've read a number of posts here and elsewhere about setting up Ubuntu for sound recording – I've downloaded the latest realtime kernel, I've set all sound preference settings to ALSA, and followed a few other fixes I've found that have made JACK run much more smoothly since I began this about a week ago. Still not able to record and playback properly though.

 Here are specifics on the audio input problem - It doesn't seem to matter which input I choose, my mic going into the computer's mic input gives only a very low, clipped sound when tapping the mic or eating it as I “check”. This is a sensitive mic running through a preamp that works great on my Mac. Plugging into the line input reacts the same way. In Ardour, I hear the same messed up input sound, but I am not getting an input signal on the track meter, regardless of whether 'capture1' or 'capture2' is selected for system input.
 Playback problem specifics - This would all lead me to believe that perhaps I have a hardware problem (ie., my audio inputs are shot), except for the fact that sound coming from inside the computer is reacting the same way - when I play a previously recorded Ardour session or a new session with imported tracks, playback gives me only strange, electronic noises that seem to be running through a very bad echo. Drums in Hydrogen sound the same, but when Hydrogen runs without Jack it sounds normal. This leads me to believe JACK is the problem. But I have followed all advise I can find on JACK setup.

 As much as I would love to record audio into this computer, it's the internal playback problem with Ardour and Jack that is most frustrating, as I had hoped to use this Ubuntu computer to do mastering between Ardour and Jamin. I can continue recording audio in Ardour onto my macbook, but the most important thing is to be able to master using Jamin.
 Any help would be much appreciated. I'm excited to get moving in Ubuntu, I just need to get over this hurdle.

---

### Post by lastcigaretteme on 2009-10-27
I just realized that my first post had very little in the way of specifics to help ferret out the problem. So here's a specific list of what I've tried so far and some error messages that I'm still getting. All of the above description of audio shenanigans still applies. Thanks again for any assistance. I'm just a babe in the woods here. Patience appreciated.

---

### Post by lastcigaretteme on 2009-10-27
So, apparently I really am a babe in the woods .... for some reason the following was dropped from my last message... Here are the specifics that I was talking about....

This is what I have done (to the best of memory and not necessarily in this order): 
* ran “sudo apt-get install linux-rt” in Terminal and was told that I already had the most up-to-date kernel (I also did the same for realtime linux headers) 
* set “Enable memlock” to 50% in the Ubuntu Studio Controls    
* enabled realtime in JACK preferences   
* created the user group “audio” and connected it in Terminal, /etc/security/limits.conf – I used these commands ( sudo su -c 'echo @audio - rtprio 99 >> /etc/security/limits.conf' ) ( sudo su -c 'echo @audio - nice -10 >> /etc/security/limits.conf' )  ( sudo su -c 'echo @audio - memlock unlimited >> /etc/security/limits.conf' )  I got these  from [https://help.ubuntu.com/community/UbuntuStudioPreparation](https://help.ubuntu.com/community/UbuntuStudioPreparation)   
* in preferences/sound I've set ALSA for all playback and input.  
* Checked that ALSA is the default driver, did this in terminal  
* The only available sound card on my system is “SB” according to the list in Terminal. I've checked that “SB” is the default card.

I'm no longer getting error messages with JACK or Ardour. Only occasional freezes and false starts with JACK. Much better than it was before. But I have been getting the below messages in other programs.

When hitting record in Audacity this error message appears:
“Error while opening sound device. Please check the input device settings and the project sample rate.”
I've tried both sample rates of both 48,000 and 44,000. Makes no different. I'm also not sure what I can do with the input device settings that I haven't already tried. Am I missing something?

When trying to open Sound Recorder, I get the error message:
“Your audio capture settinngs are invalid. Please correct them in the Multimedia settings.”
I cannot seem to find the Multimedia settings. Not sure where to look. Not even really interested in using Sound Recorder. Ardour and Jamin are my goal. But still this seems to point to a fundamental flaw in my setup.

---

### Post by AutoStatic on 2009-10-27
Hello lastcigaretteme, could you provide more information on the onboard soundcard? From reading your posts you're a bit familiar with the terminal so if possible could you post the output of the following command: ```
aplay -l && lspci | grep -i audio && cat /proc/asound/card*/codec#* | grep -i codec
```

And what are your current settings in Qjackctl and Audacity (Edit - Preferences - Audio I/O and Quality)?

---

### Post by lastcigaretteme on 2009-10-28
Hi AutoStatic,
Thanks for your reply.
An update before responding to your questions:
I'm not sure why, but something has changed. I was able to record with Sound Recorder and with Ardour earlier today. Sound recording quality was bad, but at least I had audio input. Playback improved slightly in Ardour as well. This appears to be because of switching over to 48.000 samplerate in JACK, but unfortunately it did not stand the test of time - see below.
I also got Audacity to let me record by switching the recording device in Audacity preferences to JACK. I don't remember this being an option when I looked before but... there it was. So I can press record in Audacity and it reacts as if it's recording, but all I get is the strange computer feedback that I described earlier, and this with no sound at all being inputed into the system. This was without a mic plugged in. The computer is generating the noise.
Tried the same thing again tonight (with no changes to any settings) to see if the improvements still held. But Ardour would not allow me to record from input. In Ardour, I am now only getting a similar digital feedback to what occured in Audacity and playback is as bizarre as ever...

Here's what comes up in Terminal when I enter your suggested command:
aplay -l && lspci | grep -i audio && cat /proc/asound/card*/codec#* | grep -i codec
**** List of PLAYBACK Hardware Devices ****
card 0: SB [HDA ATI SB], device 0: ALC883 Analog [ALC883 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
00:14.2 Audio device: ATI Technologies Inc IXP SB4x0 High Definition Audio Controller (rev 01)
Codec: Realtek ALC883
Codec: Conexant ID 2bfa

I'm also attaching images of the JACK and Audacity preferences settings you asked about. Although the Audacity samplerate still reads 44,000 I have had to change it in the main window (after getting the "samplerate/device settings" message mentioned earlier) when I've tried to record.

I'm not sure if this is of any use, but just in case, here is what showed up in the message window in Jack when I last tried to run it: 
**** alsa_pcm: xrun of at least 0.020 msecs
**** alsa_pcm: xrun of at least 0.024 msecs
20:32:18.486 XRUN callback (37 skipped).
**** alsa_pcm: xrun of at least 0.025 msecs
**** alsa_pcm: xrun of at least 0.016 msecs
**** alsa_pcm: xrun of at least 0.025 msecs
**** alsa_pcm: xrun of at least 0.026 msecs
**** alsa_pcm: xrun of at least 0.025 msecs
**** alsa_pcm: xrun of at least 0.018 msecs
**** alsa_pcm: xrun of at least 0.024 msecs
**** alsa_pcm: xrun of at least 0.017 msecs
**** alsa_pcm: xrun of at least 0.022 msecs
**** alsa_pcm: xrun of at least 0.022 msecs
**** alsa_pcm: xrun of at least 0.018 msecs
**** alsa_pcm: xrun of at least 0.019 msecs
**** alsa_pcm: xrun of at least 0.022 msecs
**** alsa_pcm: xrun of at least 0.017 msecs
**** alsa_pcm: xrun of at least 0.017 msecs
**** alsa_pcm: xrun of at least 0.016 msecs
**** alsa_pcm: xrun of at least 0.021 msecs
**** alsa_pcm: xrun of at least 0.017 msecs
**** alsa_pcm: xrun of at least 0.017 msecs
20:32:19.471 JACK connection graph change.
**** alsa_pcm: xrun of at least 0.029 msecs
20:32:19.493 JACK connection change.
**** alsa_pcm: xrun of at least 0.026 msecs
**** alsa_pcm: xrun of at least 0.026 msecs
**** alsa_pcm: xrun of at least 0.026 msecs
**** alsa_pcm: xrun of at least 0.029 msecs
**** alsa_pcm: xrun of at least 0.027 msecs
**** alsa_pcm: xrun of at least 0.027 msecs
**** alsa_pcm: xrun of at least 0.025 msecs
**** alsa_pcm: xrun of at least 0.022 msecs
**** alsa_pcm: xrun of at least 0.025 msecs
**** alsa_pcm: xrun of at least 0.018 msecs
**** alsa_pcm: xrun of at least 0.018 msecs
**** alsa_pcm: xrun of at least 0.025 msecs
**** alsa_pcm: xrun of at least 0.023 msecs
**** alsa_pcm: xrun of at least 0.020 msecs
**** alsa_pcm: xrun of at least 0.024 msecs
**** alsa_pcm: xrun of at least 0.021 msecs
**** alsa_pcm: xrun of at least 0.022 msecs
**** alsa_pcm: xrun of at least 0.019 msecs
**** alsa_pcm: xrun of at least 0.025 msecs
20:32:20.499 XRUN callback (38 skipped).
**** alsa_pcm: xrun of at least 0.018 msecs
**** alsa_pcm: xrun of at least 0.017 msecs
**** alsa_pcm: xrun of at least 0.019 msecs........

         it goes on like this for much longer.. I can give the whole thing if it might help..... but it ends like this....

20:33:20.574 Client deactivated.
20:33:20.575 JACK is stopping...
jack main caught signal 15
**** alsa_pcm: xrun of at least 0.024 msecs
no message buffer overruns
20:33:20.624 JACK was stopped successfully.
20:33:20.625 Post-shutdown script...
20:33:20.625 killall jackd
jackd: no process killed
20:33:21.034 Post-shutdown script terminated with exit status=256.

This is from a period of several minutes - opening and starting JACK, started Ardour and opened the session that I started earlier (which had allowed me to record very low quality audio) and tried to record again. This time the only input signal I got was a persistant computer pulse sound, similar to the one that I got with Audacity.
Thanks again AutoStatic for your reply and for any future suggestions. Apologies if I've included too much info here. I'm not sure what is relevant and what isn't. Still learning, obviously.
lastcigaretteme

---

### Post by kayosiii on 2009-10-28
> **lastcigaretteme said:**
> 

When hitting record in Audacity this error message appears:
“Error while opening sound device. Please check the input device settings and the project sample rate.”
I've tried both sample rates of both 48,000 and 44,000. Makes no different. I'm also not sure what I can do with the input device settings that I haven't already tried. Am I missing something?

When trying to open Sound Recorder, I get the error message:
“Your audio capture settinngs are invalid. Please correct them in the Multimedia settings.”
I cannot seem to find the Multimedia settings. Not sure where to look. Not even really interested in using Sound Recorder. Ardour and Jamin are my goal. But still this seems to point to a fundamental flaw in my setup.

With Audacity check the little box down in the bottom left hand corner of the screen. Make sure this number matches the rate that was set in jackd.

As for sound recorder - don't bother. If you really need a simple recorder that works with jack then download and install time-machine.
(and patchage).

---

### Post by AutoStatic on 2009-10-28
> **lastcigaretteme said:**
> Apologies if I've included too much info here.Apologies for including too much info? If every forumite would post this much information then the majority of threads would be solved in no time! So I thank you wholeheartedly!
I see you got JACK running. Configuration looks good. When JACK is running and you start up Audacity it will give you an extra playback and recording device. When using JACK with a samplerate of 48000 as a playback/recording device in Audacity you have to follow kayosiii's advise, but it's also a good idea to set the default sample rate at 48000 in the Quality section of the Preferences of Audacity.
I'd like to point out though that using JACK with Audacity is not the best combination (for me at least). I get a lot of xruns out of nowhere every now and then when using the onboard soundcard of my netbook, it could also be the onboard card or the snd-hda-intel kernel module. Not sure yet. Just to let you know :)

---

