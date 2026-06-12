---
title: "From Scratch: Recording Studio"
date: 2008-09-01
forum: Ubuntu Studio
---

### Post by Presario on 2008-09-01
Hello people. I a complete noob in ubuntu and mostly on messing with the input and output stuff.

I liek to have some work done in ubuntu during the holidays and I cant seem to get everything to work as planned. What I want to set up is just a mini recording studio. Basically just multitrack recorder software and edit stuff here and there...

What i got is ubuntu studio and an electronic keyboard capabale of general midi and line out audio. I quite an experienced user in FL studio Windows so I know the basics of recording stuff once everything is correctly set up.
The problem is that I cant get around ubuntu to actually work with recording my line in which is connected to the keyboard&#347; line out and also I cant hear anything when I open JACK. once I close jack, i can hear music files.

Basically, I like someone to guide me on setting up a mini recording studio from scratch... from getting my line in to work, JACK and stuf and also softwares that you guys can reccomend.

:confused::confused:

---

### Post by Maucca on 2008-09-02
Me doo have same need of help?

Experienced Acid and Protools User. Never EVER set-up a studio though.

---

### Post by hloupy on 2008-09-02
hmmm i would also be interested to hear how you get on, because i am also a fruity loops person switching to ubuntu .. but now for im still busy sorting out the sound and wireless on ubuntu. 
good luck!

---

### Post by cmay on 2008-09-02
[http://en.wikipedia.org/wiki/64_Studio](http://en.wikipedia.org/wiki/64_Studio)
this is what i used . it is a linux set up to be used for audio production and it works great. i am not recording anymore but i still have it standing as a option to use if i had the time. other advise could be that one should buy good studio microphones and it should be pro quality. i use se electronics. condenser mic. the next thing is a cheap workaround for  mixer you can get the old fostex fd 8 harddisk recorder really cheap now second hand and it works great as a start if a real good mixer is missing in the setup. thats all i can think off right now.
hope it helps .

---

### Post by leepesjee on 2008-09-02
Alas, things have been getting a little more complicated in Hardy, with the introduction of PulseAudio. There are so many things can go wrong now.

I cannot give you a complete step-by-step guide on how to set up a complete recording studio, but i can give you some hints:

- have you looked at the Connect window in Jack? Is your line-in listed somewhere in the Readable Clients (left side). You have to connect it to one of the Writable Clients (playback or recording software).
- Not all audio-applications can work with jack (most will, if you have started jack first). Again you might have to make the connections in jack (if you've worked out how to set the connections, you can make them permanent in Jack's Patchbay).
- Have a look at [http://ubuntuforums.org/showthread.php?t=843012](http://ubuntuforums.org/showthread.php?t=843012) (there are other threads to, just look around a bit)
- BTW, does the jack daemon start at all?

---

### Post by Presario on 2008-09-03
> **leepesjee said:**
> Alas, things have been getting a little more complicated in Hardy, with the introduction of PulseAudio. There are so many things can go wrong now.

I cannot give you a complete step-by-step guide on how to set up a complete recording studio, but i can give you some hints:

- have you looked at the Connect window in Jack? Is your line-in listed somewhere in the Readable Clients (left side). You have to connect it to one of the Writable Clients (playback or recording software).
- Not all audio-applications can work with jack (most will, if you have started jack first). Again you might have to make the connections in jack (if you've worked out how to set the connections, you can make them permanent in Jack's Patchbay).
- Have a look at [http://ubuntuforums.org/showthread.php?t=843012](http://ubuntuforums.org/showthread.php?t=843012) (there are other threads to, just look around a bit)
- BTW, does the jack daemon start at all?

thanks for the link, ill sure to check it out... Jack did start but it gave me the redlight. I followed a guide on the net about setting up Jack but still no progress. it keep giving my buffer problems in the Messages window... nomatter what setting I try. Do your Jack get the errors?

Basically I just need ubuntu to recognize my sound device ( line in, head phone, mic) and for Jack to be fully functional. I'd like to use Ardour(spelling check) for multi track recording.:guitar:

---

### Post by leepesjee on 2008-09-13
A little red arrow means that the jack daemon did not start (a red background of the icon means xruns). If jack does not start, you have to work this out first. What exactly are the error messages?

---

