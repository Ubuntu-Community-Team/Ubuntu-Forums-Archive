---
title: "Phonic Helix Board 18 firefire: it works!"
date: 2010-06-09
forum: Ubuntu Studio
---

### Post by JC Cheloven on 2010-06-09
Hi,

I like to post when I find something potentially helpful for others. This is the case. Assuming some risk, I just bought a Phonic Helix Board 18 firewire device [http://www.thomann.de/es/phonic_phhb18fw_helix_board.htm](http://www.thomann.de/es/phonic_phhb18fw_helix_board.htm)

It could be described as an analog mixer board with a firewire interface. 
In the analog side, you'll find what you could expect in a decent mixer board: 16 ins (of which 8 have xlr phantom), up to 8 outs (4xstereo), 6 inserts, a lot of buttons, built in effects, & such.
The digital part is able to send via the firewire port all independent channels to your DAW, and retrieving 2 channels, for the sake of monitoring from the pc. 

The device worked right away in Ubuntu Studio 9.10. The only needed configuration is done in jack: choosing the firewire driver, and specifying the no. of in/out channels the device has. You're done.

After a couple of days testing, everything was ok. The analog part works as expected with very low (subjective appreciation, didn't measure it) noise/signal ratio. The digital firewire connection does its job with no surprises. Perhaps the surprise is just that, LOL. I made a testing project in Traverso (devel version from git), to record 5 simultaneous channels at 48kHz, 24bit. I obtained no xruns in ~8min of recording. I didn't go further than 32ms with latency though.

A word of caution: I didn't manage so far to send the signal in a post-fader manner to the firewire port. I mean, the gain slider, 3-band equalizer, etc in the (hardware) track controls, don't seem to affect in any way the signal sent to the pc. Only the mic gain knob affects the signal level. If I happen to figure out how to send post-fader to the firewire, I'll update this post. But I'm affraid the device isn't designed that way: "if you use a daw, you'll want to edit there". I asked yestreday the phonic people. Awaiting for an answer.

To sum up, an excellent value for the price (318 eur!). A comparable device may be the Alesis Multimix 16 firewire, but it's a bit more expensive, and seems to require more tweaking to get it working in linux. 

Hope this will help anyone out there!
JC
___________________________

---

### Post by sgx on 2010-06-09
Nice hardware! When you have time to try the fx on acoustic instruments,
it would be nice to read your opinion.
Cheers

---

### Post by JC Cheloven on 2010-06-11
> **sgx said:**
> Nice hardware! When you have time to try the fx on acoustic instruments,
it would be nice to read your opinion.

Sure! :-) 
I just tried the effects feeding the mixer with a dry recording of my chamber ensemble. 

The effects are so mild that I thought they wasn't working, even with the "amount of effect" knob at the maximum. For example, the various rebverbs are really noticed when there is a pause in the music. Then you can ear the reflections. Is like if the recording were done in a large hall, but with the mics so close to the instruments that you can't really appreciate the ambience of the hall.

To sum up, the best I can say about the builtin effects of this board, is that they exist ;-)  
I'm not worried about it, though.
JC
____________

---

### Post by JC Cheloven on 2010-07-09
Just a quick update. This thread is about the Helix Board 18 FireWire. There is another device, very similar, but ~100€ more expensive: the Helix Board 18 FireWire MKII.

I suppose this one works equally well under linux, but I didin't tried it. The main nominal difference is that the MKII is able to send each channel pre or post {fader+3bandmixer+locutfilter} to the firewire port, while the basic model I own sends only pre fader.

May be an important difference for someone...

---

### Post by ronyoks on 2010-08-09
Hi, thanks for the suggestion.....  Hopefully somebody can post a sample mix band application for this mixer. Planning to buy in a couple of weeks here in the Philippines so im trying to get as much inputs and review as possible.

---

### Post by JC Cheloven on 2010-08-10
> **ronyoks said:**
> Hi, thanks for the suggestion.....  Hopefully somebody can post a sample mix band application for this mixer. Planning to buy in a couple of weeks here in the Philippines so im trying to get as much inputs and review as possible.

