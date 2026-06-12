---
title: "Live tempo control in jack"
date: 2008-12-29
forum: Ubuntu Studio
---

### Post by warfo on 2008-12-29
Hi everybody!

I'm relatively new to audio production. In the last weeks I've been investigating jack and all its friends and I'm really surprised of all its potential!

My intention is to _use seq24 to create simple "loops" that later on I can launch in a live environment_. These loops would mostly be small synth arrangements done with qsynth, nothing fancy, just background noise ;)

Seq24 seems the best way to get this done as I can very easily mute/unmute the tracks when the moment comes without need to stop it or do anything else in particular. I tried Rosegarden and Muse but they didn't seem so effective for such a "simple" task, considering that I'm just trying to launch simple arrangements here and there and not producing entire songs.

The only problem I see with seq24 (and in all jack-capable tools in general) is that _I don't have any way to change and control the tempo in real time_. Well...It's not that I can't do it, but not in a comfortable way for _live perfomance, where I need to adapt and correct small tempo gaps_...Most of my band's songs have tempo and time signature changes, and we are also not very good following strict tempos!

In example, with my guitar's delay box, I can get this solved very easily by just tapping the pedal at the desired tempo any time. I would love to find something similar for jack/seq24 but I haven't had any luck so far. Does anyone know if this is somehow possible?

Of course, perhaps there are better ways to get this done apart from seq24, so I'm also open for any other suggestions!

---

### Post by djbushido on 2008-12-29
The jack control itself has no tempo control on applications. What you can do is what is called the jack transport-you can press "play" on the jack control box (blue button) and if jack transport is enabled, then all connected applications will start playing. But there is no tempo control from jack itself. I don't really know how to help you, but you might render out the sequences to ardour and then find an application to control them that way.

---

### Post by warfo on 2008-12-29
Thanks for your answer, jack transport is not really what I was looking for but at least now I know this is not going to be that easy...

I tried also Ardour but I see the same problem than in Rosegarden and Muse...you can define and change tempos as much as you like in a "song production" environment...but I'm not trying to produce or record a song, I just need to synchronize midi arrangements in real time with other non jack-based elements like, in example, a drum player who can't keep the right tempo for more than 10 secs! ;)

If anyone knows of any other sequencer or workaround I would appreciate the feedback.

---

### Post by djbushido on 2008-12-29
As far as i know, unless you get a program like mixxx or other turntable/dj program, in linux there is no control over tempo real-time. I could be wrong, but unless i hear otherwise, buy your drummer a metronome. or get a new drummer (seriously-10 seconds?)

---

### Post by warfo on 2008-12-30
Well, probably my approach was not very realistic, I'm still not very familiar with audio processing.

What you suggest makes more sense, very probably I can create and export to audio files the midi arrangements, then use a mixer to control them on stage.

Many thanks again for your help, I will have a look at mixxx (and buy a metronome!)

---

### Post by ingie on 2008-12-31
Hi,

although i hadn't looked at this issue from your perspective, it is something that i want to do myself as well...

i wasn't exactly sure of the nature of the jack "transport" control system until i read this article: [http://www.linuxjournal.com/node/1004080](http://www.linuxjournal.com/node/1004080)

where it outlines how jack control does not *provide* tempo, but will sync any other client providing tempo to other clients requiring one...

which [and i haven't tested this in reality yet, i will tomorrow when i have time] suggests that you could load up seq24 and hydrogen and use hydrogen as the "tempo master" for jack transport...

i imagine that would work like this:

load qjackcntrl, load hydrogen, load seq24

set hydrogen and seq24 to use jack transport.

set tempo on hydrogen [with an empty pattern] and hit play on hydrogen... 

i expect this would start the jack control and sync seq24 to hydrogen's tempo [which can be easily changed with the tempo spinner on hydrogen]

i did try a similar thing using hydrogen and ardour the other night as an experiment - and it worked - but i wasn't trying to change tempo mid-record.

hope that helps [doubly so, as i want to do the same :) ]

cheers,

ingie.

---

