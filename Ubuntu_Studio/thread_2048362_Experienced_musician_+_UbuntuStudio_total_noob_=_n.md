---
title: "Experienced musician + UbuntuStudio total noob = need help for first steps"
date: 2012-08-26
forum: Ubuntu Studio
---

### Post by Andrei63 on 2012-08-26
Dear friends,  I need some very, very, very basic help.  Here is my situation:  I consider myself an experienced musician with something in the range of 30+ years of guitar, mostly acoustic jazz.  I have also been using GNU/Linux (mostly Ubuntu and Debian) for the past 10 years.  However, I have never used *any* digital device to record music and this is what I want to do now.  Let me explain:

My current instruments: a cheap but decent electric guitar (LesPaul imitation), a wonderful Ovation 1613 (nylon strings) guitar, a Yairi classical guitar and a Yamaha GL-1 Guitalele.

My hardware: two computers (desktop 2xAMD 64 2x1GHz, 4GM RAM, ATI SBx00 Azalia; laptop 2xAMD 64 2x2GHz, 4GM RAM, Nvidia MCP67) with UbuntuStudio installed, a Zoom H2n recorder and a Kustom KAA30 amp.

My goals: to record myself playing all these instuments and then mixing the tracks to make it sound like severals musicians are playing together (overdubbing).

My problem: I took at look at Audacity, LMMS, Ardour, Jack, Rosegarden, Qsynth, and I am *totally* overwhelmed.  In fact, I can't even get a sound out of most of them since I don't understand what "Jack" is or does.  Rather then RTFMs for them all, I would appreciate it if you could tell me which application I should study and then use to do the following:

a) record myself (using the Zoom H2n recorder)
b) improve the sound of the recorded instument (either during the initial recording or after)
c) mix the various track I record
d) possibly adding sounds/effects

For d) I mean the following: I do not have a bass guitar, but I can play a bass line on any of my instruments.  Could I, for example, record a bass line on my electric guitar and then make it sound like a real bass guitar is playing?  Also, I would love to add some basic percussion loops (Bongo, Conga, Goblet Drum).  So my questions are:  

a) which applications shall I use at each step of my plan?
 
b) were can I find a "Jack for Complete Idiots" -type of text/video to read/watch?

Thanks a lot for any pointers

Andrei

---

