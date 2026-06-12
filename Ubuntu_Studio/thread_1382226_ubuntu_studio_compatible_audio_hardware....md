---
title: "ubuntu studio compatible audio hardware..."
date: 2010-01-15
forum: Ubuntu Studio
---

### Post by parece06 on 2010-01-15
hey guys, i switched my system to linux last week and download ubuntu and then updated to ubuntu studio. I was looking to make some music on programs like ardour, audacity, rosegarden, and hydrogen. I've got ALSA sound drivers installed and jack is working correctly (though I'm still getting used to making the manual connections). I have an alesis io2 audio interface that I used on windows for recording my guitar directly to my computer. It is either incompatible with linux or I am just not connecting it right. Under Jack connections, it shows up in the ALSA tab as io2 under both the readable and writeable tabs. It doesn't show up on the audio tab under connections, which is how I have routed ardour. I also have a m-audio midair 25 wireless midi keyboard that has the same problem. It shows up under the ALSA tab but not the audio. I'm not really sure if both devices are compatible with Linux. Before I buy new hardware, I just wanted to know if there is anything I can do to get these working. In a nutshell, what I would like to do is plug my guitar into the audio interface and route that to a guitar program (creox?). I then want to route that guitar program to something like Ardour or Audacity so I can record, make loops, etc. Same thing with the midi keyboard. I want to route it to a synthesizer and route the synth to Ardour or Audacity. On top of everything (although this isn't necessarily crucial), I want all playback routed back to my audio interface so I can listen through my nice headphones instead of my shitty pc stereo....I know I probably made this alot more complicated than it is. All I want to do is get my guitar and midi keyboard to record on ardour, rosegarden, or audacity. The effects and tweaking I will learn with time. And I've already searched through all the forums...for days now. Please help, I want to make some tunes. And if it turns out my hardware isn't compatible, can anyone suggest some cheap alternatives that would help me achieve what I just listed. Thanks everyone.

---

### Post by AutoStatic on 2010-01-15
Hello parece06, please post the output of the terminal commands **aplay -l** and **lsusb** _with_ the Alesis connected.
And in QjackCtl the Alesis is probably called 'system' in the 'Audio' tab. And your not making anything more complicated than it is, your wish is completely sane and feasible :)

---

### Post by parece06 on 2010-01-17
[QUOTE]autostatic we meet again haha. Alright this is the output of those commands you gave me. The top half of the picture is the outputs before I plugged in my Alesis. The bottom half is the outputs after I plugged it in. I also attached a picture of my jack connections in the ALSA tab. the iO2 is the alesis. Audio and MIDI tabs are both empty, with and without the Alesis plugged in. I do notice, however, that when I start up JACK, I see the system options in both the record and play sections, when I am under the audio tab. is it looking hopeful?

---

### Post by AutoStatic on 2010-01-18
The Alesis is being recognised. What are your current JACK settings, what is the content of your ~/.jackdrc file? You could try entering 'hw:io2' in the 'Interface' entry of QjackCtl and then start JACK, then you should see something appear in the 'Audio' tab.

---

### Post by parece06 on 2010-01-18
awesome got both my midi keyboard and alesis audio interface working using this method. the only problem i have is the latency/xruns/skips. They all seem to be inter-related. Here is a copy of my jack settings. anything i can do to make the sound a lot "cleaner"??

---

### Post by AutoStatic on 2010-01-19
Yes, don't use your onboard card (hw:Intel), use your Alesis instead (hw:io2). Or am I missing out on something?
If you get the Alesis working then:
- Don't use force 16-bit, I guess the Alesis is a 24-bit capable device
- Install the realtime kernel and check [here]("https://help.ubuntu.com/community/UbuntuStudioPreparation#Real%20Time%20Kernel%20&%20Xruns") to set up your system
- Tick the Realtime option in QjackCtl

---

### Post by thorgal on 2010-01-19
and don't set the number of Input and Output channels, leave the default values (0).

try to use Periods/Buffer = 2 (not 3).

---

### Post by AutoStatic on 2010-01-19
So it's not necessary to use Periods/Buffer 3 with USB devices anymore?

---

### Post by thorgal on 2010-01-19
it used to be ?
The only time I used 3 was for the Intel HDA. 
Could well be that USB devices do require 3.

---

