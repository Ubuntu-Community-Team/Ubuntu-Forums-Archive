---
title: "virtual sound cable"
date: 2014-03-31
forum: Ubuntu Studio
---

### Post by buffler on 2014-03-31
Running 12.04.2 started with clean install, dual boot on an Acer Got that far, at least, despite win 8.1
Here's what I want to do:   connect two programs that use sound cards to each other with a virtual sound cable, line outs to line ins.
something for Windows apparently exists to do this, but the code I want to run is on Linux (GNU Radio and WSJT)
Here's what I've done. Put on a USB sound card, with a CM2606 codec. in addition to the built-in.
Went through ALSA and Jack wikis, exhausted whatever skills I have with search engines, amassed several pages of notes, found several things I thought were solutions.
Wandered through the swamplands trying to use solutions from past distros, back to 10.04
Messed with the mysterious /etc/modprobe.d/alsa-base.conf, finally getting the USB card to be hw:2
trying to find things that aren't there like /.asoundrc and other /. files in home that supposedly tell things what to do
Tried to use jack for one card and pulseaudio for another, figuring I could cross-connect two physical cards as a last resort. Good luck with that.
I'm hopelessly lost in the Dismal Swamp. 
One would have thought that with all the genius out there, someone would have created a simple (well, if it was simple, I guess it would have been done) virtual connect between two programs that would like to see a sound card.
To quote the Scottish play, "hell is murky"
Is there any way out?
](*,)

Aside:  I wrote my first program in 1958 on a Bendix G-15D. Been through JCL on IBM360, A couple of os's nobody ever heard of, had Commodore pet s/n 564, programmed Fortran, Basic, Forth, C, some C++, and now working on Python, and I have never seen anything like sound on Linux or for that matter, Windows.  


Don

---

### Post by jejeman on 2014-04-01
Explain a little bit simpler, clearer what you want to achive.

As I understand you have two audio cards. You use one program for one card, other program for second card. Why is that? Why not use just one card?

---

### Post by buffler on 2014-04-01
Sorry if I wasn't clear.  I'm trying to run two programs.  Each program is separate, and expects to drive a sound card for it's data stream in real time. . The programs are WSJT, a protocol coder and decoder for radio signals, and GNURadio, a control system for software controlled radios. So for the programs to cooperate, a virtual sound cable connecting them  is needed. Such a virtual cable is available for windows, but not,  apparently, for Linux; at least I have not been able to find one. I thought something could be hacked together, but have not been able to do it.
So, I thought if I drive a real sound card with each program, and simply cross connect the hardware, it might be really kludgy, but would work. I haven't even been able to do that despite a week spent online trying stuff. I was looking for an xyzzy to get me out of the maze
Hence my confusion.
Hope this is more clear.:)
Don

---

### Post by jejeman on 2014-04-01
I think i get it now. You actually don't need two audio cards if you can connect this two applications by virtual cable.
I never worked with this applications, and at glanced look I didn't see that they are JACK aware applications. Are they?
What kind of output does this application produce? What kind of audio backend this applications utilize?

---

### Post by buffler on 2014-04-02
Hi jejeman: You have the gist of it. The WSJT program incorporates something called Portaudio to handle its I/O streams. I don't know if this chunk of code is Jack aware or not. I think it's presently operating at 41500 and sends the same data on L and R channels. Gnuradio has source and sink blocks that can be set up to 48000.  If a way can be found to hook them directly, I'm sure a common 41500 common "clock" is possible. I have been able to run a tone to pulseaudio from the Gnuradio sink, and I can hear it on the HDMI speakers or the built-in sound card output. I can also output to the CM2606 codec USB, and hear that as well as signals from the pulseaudio built-in test lady:).

I can also use the chooser available apparently with portaudio on opening the WSJT and get sounds from that program.  I feel so close, and yet can't seem to actually connect them together.
From my reading of on-line stuff, there ought to be a way to use some combination of ALSA, ALSA loopback,Jack, and pulseaudio to do what I want, but simply can't find the proper incantations. Many of the forum and wiki things I've read seem to be of the frog-poking variety--keep poking until it jumps the right direction, but not a lot of understanding as to why it jumped that way. I need robust and well-documented because both of the programs I'm using are under the same kind of constant revelopment as Linux.
Thanks for your interest!
Don

---

### Post by jejeman on 2014-04-02
I agree that configuring ALSA and pulseaudio is really confusing. It looks like some strange language. And the thing you want can be achieving configuring both of them. 
Here is what I suggest.

#1
GNURadio is JACK aware application. It has JACK driver it is package python-gnuradio-audio-jack. But it is only aviable in 10.04. So, you need to compile it etc. Or you can try 10.04 just to see how it will work.
WSJT can also be JACK aware, because portaudio is JACK aware. (eg. Audacity run on portaudio and it produces JACK ports). But, you probably need to compile WSJT in a way that it's portaudio be JACK aware. Something like
[http://www.nitehawk.com/w3sz/wsjt596hints.html](http://www.nitehawk.com/w3sz/wsjt596hints.html)

Conclusion > Using JACK for virtual cable by compiling both applications to be JACK aware.

#2
You can use ALSA configuration I posted here
[http://ubuntuforums.org/showthread.php?t=2157213&p=12705207#post12705207](http://ubuntuforums.org/showthread.php?t=2157213&p=12705207#post12705207)
to make all ALSA applications all the time to show in JACK. Little tricky configuration...
Also I would disable pulseaudio for this one, by adding
```
echo "autospawn = no" > ~/.pulse/client.conf ; pulseaudio -k
```

Conclusion > Using JACK as virtual cable by configuring ALSA

#3
Regarding pulseaudio you can try to record whole audio output. In 
```
pavucontrol
```On recording tab if your applications shows, then you can change the source for its recording. You can change it to monitoring.
Not that good solution, but it can work.

Conclusion > Changing recording source for an application in pavucontrol.

Maybe this can be useful for you
[http://forums.debian.net/viewtopic.php?f=16&t=110440](http://forums.debian.net/viewtopic.php?f=16&t=110440)

---

### Post by buffler on 2014-04-02
Thanks, jejeman!  I think that WSJT id Jack aware, because when it's started, there's a line in the message stream that "jack is not started".
There's also a hint somewhere that GNURadio can use port audio if it is installed at compile time.
You have give me a lot to chew on, so something IS GOING TO WORK.
I'll get back to this thread when I have tried this stuff some more.
Thanks again for your help.
Don

---