### Post by CrocoDuck on 2012-08-26
Hi. Jack is strange, expecially at first sight. Have a look at here: [https://help.ubuntu.com/community/HowToJACKConfiguration](https://help.ubuntu.com/community/HowToJACKConfiguration) . On your ubuntu installation ALSA is the default audio driver. Jack is used to ensure low latency in audio applications: is a lowlatency server. Qjackctl Is confortable to configure and launch jack. With him you can tweak the right setup. The main parameters to keep on eye: Sample Rate, Frames/Period and remember to set Input and Output devices. The objective is to get the lowest latency compatible with stability (i.e. the capacity to run without too much xruns, that sounds like sample loss).

Once launched jack you 'll find that, opening the connection tab on  Qjackctl, programs can be linked with virtual wires, as if they were  guitar stompboxes. There are programs (Patchage for example) that are very confortable to do it.

You can use Ardour for everything you need: recording, mixing, working tracks and adding effects. Have a look on it, there's also some kind of manual online: [http://en.flossmanuals.net/ardour/](http://en.flossmanuals.net/ardour/) . For drums-percussion related stuff I suggest to use Hydrogen. There are programs that let you to run effects and plugins while playing (Guitarix, Rakarrack, calf host, jack rack etc...). You can route the input and output of those programs and record the sound as processed by them. On Rakarrack you can find an harmizer, you can set it as octaver. Mixed with other effects, expecially EQs, is good to "bassize" the guitar.

I suggest you to start from tuning the best jack setup. When you reach it, start recording with Ardour and experimenting with other programs.

---

### Post by sgx on 2012-08-27
> **Andrei63 said:**
> Dear friends,  I need some very, very, very basic help. 
Thanks a lot for any pointers

Andrei
For guitar, get a Fender Mustang 1 usb modeling amp, works perfect in
linux $110 maximum, 12 Fender amp models, misc fx,
and you can save 24 presets to the main dial, best guitar sound-per-dollar anywhere. Linux Mustang editor software is mentioned in this review:

[http://www.linuxjournal.com/content/plug-and-fender-mustang](http://www.linuxjournal.com/content/plug-and-fender-mustang).

[http://www.youtube.com/watch?v=Wl2Q8SNVnPU](http://www.youtube.com/watch?v=Wl2Q8SNVnPU)

[http://piorekf.org/plug/](http://piorekf.org/plug/)

For basic qjackctl connections, see my post to rapattack,
few topics below, and the wiki,

[http://en.wikipedia.org/wiki/Qjackctl](http://en.wikipedia.org/wiki/Qjackctl)

link 4 for jackd, link 8 for qjackctl.

rakarrack and guitarix are fine linux amp/fx software, and
team up with the Mustang amp, in amazing ways.

timemachine is a great simple recording app, and ardour is
a fine multi-track recorder. Audacity can import timemachine
high quality .w64 files, edit and export them, and also the various common formats you can choose in ardour.
vlc can play the .w64 files, and you can record that while
jamming along, for easy overdubbing.

In youtube, look for hydrogen, ardour, zynaddsubfx, the videos
often start with the qjacktl connections gui.

Cheers

---

### Post by Andrei63 on 2012-08-27
Dear CrocoDuck & sgx,

Thank you both for your replies! I will read up on the apps you recommend (and maybe come back later with a few more questions).  Just a quick question:  what are the pros/cons of using Ardour vs Audacity vs Timemachine to record?

Thanks!

Andrei

---

### Post by CrocoDuck on 2012-08-27
I think I've never used Timemachine. I'm usually use Ardour, he can gives to you useful and professional tools not included in Audacity (expecially to organizing tracks, or the ability to run effects without rendering the tracks anytime, control's automatization etc...). Those programs are all good, try them and choose the one you feel confortable with.

---

### Post by Andrei63 on 2012-08-27
Ok, I am a total "newbie" panic mode ](*,) I can't even figure out two basic things:

a) my laptop has a builtin mic (top of the screen) and a small hole at the front to connect an external microphone.  I don't want to use the (horrible) builtin mic.  I want to connect my guitar to the mic-in hole via a 1/4 inch Stereo Female / 3.5mm Stereo Male Adaptor.  When I do Audacity stops using the builtin mic but it does not say what it "sees".  What is this input device call for Jackd?!  And if I want to connect my electric guitar to my laptop and hear it through my headset, what is the output device?

b) I took a look at the jack configuration page ([https://help.ubuntu.com/community/HowToJACKConfiguration](https://help.ubuntu.com/community/HowToJACKConfiguration)) but I don't understand anything at all.

Guys, is there something like "Jackd for total cretinous retards" out there which could help me get just the very very very basic Jack configuration rules?

Thanks and sorry for the terminally dumb questions...

---

### Post by jejeman on 2012-08-27
Jackd only knows what driver (ALSA or ffado) tells it. You will always see capture_1 caprture_2 etc.
You need to set your input on driver level. You can use pulseaudio settings, if you use pulseaudio, or alsamixer to set desired input.

---

### Post by sgx on 2012-08-28
> **Andrei63 said:**
> 
my laptop has a builtin mic (top of the screen) and a small hole at the front to connect an external microphone.  I don't want to use the
(horrible) builtin mic.  I want to connect my guitar to the mic-in hole via a 1/4 inch Stereo Female / 3.5mm Stereo Male Adaptor. 
When I do Audacity stops using the builtin mic but it does not say what it "sees". 

On the far right of the qjackctl Setup page,

Input Device  >
Output Device >

click the  >  widget on the right side of
Input Device >  to open a dropdown list of your audio devices.

run two commands

arecord -l
cat /proc/asound/cards

the portion of the command output shown in brackets, should be similar
to items in the dropdown list.  crank up the amp, so you can hear the hum when the right connection is made. (careful no-one strums it)

If there is only one laptop input, it may be some combo jack hybrid
of mic/line. Check the laptop specs.

audacity preferences lets you choose jackd for audio source,
but 'portaudio' is the name audacity presents to qjackctl, but only
>after< the record button is pressed. (how intuitive!!!) For audacity,
 
Start qjackctl
start audacity
choose jackd in audacity recording/device preferences
Press record
press pause, 'Portaudio' now appears on the right side

highlight both 'System' on the left, and Portaudio' on the right, with a mouseclick,
and press the Connect button, lines will be drawn between the items.
(Don't mistake and press the Connect button on the main gui, use the one on the Connection page)

press pause again to resume recording, and edit the silence later.

'System' will be on both the right and left of the qjackctl
audio tab, click the little widget by System, to see its
'capture' on the left, and 'playback' on the right.

highlight both 'System' on the left, and Portaudio' on the right, with a mouseclick,
and press the Connect button, lines will be drawn between the items.

Timemachine will display its one button gui, and appear in qjackctl for connection to System, no pause etc. Very high quality default recording, using Sony .w64

The usb amp I mentioned really changes the whole game, from futzing
with unsuitable gear, to simple and sublime excellence, 10 used ones are at the GuitarCenter used gear website, $50 to $80

(New ones include Amplitube Fender LE, which adds 3 great Fender
amps to the free Amplitube Custom Shop) Another topic...
Cheers

[http://www.youtube.com/watch?v=YXIFi2LPQp0](http://www.youtube.com/watch?v=YXIFi2LPQp0)

[http://www.youtube.com/results?search_query=audacity+ububntu&oq=audacity+ububntu&gs_l=youtube.3...1486.1486.0.2105.1.1.0.0.0.0.365.365.3-1.1.0...0.0...1ac.HcQ78SmO_EY](http://www.youtube.com/results?search_query=audacity+ububntu&oq=audacity+ububntu&gs_l=youtube.3...1486.1486.0.2105.1.1.0.0.0.0.365.365.3-1.1.0...0.0...1ac.HcQ78SmO_EY)

Cheers

---

### Post by CrocoDuck on 2012-08-28
I found this: [http://www.youtube.com/watch?v=fMz6fDGBnA4](http://www.youtube.com/watch?v=fMz6fDGBnA4) . Of course, as you have jack already installed, you don't have to follow the part that speaks about installation. Don't worry about how difficult it looks: configuring jack is actually easy (if there aren't issues), easier than saying someone how to do it!

---

### Post by Andrei63 on 2012-08-28
Guys, thanks *a lot* for your kind patience and for all the very useful pointers and explanations!   I really appreciate it.  I am going to play around with these apps until I figure out the best combo for me.

Many, many, thanks,

Andrei

---

### Post by sgx on 2012-08-28
Its fun to offer suggestions, we all went through the same things,
and there are always new things we get to learn, and we'll go through them again.

A 3 ghz desktop P4 is quite affordable, and with an m-audio
pci soundcard, an nVidia video card, and a Mustang Amp,
your configurations will be simple, and results will be great.
Probably doable at $300, if you shop skillfully, and less if
you source used items, or do horse-trades. 
:guitar:

---

### Post by gunterkoenigsmann on 2013-02-06
In your first post you mentioned you own a Zoom H2n. 
Since I found no tool that allows to directly edit surround recordings made with this device I wrote a command-line tool (h2n2flac, [http://launchpad.net/h2n2flac](http://launchpad.net/h2n2flac)) that when given the name of the MS or the XY file of a recording creates a single flac file with the surround recording (that can be edited with tools like audacity and converted to ogg or mp3 easily).
A pre-compiled version of the tool can be found at [https://launchpad.net/~peterpall/+archive/h2n2flac](https://launchpad.net/~peterpall/+archive/h2n2flac)). Don't know if it might be useful for you.

---

### Post by Andrei63 on 2013-02-07
Thanks a lot for posting this. I will check out the script. 

Cheers!

---

