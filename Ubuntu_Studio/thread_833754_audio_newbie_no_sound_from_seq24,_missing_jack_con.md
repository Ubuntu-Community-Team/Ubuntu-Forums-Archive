---
title: "audio newbie: no sound from seq24, missing jack connections, ..."
date: 2008-06-18
forum: Ubuntu Studio
---

### Post by dr_gap on 2008-06-18
Hi all,
I have just upgraded from vanilla Kubuntu 7.10 to Ubuntu Studio 8.04 (KDE 3), and I want to get the audio stuff working.

I've got no external HW at the moment.

I can hear system sounds ok, and I can play tracks in amarok.  I can hear the drums in Hydrogen. I can use jack to route virtual keyboard to ZynAddSubFX to system and hear that.  But no luck with seq24 or rosegarden.  I've installed soundfonts.

Here are some things that I notice:

When I start seq24, no entries are produced in jack/connections.  I've been following a Ubuntu HowTo on this stuff, and it instructs to make a connection between seq24 and ZynAddSubFX.  But there are no seq24 connection points in jack/connections!

seq24 preferences has a dialog that includes an option "jack connect". Clicking that *removes* a ZynAddSubFX connction point from jack.  Not a connection, a connection point.  And not the ZynAddSubFX application itself.  I have to quit it and restart it to get the connection point back.

Starting rosegarden produces connections in jack between certain ports of rosegarden to system.  But no sound.  (There are several connection points in rosegarden, and I don't know what they mean.)


Starting Hydrogen produces connection points in jack/connections, and automatically connects them to system, and I can hear the drumming.

Starting rosegarden produces TIMidity connection points in jack/connections.  It doesn't appear that TIMidity actually starts.


I sort-of expected to have to make a connection from rosegarden to something like ZynAddSUbFX and then on to system, but there aren't any "rosegarden out" and "ZynAddSubFX in" pairs that could be connected, nor are there any "Timidity out"/"system in" pairs that could be connected.

(BTW, What is TIMidity, and why is rosegarden looking for it?)

There are no entries at all in the MIDI tab of jack/connections.  (Maybe this is normal.)

If stayed with me to the end ... thanks.  I dumped a lot of stuff here hoping that something will ring a bell with someone.

TIA, regards,
dr_gap

---

### Post by dr_gap on 2008-06-20
OK ... with lots of trial and error, I've gotten seq24 to work.
(Once I stumbled on a working setup, it took quite some time to reproduce it :))
I *think* the key was to start ZynAddSubFX *after* seq24 is already running.  I've also been starting seq24 from the command line with the --jack_master option, but I don't know if that's essential.

Oh ... I forgot to check rosegarden.  I don't know if that works yet.

-dr_gap

---

### Post by dr_gap on 2008-06-20
rosegarden works too.
I had to tell it to send it's output to ZynAddSub by using the MIDI management menu item.  It wasn't enough to route rosegarden to ZynAddSub in jack/connections.

---

### Post by goodmanbrown on 2008-07-01
Is it still the case that your midi connections don't show up in qjackctl's midi tab?  That definitely isn't normal.  But since I upgraded to Hardy, that's how it is for me.  Thus I can't do any midi routing through jack, which is frustrating.  If you figured out a way to get it working, please post!

---

### Post by thorgal on 2008-07-01
could be related to the ALSA MIDI layer not working properly ? The most recent jackd can handle MIDI but this is still in progress. The MIDI menu in qjackctl is mostly the direct ALSA layer. So if it doesn not work, I would think your problem lies there.

---

### Post by goodmanbrown on 2008-07-01
Interesting.  In qjackctl's "Connections" window, I can see my midi instruments on the ALSA tab, even though the midi tab is empty.  I can connect the midi instruments on the ALSA tab.  The sound seems very choppy, but it might be that I screwed up something else while playing around with settings yesterday...

I'm beginning to suspect the empty midi tab is a bug in qjackctl.

---

### Post by thorgal on 2008-07-01
no it's not a bug. By default, you have the jack midi driver off (look at the qjackctl setup window, bottom left). And it's fine because you can still use the alsa layer (the ALSA tab in the qjackctl). Could you describe your h/w so we can have a better view ? 

cat /proc/asound/cards

and 

lspci

are useful terminal commands. Just paste the output here.

oh yeah, your MIDI connectivity (ALSA tab) seems to be OK. Your problem probably is the jack sound setup, in which case, you could copy/paste the following (from a terminal) :

cat $HOME/.jackdrc

---

