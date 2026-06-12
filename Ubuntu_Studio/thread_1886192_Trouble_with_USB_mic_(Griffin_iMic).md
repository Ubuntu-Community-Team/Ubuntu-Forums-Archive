---
title: "Trouble with USB mic (Griffin iMic)"
date: 2011-11-24
forum: Ubuntu Studio
---

### Post by Quinflax on 2011-11-24
Hello,

I am very new to Ubuntustudio and I am having some trouble with my Griffin iMic into which I currently have a guitar plugged into (the switch is set to LINE). This is in Ubuntustudio 11.10.

This was all working fine last week - using qjackctl and Guitarix my guitar recorded fine in Rosegarden. Now though, I can't get anything through the iMic.

I have logged into windows to check the iMic works and had no problem getting sound into Audacity (except the terrible latency). Similarly I get sound into Audacity on Ubuntustudio but it is horribly crackly, has constant white noise and makes some terrible noises.

cat /proc/asound/cards
> 0 [NVidia         ]: HDA-Intel - HDA NVidia
                      HDA NVidia at 0xf7dfc000 irq 17
 1 [Audigy         ]: Audigy - SB Audigy 1 [SB0090]
                      SB Audigy 1 [SB0090] (rev.3, serial:0x511102) at 0xe880, irq 16
 2 [system         ]: USB-Audio - iMic USB audio system
                      Griffin Technology, Inc iMic USB audio system at usb-0000:00:1a.0-1.2, full speedIn qjackctl's settings:

[LIST]
[*]I have set my output device to hw:1 and I get sounds (as expected)
[*]I set input device to hw:2 and this no longer picks up the guitar
[/LIST]
In my faffing to get things working I fiddled around in the PulseAudio Volume Control and noticed something interesting - In the Configuration section, if I change the iMic Profile from the current Input type to a new one and quickly go to the Input section then I can see the meter (under the iMic section) responding to my plucking. However, this only lasts a few seconds before it stops responding. This happens whenever I change the type of input.

Has anybody got any idea what is going on here? Any help would be much appreciated.

---

### Post by Quinflax on 2011-11-25
Update: I rolled back the PulseAudio modules (not sure that's the right term) in synaptic from 3.1 to 3.0 as i had a hunch this was the major difference between this week and last week (when it was working). This seemed to sort out the problem - I started qjackctl up and guitarix was receiving input from the guitar...but there was no sound.

 I opened up Hydrogen, and no sound. I checked Alsamixer and all was as it should be. Curiously, although iMic was present in PulseAudioMixer's Configuration tab it had vanished from the Inputs tab (even though guitarix was showing input - the meter was responding to my plucking on the guitar).

So i thought maybe a reboot was needed and did so. Upon reboot I had sound again from hydrogen etc but guitarix no longer had any input - i.e. back to square one! (or what appears identical to square one).

---

### Post by Quinflax on 2011-11-25
Update: I will continue updating my progress in this wee battle for the mic in the interests of sharing information. Hopefully this will help folks with the same problem.

Ok, well i did a fresh install of ubuntustudio 11.10 (maybe not what you wanted to hear!). I did not install any of software offered during the Software selection part of the installation process.

After sorting out my graphics drivers I totally ignored the list of updates that were available immediately after installing. I'm going to go through the list carefully and make sure i don't select anything audio related until i'm a bit more knowledgeable (could take a while!)

I have installed (in synaptic) qjackctl, guitarix and rakarrak and everything is working fine :D

I have noticed that pulseAudio no longer appears in the list of Audio connections in qjackctl and that the pulseaudio-module-jack package is marked as not installed in synaptic. I have a strong feeling that this may be the culprit!

To do: sort out updates, install some synths, hydrogen and rosegarden and try and pin down the problem

---

### Post by sgx on 2011-11-26
Hi, when various devices are plugged in/out, the device label
can change, so your saved settings look for a device that moved.
In qjackctl setup page,

Input Device >
Output Device >

click the > widgets and check the hw: settings. I change mine routinely, now that I know they can change themselves, it's no
shock anymore. If the lsusb shows a brand-name, you can use that
instead of hw:0,0 or whatever it is today, which might be hw:1 on Monday :)

I think you can also fill in a name of your choice, which will be saved in your
/home/user/.jackdrc file  that qjackctl writes when you save settings.
Hope this helps.

---

### Post by Quinflax on 2011-11-26
Thanks for the reply sgx.

I remember reading a post on this forum in my search for a fix for my issue that said as much. I think you might have meant cat /proc/asound/cards not lsusb? So I can use hw:system to access my iMic and hw:Audigy for my soundcard. I tried it at the time and got a fail - but it seems the fail was unrelated: I have just given it another go and it works fine!

> I think you can also fill in a name of your choice, which will be saved in your
/home/user/.jackdrc file  that qjackctl writes when you save settings.Not sure what you meant there, dude.

Update: been too busy playing with my iMic/guitar to do anything else. Will mark as solved once I know what caused it not to work - I'm thinking the pulseaudio-module-jack still. No proof though...yet.

