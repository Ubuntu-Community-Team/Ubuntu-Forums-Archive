---
title: "Alternative Alternative to PulseAudio in Karmic 9.10 RT Ubuntu Studio"
date: 2010-02-02
forum: The Cafe
---

### Post by mdrake36 on 2010-02-02
Ok guys and gals I have finally locked down Memory. but here is the kicker:frown:
I had to uninstall PulseAudio. I tried everything to avoid it but pulse doesn't seem to want to let ALSA do its thing.
So I had to re-install it cuz after removing it I am un able to get through preferences/sound/alsa and esound doesn't take over for Karmic 9.10 after removing Pulseaudio
I tried all the RTprio junk to no avail. it all led back to PulseAudio

Where all my audio geeks at? we can do this.
I guess I could regress back to Jaunty? oh dear.

---

### Post by NoaHall on 2010-02-02
Easy. Just remove pulse audio and use pure alsa. That's what I use.

---

### Post by mdrake36 on 2010-02-02
> **NoaHall said:**
> Easy. Just remove pulse audio and use pure alsa. That's what I use.
How do I use pure ALSA my sound preferences don't open after purging PulseAudio
I know I have ALSA but in Qjackctl I still just see system in the readable/writable trays.
I tried qamixer but no sound. I must be missing something?

---

### Post by NoaHall on 2010-02-02
This is how I did it - [http://usefulsoftwaregamesandknowledge.blogspot.com/2009/11/how-to-fix-sound-on-ubuntu-910karmic.html](http://usefulsoftwaregamesandknowledge.blogspot.com/2009/11/how-to-fix-sound-on-ubuntu-910karmic.html)

I should clean it up a bit, and add a few more things, but I haven't used Ubuntu in a while.

---

### Post by renanfs on 2010-02-08
Hi guys, this really helped me. Now I can use skype ! But now, I got a new problem. I can´t use my bluetooth A2DP headphone anymore, the tool for that on karmic was a pulseaudio utility. How do I use bluetooth headset with pure alsa ?

Thanks

---

### Post by mdrake36 on 2010-02-08
I now use ALSA always I even mess with the ALSA MidiARP
What is a good VST host for Linux.
I just recently played with Ableton live. it was nice but it was on a mac.
Any sugestions?
Haven't got Alsa Mixer going real well yet.
using QAmixer

---

### Post by &#1057;&#1090;&#1088;&#1072;&#1085;&#1085;&#1080;&#1082; on 2010-02-08
I like lmms. It can load vst and works great

---

### Post by mdrake36 on 2010-02-09
Ok so all my Sound Utilities work and I have my audio priorities straight I think.
I uninstalled Pulse Audio and Now can lock down memory.
AWesome.
BUT..... somewhere in the process my sound card got kinda Whiny. you know like a high pitched modem sound coming through.
I can silence the sound by Starting an application like Ardour then Terminating the Jack Engine. After Terminating the Jack Engine the Sound card is as quiet as a mouse. I can even restart the Jack Engine and the Card stays quiet. Its only when I close the Offline Adour program that the Whine comes back. Also If I were to restart the Jack connection within the Ardour session it would come back. Otherwise if I were to leave Ardour Idle in the background disconnected from the Jack Engine the Card is perfect. 
This is very embarrassing when Comparing qualities with say a Mac Book Pro.





Boo Yeah

I have finally got LMMS to work and I love it but it requires alot of available on-screen memory. Large footprint. But I guess there is no real way around that,to feature those types of parameter controls. 

Cool Beans time for some more RAM.

---

