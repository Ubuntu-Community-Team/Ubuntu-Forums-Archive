---
title: "Ardour beginner issue: &quot;capture&quot; captures &quot;playback&quot;"
date: 2008-05-15
forum: Ubuntu Studio
---

### Post by acheong87 on 2008-05-15
I just installed Ardour and started recording some guitar parts.  But I notice that "capture" not only captures my line-in, but also any on-going playback.  How can I fix this?  (For example, I'm trying to listen to 'track 1' on headphones *while* recording to 'track 2'.  Unfortunately, when I try this, both line-in *and* 'track 1' get recorded into 'track 2'.)

I'm not sure whether this a problem in Ardour, or something outside of Ardour.  Can someone guide me in troubleshooting this?  I can provide any info (screenshots of sound settings, terminal commands, etc.) asap on request.

Thank you!

---

### Post by Stochastic on 2008-05-16
This is most likely an issue with your mixer input settings.  Open Ardour's mixer (alt+m) and click on the top of your recording track at the inputs section, then choose edit.  This will allow you to select which items are recorded.

If only your mic is listed there, then there's a deeper issue.  Is this playback loop the case in all Ardour projects?  Take a look at your connections in either qjackctl or patchage (do you have jack started through qjackctl or through ardour?) and double check that the mic is the only line going to the input channel of Ardour.

Does that fix it?

---

### Post by acheong87 on 2008-05-16
Hello, Stochastic.  I've read some of your other posts in this forum while looking for a solution.  Thanks for looking!

Yes, the playback loop issue seems to exist in all cases.  I attached a screenshot of the default settings for starting a new project (default-settings.png).  To create new tracks, I simply right click and "add track/bus" (stereo, otherwise defaults).

In the mixer...
[LIST]
[*]The new track's "Input" is "system_capture:1" and "system_capture:2".
[*]The new track's "Output" is "ardour-01:master/in 1" and "ardour-01:master/in 2".
[*]The master track's "Input" is "ardour-01:Audio 1/out 1" and "ardour-01:Audio 1/out 2".
[*]The master track's "Output" is "system_playback:1" and "system_playback:2".
[/LIST]

Do you see anything wrong so far?

I don't know much about qjackctl or patchage.  How can I check whether I have jack started through qjackctl or ardour?  Should I just install qjackctl from the repositories, play around with it, and see what happens?  (Is this safe to do for a beginner?)

---

### Post by Stochastic on 2008-05-16
If you're not sure where Jack is started from, then Ardour is most likely starting things for you.  Try installing qjackctl, then starting jack from there, then open ardour - does the problem disappear?  If not, take a look in the connections window and click the + sign next to all the clients listed.  This should give you a nice view of all the routings to and from your soundcard.

Ardour's In/Out settings you've described sound okay to me, but there may be something fishy going on.  Also, just to be sure, when you're recording and monitoring, could the problem be from acoustic leakage from your monitors into a mic?

---

### Post by acheong87 on 2008-05-16
Thank you!  I installed qjackctl, ran it, and started jack.  The capture-playback-issue disappeared!  I tried to reproduce the issue (just in case it was a fluke that fixed it, not qjackctl) by trying all different permutations of volume/device/ardour settings, but I could not.  Next, I stopped jack while ardour was open, then reconnected to jack from ardour, and everything was still functioning great.  Finally, I exited everything and started ardour alone, and everything continues to work!

Thanks again!

---

### Post by Stochastic on 2008-05-16
Glad to hear that fixed it.  Sounds like there was an issue with an ardour jack config file or something, but qjackctl probably overwrote it.

---

