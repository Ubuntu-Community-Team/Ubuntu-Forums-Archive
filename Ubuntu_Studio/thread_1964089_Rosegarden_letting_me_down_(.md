---
title: "Rosegarden letting me down :("
date: 2012-04-23
forum: Ubuntu Studio
---

### Post by _oscar_ on 2012-04-23
Hi All,
I'm experiencing problems with Rosegarden since my upgrade from UbuntuStudio 10.10 to 11.10 that drive me crazy.

It's not something I can reproduce, but at very random moments, Rosegarden just stops sending and receiving MIDI signals. I can still save files, edit segments manually etc, but whenever I click Record or Play, I just hear a short sound (the actual instruments at the transport position), like a few millisecs, then transport stops and nothing happens.
I don't get any Jack messgages, even no XRuns.

The only way to fix this, is close Rosegarden (doesn't remove the connections in QJackCTL!), all my other Jack apps (usually Hydrogen and QSynth), stop Jack (force it, since it still sees Rosegarden), close QJackCTL and restart everything again.
If I'm lucky I can work for another 15 minutes, sometimes only 2 or 3 :-(

Like I said, no logging, so I don't know where to look. All hints are welcome!

Some details about my setup (the part involved in this issue:
Software:
- UbuntuStudio 11.10
- Kernel 3.0.0-17-generic-pae
- Rosegarden 11.06 (11.11 won't compile...)
 - Jackd with Alsa2Jack

Hardware:
- Elka MK88 masterkeyboard
- Akai ME30P Midi patchbay
- Terratec Phase88 FireWire

This computer (32bit) is dedicated for my studio; nothing special installed there.

---

### Post by sgx on 2012-04-26
Hi, you can run htop to monitor your active applications.
Maybe start a hydrogen beat going with rosegarden, and look
in htop for fairly even cpu usage, memory use not growing,
and apps running that are not needed for music.

Maybe a clue will be revealed, when the crash occurs.
System logs can also be searched at that point.

If startup apps are using lots of cpu and ram, they can be googled, to see if others have problems. You can kill them with htop by pressing a function key, mentioned in the htop gui.

---

### Post by _oscar_ on 2012-04-29
Thanks for your reply!

I checked the system load, but the average is somewhere between 0.30 and 0.45, low CPU usage.

But... I suppose I've overlooked it last time, but there *is* a message in the Jack message box:

 p, li { white-space: pre-wrap; }  JackAudioDriver::ProcessGraphAsync: Process error
 JackFFADODriver::ffado_driver_wait - unhandled xrun
 firewire ERR: wait status < 0! (= -1)
 JackAudioDriver::ProcessAsync: read error, stopping...

So it's not rosegarden (which I managed to update to 11.11.42 last week) , it's a firewire issue.
This gives me something to google for. One thread I found is [http://ubuntuforums.org/showthread.php?t=1764156;](http://ubuntuforums.org/showthread.php?t=1764156;) I do have pulseaudio running and I remember I've heard about issues with Jackl and Pulseaudio before.

I'll kill pulseaudio and see what happens next; suggestions are still welcome, I'll update here when I know more

---

