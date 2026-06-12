---
title: "monitor and record audio signal from Mic &amp; Line Inputs"
date: 2010-02-08
forum: Ubuntu Studio
---

### Post by amishrobots on 2010-02-08
I am posting this for the benefit of others who may have the same problem i was having. I was unable to send audio from from my input jacks (mic/line) to my speakers, so that while i was recording audio from a separate source (my 4 track cassette mixer/recorder) I would be able to hear the audio through my computer speakers as it was being recorded. Thank You very much to crimsun, who solved my problems via irc.ubuntu.com #alsa . crimsun has also been seen on  #ubuntu-audio-help

it took a while for me to communicate the exact nature of my problem, here is the resulting conversation that solved the issue:

(05:10:37 PM) amishrobots: right now my problem is i cannot seem to send the audio signal from Line In to my speakers at all
(05:10:57 PM) amishrobots: or from Mic either for that matter
(05:12:22 PM) crimsun: so you don't know if you're capturing anything?
(05:12:38 PM) amishrobots: i can record the input blindly, and then listen to what was just recorded, but i cannot monitor the input on my speakers
(05:12:45 PM) crimsun: ah
(05:13:23 PM) amishrobots: i know the input signal is being captured, i just can't listen to it
(05:13:24 PM) crimsun: well, there's a neat something in PA called the loopback module
(05:13:31 PM) crimsun: it does what you're looking to do
(05:13:36 PM) amishrobots: ah
(05:13:44 PM) crimsun: so, pactl load-module module-loopback
(05:13:51 PM) crimsun: then play with pavucontrol

being a newbie i have very little understanding of what this actually does, except that typing pactl load-module module-loopback solved my problems immediately. 

aparently the loopback module is part of PulseAudio, so it would be important to have that installed already. and pavucontrol near as i understand is the pulse audio volume control gui so, apt-get install pavucontrol might come in handy. 

Other terminal commands of interest: alsamixer  ,  amixer  .

as i said, I am a newbie, and understand very little of this stuff, I am posting this to help others, or at least point them in the right direction to solving their problems. Any further explanation of this issue would be appreciated for the benefit of those who may stumble upon this post in their quest for solutions

---

### Post by amishrobots on 2010-02-08
further issues: upon further exploration i have come to realize that while i can now monitor the signal coming into my Line input, it comes out of the speakers with a about a 1 second delay. Anybody know how i can fix that? its kinda hard to operate a mixing board when everything you do takes a whole second to actually be heard. Of course i can just plug headphones into the 4 track machine's monitor output while plugging its line output into the computer's line input, but i would much prefer to hear it exactly as the computer does (for numerous reasons) besides which, doing it that way makes the whole loopback module kind of pointless, except as a general reference to make sure the signal is at least coming in clear when i start recording.

---

### Post by AutoStatic on 2010-02-09
> **amishrobots said:**
> further issues: upon further exploration i have come to realize that while i can now monitor the signal coming into my Line input, it comes out of the speakers with a about a 1 second delay. Anybody know how i can fix that?Hello amishrobots, with PulseAudio you probably can't work around this. PulseAudio is not designed for low latency audio stuff. You might need JACK, that's the low latency sound daemon for Linux.

---

### Post by amishrobots on 2010-02-09
grr. JACK! seems like everytime i install anything JACK related, i immediately have twice as many problems. I don't understand JACK, but i guess if its what i have to use.... any help you could give me as far as installing , and understanding JACK would be very appreciated.

---

### Post by lhaeh on 2010-05-09
I've got the same issue, but never had it before with pulseaudio. The problem here is that it is doing some amount of processing on the signal. AFAIK there is a software triggered switch on the sound card that allows it to pass any input to its output, as well as through its own amp and mixer directly, in hardware. This is how you used to be able to listen to an audio CD back before sound cards could handle CD quality audio. Any ideas on how to do this?

---

