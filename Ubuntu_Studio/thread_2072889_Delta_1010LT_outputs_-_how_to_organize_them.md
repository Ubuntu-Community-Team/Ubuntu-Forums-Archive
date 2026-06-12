---
title: "Delta 1010LT outputs - how to organize them?"
date: 2012-10-18
forum: Ubuntu Studio
---

### Post by ramjr on 2012-10-18
I've actually been using a Delta 1010 for some time, but it's developed a hardware problem I haven't been able to track down, and I decided to replace it.

The software I use is Ardour/Jack.

Long story short, I decided to replace it with a 1010LT, but I find I'm "missing" the nice, ordered in/out connections on the 1010.  The output for the 1010LT is a set of 8 wires, 7 RCA, with no distinguishing marks I can find.

I use the sound system to record multi-track, but mix down to stereo to output to a simple 2-speaker PA system.

So I have 7 output connectors to choose from.   How do I figure out which ones are 'active', when I select an output connections in software?

Thanks for the help.

Bob

---

### Post by sgx on 2012-10-18
Hi, there are four stereo pairs of rca outputs. If they show up
in qjackctl Audio tab, load a jack-aware media player
like aqualung, or vlc/xine/xmms with the jackd plugin,
play a media file and route its audio output to a 1010lt
output pair. Use an adaptor to connect headphones to the rca,
and listen on each one.
Get, or make 3 colors of tape, to ID the three pairs that
are not the main outs.

If the outputs don't appear in qjackctl, are you using
envy24control, or its the newer Mudita version?
Thats the mixer control for maudio cards
You can still manually find and label the pair,
whether the software shows them, or not

:popcorn:

---

### Post by ramjr on 2012-10-19
Hi, sgx,

OK, that makes sense.  I guess I let the Delta1010LT admonition about powering off the computer before attaching or detaching either breakout cable set, spook me. ;)

Thanks for the suggestion.

Bob

---

### Post by sgx on 2012-10-20
Actually, with cost-cutting on so many circuit boards,
componants may be more at risk than ever. rca i/o
are the only cables I re-position with the power on,
and that is maybe a few times in a year.

Phantom power on/off buttons, have proven to be favorites
for gremlins to launch gear-frying lightning strikes.
Cheers

---

### Post by Odox00 on 2013-04-22
Hello. A little late perhaps ... I had the same problem with finding the contact representing which output / input until I saw that they are labeled. If you look carefully at the plastic on the connectors you will see that it says IN1, OUT1, IN2, OUT2, etc. At least on the wiring harness I have.

---

