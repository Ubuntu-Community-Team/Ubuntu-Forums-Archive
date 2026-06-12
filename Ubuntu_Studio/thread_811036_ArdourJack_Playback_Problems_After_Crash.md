---
title: "Ardour/Jack Playback Problems After Crash"
date: 2008-05-28
forum: Ubuntu Studio
---

### Post by logicalfrank on 2008-05-28
I'm using Ubuntu Studio 8.04 and a Lexicon Omega USB interface. It seems a lot of folks have trouble w/ the Lexicon and I did too but I eventually got it working well enough--though w/ a bit more latency than I'd prefer.

Anyway, I was putting the setup through it's paces just to see how much I could throw at it and caused it to crash recording tons of tracks at once, tons of automation, tons of plugins... That is not the problem. The problem is now that I restarted it, it doesn't want to playback the audio. It looks normal visually; the curser goes over the music and the little blue meters on the left jump up and down but there is no sound. It seems like everything is there but I just can't hear it. If I switch to another project, I can hear it just fine--this is w/o restarting Jack or changing settings. In fact, I think I can even record in the one that's messed up, I just can't hear it again once I'm done.

Anyway, this is the error I got:

JACK has either been shutdown or it
disconnected Ardour because Ardour
was not fast enough. You can save the
session and/or try to reconnect to JACK 

Ardour's log had a bunch of stuff like this (it goes on and on):

ERROR]: could not reconnect ardour:Audio 2/out 1 and ardour:master/in 1 (err = -1)
[ERROR]: could not reconnect ardour:Audio 3/out 1 and ardour:master/in 1 (err = -1)
[ERROR]: could not reconnect ardour:Audio 4/out 1 and ardour:master/in 1 (err = -1)
[ERROR]: could not reconnect ardour:Audio 5/out 1 and ardour:master/in 1 

The messages from Jack were something like this (again, on and on):

unknown source port in attempted connection [ardour:auditioner/out 1]
unknown source port in attempted connection [ardour:auditioner/out 2]
unknown destination port in attempted connection [ardour:Audio 1/in 1]
unknown source port in attempted connection [ardour:Audio 1/out 1]
unknown source port in attempted connection [ardour:Audio 1/out 2]
unknown destination port in attempted connection [ardour:Audio 2/in 1]
unknown source port in attempted connection [ardour:Audio 2/out 1]

Any ideas? I am pretty much stuck. Excuse the long post and thanks in advance.

---

### Post by logicalfrank on 2008-05-28
Well--do you ever do that thing where you screw around w/ something all day and can't figure it out and then post your question on a forum only to figure it out yourself an hour later before anyone replies? I just did that. I had to manually set the output in the mixer. Anyone got any idea why it would change on it's own all of a sudden?

Anyway, while I have this thread open, anyone have any suggestions/settings to get this Lexicon Omega working in lower latency? I have periods/buffer at 9 and frames/period and it runs w/o errors unless I really try to push it to break but w/ 104 msec latency. I know w/ USB is hard to get lower latency but I've read that w/ these Lexicons you can get down to 6 msec latency in Windows.

---

### Post by nalmeth on 2008-05-29
I can't explain why the output device was changed, but nice job figuring out what happened.

About the latency, have you installed the realtime kernel yet? The package is called linux-rt. After you've installed it, just reboot and pick the Realtime kernel in GRUB.

---

### Post by logicalfrank on 2008-05-29
Yeah, the RT kernel installed automatically w/ the Ubuntu Studio Audio package, I think. Anyway, I checked in GRUB and it's my default option. I think it might be a matter of fiddling to see how low I can get it w/o problems. Seems like when I had it at lower latencies, the one thing that would cause it to throw errors when it was unexpected was when I moved a window around or something so I'm thinking it might have something to do w/ my video (haven't got a decent card yet, using the onboard on my ASUS motherboard).

---

