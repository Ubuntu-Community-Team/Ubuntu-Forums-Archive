---
title: "Moving from Vista to Ubuntu, Looking for simple podcast help"
date: 2008-07-15
forum: Ubuntu Studio
---

### Post by TCWriter on 2008-07-15
I'm chronicling my 30-day trial of Ubuntu on my [CopywriterUnderground.com]("http://copywriterunderground.com/?s=ubuntu") blog, and so far, so good (running on my 17" Dell Inspiron).

I do occasionally produce podcasts (using Audacity), and my old m-audio USB "Podcast factory" mic and USB interface -- which is plug-and-play in Vista -- doesn't seem to work at all under Ubuntu, and I've been told USB-based sound solutions don't work so well in Ubuntu. 

If that's true (and feel free to get this thing working for me), can someone offer me a better path to producing my so-so quality podcasts? How do I connect my active microphone to Ubuntu?

Thanks. I like Ubuntu, and my readers are getting an education.

---

### Post by aeiah on 2008-07-15
yea you might be out of luck. a lot of m-audio stuff works but probably not a lot of the usb stuff as you say. what other stuff do you have? just a laptop and a mic? you could always, say, plug it into the mic socket of your laptop :p although the chances are it'll be **** quality.

out of interest, what does the terminal say when you have it plugged in and you run lsusb? (this will list what usb devices are plugged in, and may help identify if it shares components with something that a driver exists for)

---

### Post by TCWriter on 2008-07-15
Thanks for the lsusb hint. Amazingly, I found it listed under "midiman" and while I can get it to work now, I can't get it to work right. 

I've played with the mic, "recording interface" and Audacity settings, but my voice barely comes across; turning the gain all the way up in Audacity means I can hear it, but it's not suitable for use. 

I had a similar problem on XP; I got it to work, but the sound was pretty faint. 

In Linux, it's unusable. 

FYI: my microphone has one of those monster mic connections on it, so no way it's plugging directly into the laptop. 

Is there a standard setup (condenser mic, preamp, etc) that Linux audio types use?

---

### Post by Stochastic on 2008-07-16
That "monster mic connection" is called an XLR connection, and your particular microphone does not need a phantom powered preamp (expensive), merely a signal boost from a mic level to a line level.  If you're laptop has a mic input on it (usually a 3.5mm - same as a small headphone jack) then your easiest route to success would be to run down to radio shack (or whatever Circuit City tries to rename it) and buy an XLR to 3.5mm adapter (you may need to get an XLR to 1/4" - a guitar jack style - then also get a 1/4" to 3.5mm adapter and hook the two together).  Simply use your inbuilt soundcard as the main soundcard - this setup will cause the least configuration troubles.

Then again, if you don't want to pay the $6-12 for adapters, you may also want to check your alsamixer settings if the mic input is too low.  Simply open a terminal and type ```
alsamixer
``` and make sure all your levels are nice and high.

Also - and I know this is basic, but you'd be surprised at how many issues arise from looking over the basics - make sure you're gain knob on the M-Audio Fast Track USB soundcard is up nice and high (enough to just barely trigger the clipping light) then turn it down a touch so the clipping light disappears.

---

### Post by anderber on 2008-07-17
I got the Samson USB Mic CO1U to work(it's a condenser), the sound is really good and they are reasonably price.

---

### Post by TCWriter on 2008-07-17
Stochastic: Thanks for the info and hints. And yeah, I've got the m-Audio stuff set up correctly (it works perfectly in Vista). The adapter route might be the ticket, though the whole mess seems to have gone a little sideways.

I installed the Ardour package (to see if I liked it), and now Audacity isn't working (running extremely slow, not finding the mic like it did before, etc). 

I'll fuss with this when I've got more time, but it's nice to know a simple adapter could get me up and going.

And thanks for the info on the Samson condenser mic. That's good to know.

Clearly, the Ubuntu Project Continues.

Tom Chandler

---

### Post by TCWriter on 2008-07-17
Just an update for anyone who comes along later. 

Ran the Alsamixer as suggested (thanks), which revealed one "capture" channel was turned all the way down. Ahah! 

Turned it up, but in the meantime I installed Ardour, which installed Jack, which largely killed Audacity. Got that figured and removed Ardour (which is complex) and Jack, and figured I had it made.

Nope. Same issue. 

Audacity recognizes my m-Audio USB source and records the sound, but so faintly that even the full gain setting on the track won't quite do it. And this despite messing with all the settings on the M-Audio "recording interface."

Running the "Amplification" effect in Audacity makes things more palatable, but doesn't quite seem ideal.

FWIW, I had a similar problem in XP with the M-Audio "Podcast Factory" (though not quite as severe), but not in Vista (which auto-installs the M-Audio drivers) which suggests that the output from this admitted piece of crap is low to begin with, and M-Audio's compensating with their drivers.

At least Audacity's working, and perhaps buying an adapter for use with the internal sound card will be enough. Love to test this with a USB Condenser mic just to compare.

Thanks to everyone who helped, and new suggestions are appreciated.

---

