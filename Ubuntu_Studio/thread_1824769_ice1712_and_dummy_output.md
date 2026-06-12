---
title: "ice1712 and dummy output"
date: 2011-08-14
forum: Ubuntu Studio
---

### Post by Bucky Ball on 2011-08-14
Hi all,

I have desktop running 10.04, Hoontech card with ice1712 chip. All sound is registering just fine in Pulseaudio and everywhere else but it's all coming through a dummy output. When I check for the device elsewhere it is there everywhere also. Just not in pulse. I can get no sound from the outboard Hoontech interface through headphones or speakers.

I have checked and everything is unmuted everywhere I can find. This seems to be a common problem. Despite all the websites I have looked at regarding this I can't find a fix. One thing I have picked up is that the soundcard might be getting locked by something at boot? I have checked all that also and nothing else is using the sound card. 

Am I barking up the wrong tree or have I just got something tweaked wrongly?

All suggestions welcomed. ;)

---

### Post by sgx on 2011-08-14
Hi, in part, knowing what you will try to use the hoontech for,
determines the answers, if you are a musician wanting to record
your music, install alsamixergui and envy24control (it may be in an alsa-tools package, if not listed separately in synaptic) It is a mixer specifically for snd_ice1712 devices. And alsmixergui is great
for displaying all the sound i/o possibilities.

run the command

ps ux   if anything named pulsexxx appears,

killall name-of-pulse

then run the command

lsmod

and look for snd_ice1712 or snd_ice1724

If none appears,

run the command

modprobe snd_ice1712 and rerun lsmod

Commands sometimes produce no output when successful,
so a modprobe will reply if there are errors, but not success.

Now qjackctl needs you to pick your sound devices in its setup page.

[https://help.ubuntu.com/community/HowToQjackCtlConnections](https://help.ubuntu.com/community/HowToQjackCtlConnections)

this link has screenshots and details

Input Device >
Output Device >

click the > widgets to see a dropdown list of your soundcard choices.
Your ice_1712 or 1724 device should be listed.

In the qjackctl connections panel (press Connect on the main gui)
you must choose input/output, or capture/playback for each software
and hardware you want to use. The Alsa tab is for midi, the Audio
tab is for audio capture/playback. Each has a left and right side, select an item from each side, and press this panels connect button (not the one on the main gui!) and a connection line is drawn.

In the Alsa tab, a softsynth would appear on the right panel
and a midi keyboard on the left panel, connect them to send keyboard data to the softsynth.

In the audio tab, the softsynth sound output is on the left panel,
and would be connected to your soundcards output, on the right panel.
An fx app like rakarrack would show on the left and right panels,
so the softsynth output would go to rakarrack input, and rakarrack output, would go to your soundcards output.

You could install timemachine to record, and connect the sound outputs
you choose, to the timemachine input, press record, and begin playing.

There may be more, but this is a start.
Cheers

---

### Post by Bucky Ball on 2011-08-15
Thanks for the suggestions.

Well, the main thing that came out of that was hw:0 already in use. This is what I get when I try and start Jack:

p, li { white-space: pre-wrap; }```
creating alsa driver ... hw:0|hw:0|1024|2|48000|0|0|nomon|swmeter|-|32bit
 control device hw:0
 the playback device "hw:0" is already in use. Please stop the application using it and run JACK again
 cannot load driver module alsa

```Also, I'm trying:

```
killall pulseaudio
```But when I run qjackctl it tells me:

```
Suspending Pulseaudio
```So it obviously is not being killed. Should I be trying to kill it with some other command? When qjackctl does open I only get an option for the Hoontech in the 'Alsa' tab. It doesn't exist anywhere else. Nothing does.

But I guess that's because hw:0 is being used by another device. I also have Pulseaudio switched off in the autostart applications so it shouldn't be starting at boot but it is. Guess it's 'auto-spawning'.

* One other thing: Jack won't start, but it did last night. Would that be because it is looking for Pulse but it has been suspended by Qjackctl?

---

### Post by sgx on 2011-08-16
Hi, to disable auto-spawn, edit or create the text file 
called

client.conf  and place it in the folder   /home/username/.pulse  

and add a line to containing "autospawn = no"

When ps ux lists the running processes, use the exact name of the process with the killall  command. Run  ps ux   again to verify the death. (not all apps error messages are accurate!)

Now reboot, no web browsers, skype etc, and start qjackctl, and check
the  > widgets again.  If you feed a cd player/radio or similar constant output to your hoontech line-in, you can hear/see when qjackctl connections are successful. Also check your motherboard sound outputs.

You can blacklist the motherboard soundchip by having the root user create a simple text file called blacklist, in the folder modprobe.d

/etc/modprobe.d

my file is just

blacklist snd_intel8x0

use sudo gedit or sudo kwrite, to run text editors as root.

You can also shut off a soundchip in the bios.

Cheers

---

### Post by Bucky Ball on 2011-08-17
Thanks sgx but no different. I should add that this has only been a problem since upgrading from 8.04 to 10.04. All working great 'out of the box' with 8.04. Progress, ay? ;)

---

### Post by Bucky Ball on 2011-08-17
Well, I got somewhere. I followed the steps on [THIS]("http://www.nbl.fi/%7Enbl4321/?p=491") page and got sound! The only thing is no volume control I have installed will control it, it is LOUD, and Pulseaudio Volume Manager won't open (Connection Refused error) to test if that will turn it down. 

I fumble forward ...

Just refreshing my setup: I have the Hoontech DSP24 which consists of ice1712 sound card connected to an eight analogue input/MIDI in/out/thru outboard audio interface. I have my headphones plugged into that for testing so any sound that is coming to the cans is coming from the ice1712 card in the box.

Whatever I try, Pulse won't die, so I went this way. Not ideal ...

---

### Post by sgx on 2011-08-18
Have you installed envy24control? It's a dedicated ice1712 mixer (or it's new nikname 'mudita'?
Scroll right to the analog volume sliders, and see if they are finding sound. (nice link you found! bookmarked :D )
Cheers

---

### Post by Bucky Ball on 2011-08-18
Funky. Cheers. Never thought of that; envy24control does control the volume. Sound through headphones and speakers, sweet.

Just one thing; in envy24control, I am getting output levels in the 'Monitor PCM' tab on PCM1 and 2. They both have left and right sliders and both work to control sound level. Why is that? Also, in 'Patchbay/Router' I can set H/W out 1 and 2 to PCM or Digital out and they both work.

I will do a little digging for a guide to envy24control (and keep experimenting) when I have some time later but any ideas for now? Not quite ready to declare this solved. ;)

---

