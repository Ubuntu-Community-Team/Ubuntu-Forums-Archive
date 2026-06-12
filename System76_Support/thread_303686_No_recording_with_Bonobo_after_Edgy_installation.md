---
title: "No recording with Bonobo after Edgy installation?"
date: 2006-11-20
forum: System76 Support
---

### Post by rapha on 2006-11-20
Hi,

just tried to make a small sound recording, which always worked like a charm with the default Dapper install. Now, with Edgy, there simply is no "Recording" tab in the volume mixer. The mike works, but just for listening to (not so) cool feeping sounds :-} ... what am I doing wrong / have I not installed / am I missing?

Thx & Rgds,
Raphael

---

### Post by crichell on 2006-11-20
are you using Sound Recorder for recording?

Right click on the speaker and go to Volume Control
Choose Edit > Preferences
Tick the checkboxes next to the Capture tracks to display them

---

### Post by rapha on 2006-11-21
That's the prob... no capture tracks there :-(
(Got 'em in alsamixer but setting them to 100 doesn't do anyhing)

---

### Post by crichell on 2006-11-21
rapha - i've emailed you a new version of our driver that's being released today or tomorrow.  Install it and go to System > Administration > System76 Driver Installer.  Run the installer and let me know how it goes.  I added a last minute addition for this issue.  (You'll be happy to hear I'm also putting together a wiki page with change log and all those goodies.)

---

### Post by rapha on 2006-11-21
Hey wow, thanks! :-)

Installing it now...

Neat new screens (I just wonder where that progress bar is getting its info from, heheh). Oh and it's only partly in German, everywhere you use stock Gtk buttons. That's a bit odd. If you want it translated into German (could prolly also do French, but would rather not) just mail me your .po file.

---

Okay, rebooted now. And WHEE, all the audio stuff is back! :-)

Your Wiki page should probably contain an explanation of the differences between "Recording", "Recording 1" and "Recording 2" now, as well as a description of the "IEC958" checkbox and the difference between "Mic" and "Front Mic". Haven't even had all these with the original installation IIRC.

---

OT: What's still broken under Edgy is VT switching. Most of the time I get a purple screen on the text consoles (colours can vary tho) and have to Ctrl-Alt-Backspace XOrg afterwards

---

All in all,
thanks a heap!

Raphael

---

### Post by crichell on 2006-11-21
> (I just wonder where that progress bar is getting its info from, heheh)

That's funny - This is my first Python app so I'm still figuring out progress bars :) - call it random bliss

Alsa's recording option are confusing - and they change often.  I suppose they have different tracks and volume control for each input device for a good reason but a single master control for all of them makes more sense to me (and is how it works on my Gazelle Value).

> What's still broken under Edgy is VT switching.

I think I've seen a fix for this before (back in Dapper).  I'll do some searching.

---