### Post by thorgal on 2008-12-31
jack can pass on a tempo (in fact, BPM) from a time master to a slave. Ardour can be set to be time master (there's a button next to the transport mode button to activate it). Usually, I create a tempo map in rosegarden (and therefore, rosegarden is my time master) for my MIDI drumming, I can even ramp it up or down. The drum VSTi will play along the rosegarden tempo map, and I record the VSTi's audio output to an ardour track. The only issue with this is that ardour does not handle tempo ramping so if your composition has weird progressive variations of tempo, ardour cannot be configured to understand such a tempo map. A pity ... but if you only have sudden tempo changes, no problem, you can define new tempo markers in ardour's tempo ruler to match your time master tempo map. I hope ardour will introduce progressive tempo changes as well.

---

### Post by ingie on 2008-12-31
> **thorgal said:**
> jack can pass on a tempo (in fact, BPM) from a time master to a slave. Ardour can be set to be time master (there's a button next to the transport mode button to activate it). Usually, I create a tempo map in rosegarden (and therefore, rosegarden is my time master) for my MIDI drumming, I can even ramp it up or down. The drum VSTi will play along the rosegarden tempo map, and I record the VSTi's audio output to an ardour track. The only issue with this is that ardour does not handle tempo ramping so if your composition has weird progressive variations of tempo, ardour cannot be configured to understand such a tempo map. A pity ... but if you only have sudden tempo changes, no problem, you can define new tempo markers in ardour's tempo ruler to match your time master tempo map. I hope ardour will introduce progressive tempo changes as well.

i think the original poster's point was that he knew he could do it in ardour, by pre-sequencing it... but needed to do it "on-the-fly" for live performance

edit: that's not to say i didn't find your post interesting, i haven't got VSTi synths working yet :)

---

### Post by djbushido on 2008-12-31
As said before, chances are for real-time the best thing to do is render it out and use something like a dj tool for real-time tempo control. The jack transport is an interesting idea (i didn't know it did that), but is really not good for live performance.

---

### Post by warfo on 2009-01-02
I exported the midi sequence to a wav file but I'm still a bit stuck with the tempo issues...

The problem with mixxx (and a couple more of dj apps I've tried) is that when I modify the tempo the pitch changes accordingly.

I've thought about loading the wav files in a looper pedal we have, we could probably use it to control the tempo and as far as I know it doesn't modify the original pitch. 

I will also try to use Hydrogen as the tempo master as ingie suggests.

---

### Post by djbushido on 2009-01-02
sorry, forgot it was pitch, not tempo. but i think there should still be a way around it. Now that i know that, it might be a good idea to use the wav's and the jack transport master tempo idea. keep the wav's just for cpu speed, controlling something like that is pretty hard on cpu's. sorry that i couldn't help more, and good luck!

---

### Post by thorgal on 2009-01-02
I don't know whether it would help but what about an app like freecycle ?
It's a beat slicer.

[http://freecycle.redsteamrecords.com/](http://freecycle.redsteamrecords.com/)

for live stuff, I don't know, SooperLooper ? 
[http://essej.net/sooperlooper/features.html](http://essej.net/sooperlooper/features.html)

---

### Post by babarosa on 2009-03-01
Hi folks!

In the past there were some threads mentioning freecycle and the problem that there is no audio output when using the repository's version.

To my mind the reason is a "corrupted" libsoundtouch-file.

[LIST]It can easily be compiled or downloaded from here [http://packages.debian.org/lenny/libsoundtouch1c2](http://packages.debian.org/lenny/libsoundtouch1c2)
[/LIST][LIST]freecycle can be downloaded from here [http://packages.debian.org/lenny/freecycle](http://packages.debian.org/lenny/freecycle)
[/LIST]

Start jackd/qjackctl and choose alsa, then the audio preview and looping works very fine, if you choose firewire as driver it shows some weirdness but works.

It also should be mentioned that ardour comes with "rhythm ferret", a plugin that offers beat-slicing but does not automatically produce a linked midi-file.

Regards,
Michael

---