Im primary a drummer so 8 channels of xlr would be enough for me to use if ill not be recording simulatanious with bass, guitar or keyoard. 
Hi ronyoks, It's never easy to give pointings about this, as there are as many opinions as engineers. Also, I'm not completely clear about your use case, but I guess you're thinking in the helix board as the main digital device plugged to a computer to record your band. Some thoughts that could apply to you:

- If you plan to use 8 XLR mic inputs for yourself, this device could be short for your band: the singer(s) may most likely need some of these. And anyway, what remain for guitars, kb, etc are 2 stereo inputs (4 if you use the 2 aux returns). 

- Have you considered the possibility of an additional analog mixer (cheaper than digital) to mixdown your drums to 2 channels? The idea is that, your band being in a budget, there may not be a need to send every mic in your drums as an independent channel to the computer. Instead, 2-channel mix drums could sent from your mixer to the (digital) device plugged to the computer. This one could be the Helix board or something similar. 

- Conversely, the idea of an additional analog mixer could also apply to some other group of instrument/voices in your band (dunno how big is it...)

- Please note that the device sends everything pre-fader to the firewire port. In practice, this means that all those buttons are useless as for the recording of many independent tracks to the pc goes. All fades, eq, lo-cut, and such, are only applied to the main output, which is stereo. The underlying idea is that if you're using a DAW, you'll want to edit and apply effects there, so the firewire sends only a 'raw' signal. All the buttons are there for the use of the device as an analog mixer. The MKII version of the device is able to send pre fader, which can be of great interest. But I don't have it, so I'm not even sure whether it works in linux or not. 

Tope this helps
JC

---

### Post by rytmisk on 2010-08-18
Seems very interesting! 

Does it work with software that does not support jack? (e.g. java programs, video editors etc)

Best regards
Ketil

---

### Post by sawtdk on 2010-08-18
Hey JC. Are you sure it's working in 24 bits? I can't find in it's specifications that it converts to more than 16 bits.

Mark II, however, does 24 bit.

---

### Post by mrufino1 on 2010-08-20
I have the 24mkII, and it has jumpers on the inside that can be set for pre/post eq recording send. But no way to get the faders to affect recording level though. This is not a problem for me though because I use it to record shows while I am doing sound, so I don't want the firewire send post fader. When I do record not at a show, it is also not really an issue for me, just set the right levels and record. It is a good, clean signal, not a neve but certainly useable. If you go to [www.totalsoul.com](www.totalsoul.com) you can hear live recordings I did with it (background music on the site), and on bigjeffmusic.com, the sound for our video was done through this board (although I didn't engineer it, I was busy playing!)

---

### Post by JC Cheloven on 2010-08-24
> **rytmisk said:**
> 
Does it work with software that does not support jack? (e.g. java programs, video editors etc)
The situation in gnu-linux is that ffado provides the firewire driver. Ffado needs a "client" program. The only ffado client at the moment is jack. So in practice, firewire implies jack, in linux. 

> **sawtdk]Hey JC. Are you sure it's working in 24 bits? I can't find in it's specifications that it converts to more than 16 bits.Mark II, however, does 24 bit. [/QUOTE]
I had the same question, an asked to the Phonic tech support. They were kind and responsive. The answer was (copy-paste with typos included  said:**
> [I]Hi Juan,
Thank you for contacting Phonic ands orry for the delay in our response. The interface is indeed in 24-bit. We do not have a linux driver ourselves, but if you go to (...)[/I][/INDENT]

[QUOTE=mrufino1]I have the 24mkII, and it has jumpers on the inside that can be set for pre/post eq recording send. But no way to get the faders to affect recording level though.
Congrats, great sound and great band that of yours!
It's strange what you say about the MKII. I downloaded the manual, and it is pretty explicit:
[INDENT][I]25. FireWire Pre/Post Switch
This switch is used to change the signal of the corresponding channel that is sent to the Computer via the FireWire interface between that of a pre-EQ, pre-fader, pre-low cut and that of a post-EQ, post-fader, post-low cut. In the upper-most position, the channel will be pre, and in the lower position post.[/I][/INDENT]
In the referenced figure, a switch with a firewire symbol appears just above the "aux I moni" knob. It's accesible from the outside, just as the many other buttons. Maybe there are different variants of the MKII?

Greetings
JC

---

