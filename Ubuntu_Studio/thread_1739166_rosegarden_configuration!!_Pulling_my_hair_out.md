---
title: "rosegarden configuration!! Pulling my hair out"
date: 2011-04-25
forum: Ubuntu Studio
---

### Post by boulezfan317 on 2011-04-25
here's the message I get when I try to run rosegarden: "Audio sequencing and synth plugins unavailable!

Rosegarden could not connect to the JACK audio sever. This probably means that Rosegarden was unable to start the audio server due to a problem with your configuration, your sustem installation, or both. 

If you want to be able to play or record audio files or use plugins, we suggest that you exit ROsegarden aned use the JACK Control Utility to try different settings until you arrive at a configuration that permits JACK to start. You may also need to install a realtime kernel, edit your system security configuration, and so on. Unfortunately this is an extremely complex subject (!!!) 

Once you establish a working JACK configuration, Rosegarden will be able to start the audio server automatically in the future. " 

I also got this message

 "Rosegarden was unable to find a high-resolution timing source for MIDI performance. You may be able to solve this problem by loading the RTC timer kernel module. To do this try running sudo modprobe snd-rtctimer in a terminal window and then restarting Rosegarden. Alternatively, check whether your linux distributor provides a multimedia-optimixed kernel" 

WHEW!! 

OK, so I configured the Jack controls based on another post I read which greatly reduced the number of error messages I had been getting, but what the hell do I do to make rosegarden RUN!!! I have only used linux for about a week, and I have to say I think I'm in love with it, but what the hell! why does it have to be so hard to get certain goddamn software to run!!?? oh btw I also tried sudo modprobe etc but it didn't recognize the commands. is there a misprint or am I just an idiot? 

any suggestions? 

oh yeah, my whole aim is to be able to edit midi files (the tuning of which has been modified by this other amazing program that I also had a hell of a time getting going) so that they have a very complex overtone complement, but absolutely no vibrato or chorus or anything. Something my group can use to practice intonation with. 

Thanks for any help!

---

### Post by FuzzShifter on 2011-04-26
Are you starting QJack control before starting Rosegarden?

---

### Post by boulezfan317 on 2011-04-26
yes I have tried running qjackctl, but I still get error messages telling me that I need to add myself to the audio group (which I have created). So I type "sudo usermod -a -G myusername" 
and press enter and nothing happens except that I get another prompt the next line down. This is exactly what I did last night, and the jack controls worked, and I would have tried your suggestion. But why the hell did it work last night but not today??!?! its so frustrating! what did I do to undue the progress I made last night?

btw here is the message in the qjackctl message window: 
p, li { white-space: pre-wrap; } JACK is running in realtime mode, but you are not allowed to use realtime scheduling.
 Your system has an audio group, but you are not a member of it.
 Please add yourself to the audio group by executing (as root):
   usermod -a -G audio (null)
 After applying these changes, please re-login in order for them to take effect.
 You don't appear to have a sane system configuration. It is very likely that you
 encounter xruns. Please apply all the above mentioned changes and start jack again!

---

### Post by FuzzShifter on 2011-04-26
I like to use gui's, so my methods may be different than others...

Under system/admin/users and groups (from main menu), unlock groups and create a group called audio (and check your user name under it).

If you are currently using the -rt kernel, it may also make things easier to start out by using the generic kernel during setup. The -rt kernel can cause stability problems with certain hardware/drivers.

What info do you get on the x-runs?

---

### Post by boulezfan317 on 2011-04-26
Ha i like guis too, and following your instructions I find that I'm already a member of the audio group. (my user name is checked already in other words) 
Next, what is the -rt kernel?

---

### Post by FuzzShifter on 2011-04-26
If you've installed Ubuntu Studio from disc, you most likely have the -rt kernel (verified by mention of running Jack in realtime mode).

If startup-manager is installed (system/administration/startup-manager), you can check which kernel is default and/or change to another installed kernel.*

Others will have different experiences, but my system runs with good stability with memory lock off (in Jack), while using generic kernel, and realtime unchecked in Jack.

Sure, the reported latency is just over 42ms, but that only seems to effect actual audio, and I monitor the input of audio instead of output while recording (plenty of metering in rosegarden).

*Alternately, a different kernel can be loaded from the GRUB menu @ startup.

Jack can be difficult to get going the way you'd like, and that is doubly so when too many variables are changed at once.

---

### Post by sgx on 2011-04-26
Rosegarden needs a kernel with 1000hz midi timer

put this in google:

rosegarden kernel timer 1000 midi

Cheers

---

### Post by rosencrantz on 2011-04-26
Or use rosegarden's recommendations: [http://www.rosegardenmusic.com/wiki/low-latency_kernels](http://www.rosegardenmusic.com/wiki/low-latency_kernels)

---

### Post by FuzzShifter on 2011-04-27
Thanks for the backup guys.

I was just trying to not help him break it any more.:)

---

### Post by boulezfan317 on 2011-04-27
thanks guys, I have to go to work right now, but I will try your suggestions tonight! Thanks for your patience with all my ignorance!!

---

### Post by Pablo_F on 2011-04-27
Hi,

Once you have jack up and running, don't forget this: 

Rosegarden _does not make sounds by itself_. For MIDI tracks you need either an external synth or a synth plugin.

The external synth can be hardware or software, being the default name "general MIDI device". You can rename it and, most importantly, you need to assign it to the actual external synth via Studio -> Manage MIDI devices. A classic example of external soft synth is qsynth , a soundfont player (well, qsynth is a front-end for fluidsynth). You need to load at least one soundfont file in qsynth. You can find a decent one in /usr/share/sounds/sf2 once you install the package called "fluid-soundfont-gm". 

The other option for making noise from MIDI tracks is a dssi plugin or "synth plugin". If you want to play soundfonts you can choose fludsynth-dssi. There is also hexter, a Yamaha DX7 emulator. I suggest these ones because they are good and easy available (via software center, synaptic or "apt-get install"...).

Cheers, Pablo

---

