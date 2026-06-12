---
title: "The BS I have to go through - a story of conflicting software"
date: 2007-11-08
forum: The Cafe
---

### Post by FG123 on 2007-11-08
I'm a geek, so naturally I can deal with most problems in Linux, but I found myself with a tricky problem with virtually no help, and the solution was so pathetic I felt it necessary to provide you all with a little story. This will take a while. O:)

Yesterday I reinstalled Ubuntu, because I had repartitioned my drives and moved things around to make better use of the available space. Anyway, so I'm installing all the goodies from the repos and extra programs, and I also install VMware Workstation so I can run Vista. I test my existing virtual machine, works as expected.  Cool? Cool.

Now, today when I launched VMware and tried booting Vista I was delivered a warning about how **/dev/rtc** (the Real-Time Clock) was in use - **Device busy or not responding it said** - and so the timer controlling the VM would be out of whack. This would result in Vista running slower (if that was even possible), or at the very least inconsistantly. Perhaps even more disturbing, the VM was working perfectly yesterday, what had happened? I don't like surprises!

The reported cause is normally due to another program locking /dev/rtc, but various tests didn't show this to be the case, so I'm left holding a fresh Linux install where something broke overnight. There's bugger-all stuff on the net about /dev/rtc and VMware, and virtually nothing on how to fix it if you can't find what's locking it. The most I found was instructions for recompiling the kernel, which was BS because it was working yesterday! So I'm going off like a psycho, killing off processes that may have a subtle effect on the timing of the system, but nothing's happening. WTF you crazy OS, let me control you! Uhg.

Even though I had reinstalled an entire system yesterday, I didn't recall doing anything particular usual, mostly just installing packages. What to do, what to do...

:-k

:idea:

Packages! Must be it right? I must have installed something that somehow either took over the rtc, but wasn't showing up on the processes list (or was not noticeable enough). Now, since this was a new install with a defined partition layout, I was experimenting with more packages than before since this was going to last a long longer than the previous install. So, did I install something **after** testing VMware which caused the conflict not noticed until today?

I had to think hard about this for a while...

:-k

:idea:

You'll never guess what package I had to remove. Ready?

**timidity** :-s

That friggin software MIDI sequencer. I had installed it because I wanted to fool around with Doomsday. When I told Synaptic to uninstall, I checked the terminal messages:

Removing timidity ...
 * Stopping TiMidity++ ALSA midi emulation...

Hrm, interesting. I didn't know it installed a service, or whatever resident process it was. But it had injected itself into ALSA, and I recalled one of the solutions for /dev/rtc was due to an issue with ALSA, albeit different. So, I run VMware again and lo and behold, the thing works without whining at me.

To summarize:

A **software MIDI synthesis** program was able to conflict with a** virtual machine**'s ability to access important system resources.

:roll:

Conclusion - Thank goodness I'm a geek. \\:D/

---

### Post by Lostincyberspace on 2007-11-08
I would have given it the time of. But I have to give you props sticking to it.

---

### Post by init1 on 2007-11-08
Interesting.

---

### Post by roboknight on 2007-12-31
I've been looking everywhere for the source of the audio /dev/rtc hogging... Sheesh... Isn't there a better way to share resources.  Anyway, thanks FG123 for being persistent.  I only got as far as tracking it back to the audio.

---