---

### Post by sgx on 2011-11-27
Hi, qjackctl writes  a config file called .jackdrc, in your
/home/username folder. This is the command it uses if it is
configured to start jackd automatically. If you have a couple
radically different setups in regular use, you can have separate
jackd command string for each, and turn off  jackd autostart in the
 qjackctl misc settings section. Edit your .bash_history text file, to
keep them near the top, and recall the preferred one easily using the up-arrow key.
Glad you're :guitar: Hope rakarrack, guitarix, and calf plugins are
getting warn out :)

---

### Post by Quinflax on 2011-11-27
Aye, I figured it out not long after posting previous. Going to have to research .bash_history, am guessing i can just use gedit to edit it. Will be handy for switching between my headphone setup and audigy setup - though I think i need to replace the audigy (one day!), as i am getting better performance just using my logitech usb headphones!

Am enjoying it all muchly :guitar:. Giggled like a f***wit when i discovered the pitch shifter in rakarrak...shame about the latency when i use it though. Have settled for laying basslines with normal guitar then using ardour's pitch shift to bump em down post-recording. Fun! :D

---

### Post by sgx on 2011-11-27
There are settings in rakarrack to lower quality a bit, to enable
getting to a happy compromise. Look in the General heading of
nice html help-files, that are at 

/usr/share/doc/rakarrack/html/ or click help/pressF1 when it is open.

If there are several fx on, you can try lowering the quality
on the ones least important to the sum. And there may be
lightweight external fx, from ladspa, or lv2 plugins from
calf, mda or invada etc that can be
used as bread&butter, with rakarrack providing the specialty.
Cheers

---

### Post by Quinflax on 2011-11-28
Thankyou sgx, very useful information there. Will certainly try it all out!

Update: Here is the list of updates (please see attached file) that I was hesitant to install (much to the potential amusement of the more knowledgeable lurkers :p). After bit of thinking I decided that it is probably safe to go ahead and install them and did so. Sure enough my iMic is still chanelling my guitar without any trouble.

Now I am looking at the pulseaudio-module-jack module...and I can feel it looking back! :evil: <- pulseaudio-module-jack.

Dare I install it? Will it be a simple case of uninstalling it again if my iMic + JACK goes ****-up? Or will I be left with a headache?

Stay tuned to find out (when I can be *rsed to find out!)

---

### Post by Quinflax on 2011-12-01
Well, it seems my troubles have absolutely naff-all to do with pulseaudio-module-jack.

I am now back to getting no input through my iMic - I am using the exact same settings in qjackctl as when I was happily playing away.

This evening I switched settings in qjackctl to use my Audigy as the interface so I could play around with midi in Rosegarden and ZynAddSubFX. Messed around for a while and got bored...wanted to play some more guitar. So reloaded the settings that (as i say) have been working fine for past few days. Jack server won't even start!!

Has anybody got any idea what is going on here?

Maybe it's time I tried out other distros...

---

### Post by sgx on 2011-12-01
Being familiar with 3 distros is good luck. In the meantime, try
unplugging the mic, reboot, start your audio apps, run the command

cat /proc/asound/cards

Then plug in the mic, and repeat the command.

Then check if it is listed in command output,
and if it shows up in qjackctl 

Input Device >

and if it works.

Compare /home/username/.jackdrc with the backup version if there is one.

This will document a recent change in qjackctl saved settings.

Cheers

---

### Post by Quinflax on 2011-12-01
I ran cat /proc/asound/cards before rebooting and iMic was present.

Removed the iMic and rebooted, then ran cat /proc/asound/cards and iMic not present.

Plugged it back in and ran cat /proc/asound/cards: present again.

Checked qjackctl Input> and it was there but still not working.

Same goes for the usb headset - no sound coming from it (selected in Output>). The headset works otherwise e.g. youtube vids.

Seems qjackctl has issues with usb generally, not just iMic. Now that the issue seems less specific/more general there are lots of posts to read...

Was going to look at more distros anyway, just more of a priority now. But if the problem is with qjackctl (or is it a jackd2 issue?) will i run into same issue with other distros? Was thinking of trying earlier version of ubuntu studio (11.10 may not have been best choice!), AV linux, pure:dyne (looks interesting) and maybe dream studio...

---

### Post by sgx on 2011-12-02
usb itself is difficult for OS coders to master. Just last night,
there happened an inexplicable change, a class compliant device that once displayed it's name in qjackctl, now is there, and working, but labeled System, instead of a device under System.

You might add Tango Studio and Ubuntu studio 10.04 to your list. Pure-Dyne has a new beta 3.x for testing, which likely would have better modern usb support. It uses a 'nest' file saved to your hard-disk/usbstick, to access your settings in future sessions.

[http://linuxhomerecording.blogspot.com/2011/11/using-multiple-devices-with-jack.html](http://linuxhomerecording.blogspot.com/2011/11/using-multiple-devices-with-jack.html)

a command string with a usb mic is discussed here, which you might modify using the names of your specific devices.

Cheers

---

