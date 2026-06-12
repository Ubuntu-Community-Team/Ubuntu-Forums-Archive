---
title: "Audiophile 2496 alsa-&gt;jack port names..."
date: 2009-08-06
forum: Ubuntu Studio
---

### Post by RaumTrug on 2009-08-06
Hi!
I've treated myself an m-audio audiophile 2496 as replacement for a crappy onboard sound, and am now struggling to learn how to use it properly. the whole thing worked plug&play with the alsa driver in ubuntu 9.04, and with the gnome/alsa mixer and envy24control I'm able to configure this thing as expected - the sound is very good!

now my problem is that both envy24control and most notably jack don't make it too easy for you to use that baby: 

A) the envy24control applet behaves a little different than the win/mac tool described in the cards manual when it comes to the monitor mixer: I can rule 8(!) individual (mono) pcm channels; does anyone know what those actually are...??? independent "slots" of the pcm chip hardware mixer, maybe?

B) most important for me, as I wish to use jack: when I fire up jack, the inputs/outputs aren't named properly...I just get 12 inputs (named system.input_1..12) and 10 outputs (similliar). I've been getting as far as that output_1 and output_2 can be used to connect jack clients to the soundcards output...but what exactly are all those others...??? where is spdif in/out, where the monitor mixer in/out?
finding them all out via trial&error would be tedious, so I ask here if someone else has already found out ;) - I'd be really thankful if anyone knows the actual meanings of those ports, or can point to some link where it is described...

btw. is there any way to name the ports in jack/qjackctl...?

thanks in advance!

---

### Post by austin on 2009-11-08
I think there is no way to rename ports ... .(

M2496 works like that:
analog ports are 1 and 2, digital ports are 9 and 10
(applies both to input and output)

in order to use digital in: run program "envy24 control" -> hardware settings - Master clock must be set to spdif in

---

### Post by RaumTrug on 2009-12-06
one late thanks for your response!

I fiddled around a little and found some more info for that card I'd like to share:

as said above, input 1 & 2 are the analog inputs, output 1 & 2 the "main" pcm channels played back, 9 & 10 the s/pdif equivalents.

however, when you activate "Digital Mix L/R" in the "Patchbay/Router" tab in envy24control, you can do some more fancy stuff, like mixing multiple pcm sources in hardware (though jack alone is enough to do it in software): in jack output1 - output8 are then the 8 "pcm" channels in the "Monitor PCMs" tab and can be mixed/panned there - very useful because of the nice meters in envy24control!

also "Monitor Inputs" will let you then zero-latency monitor the inputs (without connecting them in Jack, or you'll get doubled up sound!), just mix them in like the pcm's.

finally capture_11 & capture_12 let you record what's on the hardware mixer - just don't ever connect those to any output, will give nasty feedback!!! recording also works while output in envy24ctrl is set to pcm or whatever.

much fun to you, peace!

---

### Post by sgx on 2009-12-06
Hi, RaumTrug, could you please run the command 

lspci -nn

and down at the bottom of the output, should be something like this:

03:07.0 Multimedia audio controller [0401]: VIA Technologies Inc. ICE1712 [Envy24] PCI Multi-Channel I/O Controller [1412:1712] (rev 02)

I am interested in the (rev 02) part, trying to verify if and which newer 
maudio 24/96 cards work, and which revisions are good to recommend for
linux users, where they were purchased etc.

And thanks for the great info about using the ports in envy24control! :)

---

### Post by RaumTrug on 2009-12-07
hi sgx!

It's an older model, printed on the card itself is "Rev. B" and date of 2004 I think (not sure about the date, and I don't want to open the case & plug out the card right now as you might understand...). 

I've already heard about newer models not working with the delta alsa drivers, which is a big mess imho! I've also heard about those models working with ossv4 drivers; probably someone could look at the sources & expand the alsa drivers if that was true...?

"lspci -nn" gives exactly the same as you stated above: "rev 02"

I purchased the card at germany's major musical gear internet/mailorder store (thomann), making sure it was from the "delta series" & compatible with linux with the sales support guys before I ordered! ...it came with an already opened (and obviously heavily used) package & a sheet of paper with a note regarding "reuse of packaging material for the environment"; I doubt this and guess it was a complaint return model from somewhere, but the card itself & the breakout cable as well as the cd's looked unused, and it worked fine and has great sound, so I don't really care...

but maybe you'll want to open an extra thread for this, the card is pretty widespread so you'll pretty sure find lots of other users of it on this forum!

good luck with your reserch!

---

### Post by sgx on 2009-12-08
Thanks for supplying the information! I think I'll start hoarding soundcards that work ;)

Cheers

---

