---
title: "No Playback While Recording Jack/Firepod"
date: 2009-06-07
forum: Ubuntu Studio
---

### Post by Firepod on 2009-06-07
QUESTION:

using audacity audio recorder, how do I get jack to playback WHILE I record (duplex audio)? 

PROBLEM:

When I set the output and input channels for audacity both to the "Jack" settings, set the option "Playback While Recording" to "true", and then I record with more than 1 track i get No SOUND. And when I use Jack for input and default for output I of course get an error: Error while opening sound device. Please check the input device settings and the project sample rate. This is a similar problem with ardour as well (and I assume any other program I may use). Playback Does NOT work alone yet recording works alone.

I attached screen shots of my jack connections page when running ardour (if you need more dont hesitate to ask!)

Any help is greatly appreciated. Thank you very much

P.S. I originally posted this weeks ago with no responses. Please someone help!!!! Even if you know only a piece of the solution! I am that desperate!



INITIAL SETUP (if useful):
fresh ubuntu hardy heron install
through synaptic, I installed ubuntu studio
system>administration>ubuntu studio controls: checked all options, set memlock to 95%
set permissions as exactly specified by this: [http://freebob.sourceforge.net/index.php/FAQ](http://freebob.sourceforge.net/index.php/FAQ)
loaded jack control, in setup chose the following:
realtime
driver: freebob
interface: hw:0

---

### Post by trulan on 2009-06-07
> **Firepod said:**
>  set permissions as exactly specified by this: [http://freebob.sourceforge.net/index.php/FAQ](http://freebob.sourceforge.net/index.php/FAQ)
loaded jack control, in setup chose the following:
realtime
driver: freebob
interface: hw:0

I'm newer at this than you are, so I'm probably not much help - I haven't gotten as far as hooking up my firepod yet.  Just installed Ubuntu Studio three days ago.  I went with Jaunty Jackalope specifically because it includes the new ffado drivers which supersede the freebob drivers.  I know ffado is still a beta but I wonder if it wouldn't be worth your while to check out ffado:  [http://www.ffado.org/](http://www.ffado.org/)

---

### Post by kayosiii on 2009-06-08
I would suggest putting a bit of effort into installing and learning Ardour. It Audacity is a Sound editor that can do multitracking where as Ardour is a dedicated multi track recording program. Also Audacity uses PortAudio to talk to jack which does not work as well as talking to jack natively. Ardour does not have this limitation. In Ubuntu Audacity is best for doctoring difficult files. There are better tools for multitracking.

---

### Post by mypetjaws on 2009-06-09
First things first- check the dials on your firepod. I do playback through the firepod, it works fine. I can monitor and simultaneously listen to the playback. 

On the firepod, there's a mixer knob under the knobs for 'headphones' and 'main level' called 'mixer'. Make sure the dial is at 12 o'clock, half way between inputs(1-8 ) and playback(1-2). This will give you playback thru the firepod. Also, I'm sure you did this but select "duplex" in the "Audio" drop down menu in the Setup window for qjackctl. It's next to the "Sample Rate" drop down menu.

As far as recording from the firepod while simultaneously getting playback on your system, as in monitoring thru headphones while you get playback thru system speakers, is using two different soundcards I believe and implementing this will only cause further instability (according to the ardour manual).

If none of this is helpful, I dunno what else to try. Hope it works for you! Stochastic is the ubuntu/firepod master, search threads with his user name in them. I feel like he's covered most topics on here.

---

