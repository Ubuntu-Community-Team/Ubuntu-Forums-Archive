---
title: "playing audio files at 2x speed or more?"
date: 2008-08-18
forum: Ubuntu Studio
---

### Post by trazan87 on 2008-08-18
Hey

I'm looking for a program that i can use to play a .flac file at 3-6x speed. I tried using VLC, but when i sped up the audio it went silent. Is there some way around this using VLC or is there another program that i can use? I tried with audacity, but i'm getting error messages about my output devices (drivers probably), and some other things.

anyone know how to solve my problem?

Thanks alot:guitar:


[COLOR="White"]notpron - the riddle[/COLOR]

---

### Post by trazan87 on 2008-08-18
anyone?

---

### Post by FatDave on 2008-08-18
This is probably not the most elegant solution, but you can get audacity to do this. Launch audacity, and go to File->Import and pull in the track you want to speed up. Then under the effects menu there is a "change speed" option that will let you enter a percentage to adjust the speed by. There will be a bit of processing time, after which you can play the altered file back or export it to a new file.

Not perfect, but it should work.

---

### Post by trazan87 on 2008-08-20
thanks, i'll give it a try:)

---

### Post by thorgal on 2008-08-20
if you want to play the file at different speed, you can use alsaplayer. It has a transport shuttle that you can toy around with during playback, it can speed up or slow down and even reverse the playback. If you want to record the output, you can always use alsaplayer with the jack output (so you would have the jackd server running in the background, you can use qjackctl to start jackd) and use ardour or any other recorder jack client (like the simple client called jack_capture) by connecting the alsaplayer jack output ports to the recorder's jack input ports. If you have used jackd and jack clients before, it's really straightforward.

---

### Post by trazan87 on 2008-08-21
thanks for the heads up! i'll give alsaplayer a go and see what happens:) i'm still kinda new to linux so i'm learning new things every day.

---

### Post by thorgal on 2008-08-21
alsaplayer is definitely your friend :

[http://www.alsaplayer.org/features.php3](http://www.alsaplayer.org/features.php3)

the first item on the feature list is exactly what you want :)
I don't know how popular this player is but it can play about all sorts of audio formats, is very handy and knows how to be discreet (the basic GUI is quite thin). I kind of like it because I can vary the transport speed in realtime (scrub mp3 files for example) and record the output at the same time thanks to jackd into ardour (I built up a linux DAW in my music home studio, using ardour as the main audio recorder and jack as the audio server).

edit: wrong discussion thread! This message must be moved to [http://ubuntuforums.org/showthread.php?t=893788](http://ubuntuforums.org/showthread.php?t=893788)

---

### Post by thorgal on 2008-08-21
alsaplayer is definitely your friend :

[http://www.alsaplayer.org/features.php3](http://www.alsaplayer.org/features.php3)

the first item on the feature list is exactly what you want
I don't know how popular this player is but it can play about all sorts of audio formats, is very handy and knows how to be discreet (the basic GUI is quite thin). I kind of like it because I can vary the transport speed in realtime (scrub mp3 files for example) and record the output at the same time thanks to jackd into ardour (I built up a linux DAW in my music home studio, using ardour as the main audio recorder and jack as the audio server).

---

### Post by Joeb454 on 2008-08-21
I moved your post, though it seems you already posted it, so I've deleted one ;)

---

### Post by Archmage on 2008-08-21
mplayer can do it [ speeds up, ] slows down.

---

### Post by thorgal on 2008-08-21
@Joeb454 : thanks :)

about mplayer, IIRC it does this in a rather discreet way (i.e. non continuous, it jumps in speed by a noticeable small bit as you type the [ or ] key). The alsaplayer sounds more continous but it's been a while since I played around with varispeed so I can confuse the two.

---

