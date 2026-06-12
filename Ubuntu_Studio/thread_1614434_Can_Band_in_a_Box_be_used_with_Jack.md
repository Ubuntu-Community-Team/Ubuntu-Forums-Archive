---
title: "Can Band in a Box be used with Jack?"
date: 2010-11-05
forum: Ubuntu Studio
---

### Post by windeguy on 2010-11-05
I have not been able to run Band in a Box under WINE and get any output sound with Jack running.  Is it possible?

---

### Post by AutoStatic on 2010-11-05
[http://appdb.winehq.org/objectManager.php?sClass=application&iId=1094](http://appdb.winehq.org/objectManager.php?sClass=application&iId=1094)

---

### Post by Pablo_F on 2010-11-05
You probably need wineasio. 

Cheers! Pablo

---

### Post by windeguy on 2010-11-06
Thank you for the replies.  I do have wineasio and can use it to run VSTHost and Reaper. I have seen the link regarding getting BIAB to run using winetricks and WMP10 and have WMP10 and winetricks installed. 

I can run BIAB and hear sound from Timidity but BIAB will not recognize wineasio. I can only hear audio output from BIAB if Jack is not running. 
BIAB does not show up in JACK's connection list ( or in Patchage). That is where I need the help to see if there is some detail I am missing so that I can hear ( and patch) BIAB's audio while JACK is running.

---

### Post by windeguy on 2010-11-10
I was able to download support for DXi instruments which allowed me to use a Hypercanvas VSTi instead of Timidity for sound output.  Hypercanvas is more realistic than Timidity.

I can still hear audio from Band in Box only when Jack is not running. I haven't found any way to get Band in Box to run with Jack. I have no problem running VSTHost and Reaper with Jack.

---

### Post by windeguy on 2010-11-10
[http://www.linuxmusicians.com/viewtopic.php?f=19&t=2507](http://www.linuxmusicians.com/viewtopic.php?f=19&t=2507)

I saw the above thread about getting Jack to work with various applications with some familiar names posting there. I find I am not skilled enough yet in linux to attempt to Jackify Band in a Box. Is it even possible?

---

### Post by Pablo_F on 2010-11-11
I suppose there are not a lot of people running band in a box in Linux. Have you tried selecting jack in the wine audio configuration? maybe use the pulse-jack plugin?

Cheers! Pablo

---

### Post by windeguy on 2010-11-11
I suspected that there are not a lot of BIAB users on Linux. 

I have tried using WINE with ALSA alone selected,  ALSA and JACK both selected and JACK alone selected in WINEconfig but none of these allow me to get sound output from BIAB with JACK running. 

I have no experience yet using PulseAudio and I just re-install PuleseAudio. I now have a PulseAudio applet.  I can start PulseAudio in the 
terminal window using "pulseaudio --start" .  I cannot get audio output from BIAB if I start PulseAudio before I run BIAB.  If I start BIAB first I can get audio output, but PulseAudio doesn't seem to be doing anything for me.

I suspect that the issue is that BIAB does not allow me to select ASIO for audio. If I try to select ASIO, the program hangs up. 
Other windows programs will allow WineASIO to be selected, but BIAB has no such option.  Only MME works as the audio output unless I hear of 
a method to select WineASIO.

---

### Post by eric71 on 2010-11-12
I use BIAB regularly in Linux. I usually just use it through timidity, but if you use qsynth with a soundfont you can use it with jack. Just make sure you start qsynth first with a good GM soundfont loaded, using jack. Set BIAB to use Wine MIDI mapper for output.

---

### Post by windeguy on 2010-11-15
> **eric71 said:**
> I use BIAB regularly in Linux. I usually just use it through timidity, but if you use qsynth with a soundfont you can use it with jack. Just make sure you start qsynth first with a good GM soundfont loaded, using jack. Set BIAB to use Wine MIDI mapper for output.

Thank you Eric. This looks like what I was trying to find. I will experiment with this!.  Thanks again.

---

### Post by bluesscream on 2010-11-19
There is a nice alternative:
[https://www.cs.hmc.edu/~keller/jazz/improvisor/](https://www.cs.hmc.edu/~keller/jazz/improvisor/)
seems to be actually under developement.
Works fine here in jackd via virmidi and qsynth

---

### Post by mnieber on 2012-12-08
> **eric71 said:**
> I use BIAB regularly in Linux. I usually just use it through timidity, but if you use qsynth with a soundfont you can use it with jack. Just make sure you start qsynth first with a good GM soundfont loaded, using jack. Set BIAB to use Wine MIDI mapper for output.

This worked for me, but I had to change the midi output setting in BAIB to "Synth input port". I don't claim that I understand my setup, I just connected the midi_capture ports to the midi_playback ports in gladish, and it worked.

---

### Post by lisati on 2012-12-08
If a thread hasn't had a response in over a year, please start a new thread. Things can change a lot in the space of a few months.

---

