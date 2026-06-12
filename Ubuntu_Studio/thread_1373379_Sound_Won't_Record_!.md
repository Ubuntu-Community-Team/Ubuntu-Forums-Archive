---
title: "Sound Won't Record !?"
date: 2010-01-05
forum: Ubuntu Studio
---

### Post by derekeverett on 2010-01-05
Hello Folks! 

First, I apologize if this thread seems familiar. I have posted this problem at earlier stages a few times now. I am making progress, but it is slow in coming and has been very frustrating. I am hoping "fresh eyes" may help me figure it out!

I'll try to explain my problem as briefly, yet as thoroughly as possible. I am dual booting between Vista and 9.10. I have a built-in-to-my-monitor microphone on my HP monitor that sounds terrible so I wish to disable it. I think I have done this. I can no longer hear it anyway. So far so good...

I am running a condenser mic into a mixer and I have connected the mixer to the "in" port on my sound card. The cable I am using to connect the mixer is 2 RCA out and 1 1/8 inch in. (Picture of cable attached)..

With help from previous posts to this forum I have gotten my system so that I can hear in my headphones the output from the mixer, but I can not get the audio to record (trying using Sound Recorder for now). It needs to be noted here that in Vista, using this same machine and same set-up, I have been able to record audio for days now. I had no trouble getting this to work with Windows, so I'm quite sure the problem lies with Ubuntu.

This is driving me crazy! I really, really want to get this working. At this point I have hours invested in this problem. Any suggestions would be appreciated. I have also attached screenshots of Sound Preferences, alsa-mixer, and Pulse Audio Volume control. 

I am dual booting, there is no virtual machine or anything like that and my install was a fresh brand new install a week or so after the release of 9.10. It was not an update from an earlier version of Ubuntu. My system is also up to date.

Thanks in advance for any attempt at assistance.

---

### Post by derekeverett on 2010-01-07
Bump. I'm still stuck :frown:

---

### Post by sgx on 2010-01-07
Hi, use qjackctl and timemachine. Qjackctl is your patchbay, virtually connecting the available audio sources, like your soundcard line-in.

Install and study qjackctl, you use it to start the jackd sound server. It has panels that open when you press buttons like setup, and connect, and tabbed pages on those panels. 


Start qjackctl, click setup in the gui, on the right side, halfway down, are
Input Device / Output Device, click the widgets shaped like >

These will reveal what sound devices are seen by your system.
Select your soundcard.

To record, you can install and use timemachine, a one-big-button recording app that will be listed in qjackctl when you run the command

timemachine

or start it from its icon.

In the qjackctl audio tab, connect timemachine on the right side, to system (your soundcard line-in) on the left side. Place a radio or similar soundsource by your mic for a constant signal, you'll see it monitored in the timemachine interface when the right connections occur. Take notes/pics as desired. You can also open zynaddsubfx, hydrogen, or other software instrument to test recording.

 There will be three tabs in qjackctl, audio, midi, and alsa. The soundcard and timemachine in the audio tab should be connected.
For a synth, start zynaddsubfx. In the alsa tab, zyn will be on the right, your soundcard midi on the left. Connect these, then, back in the audio tab, zyn is on the left side, connect it to both system, and timemachine on the right side. Press the

VirtualKeyboard

button (its abbreviated) on zyn to open its keyboard, and play some sounds, you'll see
activity on the timemachine meters when properly connected.

Follow that routine for each linux instrument, like the hydrogen drum machine.

To record, press the green button in timemachine, it all goes orange while recording. Press it again to stop recording.

Your recording will be a high resolution wave file, looking similar to this:

tm-2010-01-01T00:35:15.w64

You can use 'import audio' in Audacity to load, edit, and convert this file to .wav, mp3 as desired.

Cheers

---

### Post by derekeverett on 2010-01-08
Ok first off, thank you very much sgx. This seems like I might be getting close to finding a solution.

I believe I have installed the two apps you refer too, although I find they have slightly different names. JACK Control and JACK Timemachine were the closest I could find to what you describe.

First problem I think I'm having as I can't get JACK Control working. As soon as I launch it, it stops. I found the setup button/options you discuss, but no matter what I choose for input device and/or output device, if I press the start button it starts for 2 seconds then stops.

If I press the connect button then I see the Audio tab that you refer too, but no applications are listed in the menus/drop ddown boxes. I had a couple running but nothing was listed. Perhaps this is because I can't get JACK Control running?

Thanks again, this has been driving me nuts.

---

