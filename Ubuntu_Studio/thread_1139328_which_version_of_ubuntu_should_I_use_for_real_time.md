---
title: "which version of ubuntu should I use for real time audio work?"
date: 2009-04-26
forum: Ubuntu Studio
---

### Post by _nate on 2009-04-26
I currently have 9.04 installed with the realtime kernel however my system keeps on freezing.  Which version has a decent stable real time kernel that won't keep crashing my system?  If I can't figure it out I will switch back to windoze. thanks

---

### Post by vaughnm on 2009-04-27
I'm looking for an answer to this aswell. I'm currently using Intrepid but was curious about how Jaunty is for having a RT kernel. Has anyone had good results using Jaunty?

---

### Post by WyleECoyote on 2009-04-27
no good luck here either unless I disable one CPU then it works fine, but slow. I just installed the generic kernel it works great but I would like to see what all the fuss of this realtime kernel is about and if it is worth the effort. I can boot into it but it does freeze eventually if not while using, then it freezes at shutdown. htop tells me that CPU2 is running at %100 even in single user mode before anything is loaded as confirmed in this link [https://bugs.launchpad.net/ubuntu/+source/linux-rt/+bug/354816](https://bugs.launchpad.net/ubuntu/+source/linux-rt/+bug/354816) I have tried disabling: onboard lan, onboard sound, C1E support, speedstep, and hyperthreading in the bios. The only success I have had is to disable hyperthreading in my P4 processor, or disable 1 CPU in grub, or where I am at now install generic kernel that works. I tried studio 32 intrepid <--(converted ubuntu mini install to studio) jaunty 32, and I am now using jaunty 64. all of them have the exact same problem. I dont use audio editing enough to even care to try to fix it anymore. I will wait and hope for the best.

---

### Post by angelsguitar on 2009-04-27
I'm a little disapointed with the rt kernel on jaunty too.  Just expected a little more from a "heavily tested" rt kernel.

Intrepid's rt kernel has a lot of problems, so I would recommend you stay away from it. That's why Ubuntu Studio 8.10 doesn't have an rt kernel by default.

From my experience, Hardy's rt kernel (Ubuntu Studio 8.04) gives good performance.  However, in my opinion, nothing beats 64Studio for audio & MIDI work.

---

### Post by babarosa on 2009-04-27
Hi _nate,

I agree with angelsguitar, the most performant kernel is from my experience v8.04 too. I'd recommend using hardy and keeping your software up-to-date using [www.getdeb.net](www.getdeb.net), launchpad and compiling softwares by yourselves. Recommending 64Studio is also a good decision and not a bubble.

I installed v9.04 yesterday, rt-kernel freezes sometimes also on my system. It is really a shame to call it "heavily tested", but it was worse on v8.10 (hence Inusable Ibex).

Ffado, jackd and qjackctl from v9.04's repo didn't work very well. Additionally in qjackctl's "about" menu was written in red letters that something was missing from compilation (?).

Not so after compiling them all by myselves, v9.04's rt-kernel works rock solid so far (what a surprise) [-o< and delivers the same good performance as v8.04 does (that is recording 5 tracks at 44.1KHz, 32bit with "4.35ms" latency for 1 hour without any xruns on my 2GHz Celeron notebook).

The benefits from v9.04 are in my mind for example, I plug in my webcam and for the first time it is recognized automatically.

Good luck,
Michael

---

### Post by _nate on 2009-04-30
Thanks for the info.  I tried 64studio which worked great except for a screen resolution.  I have a ati radeon x1270 and I couldn't get the resolution to greater than 1280x760.  I ended up deleting the wubi install of ubuntu which was 9.04 with the rt kernel.  I created a new partion and installed a fresh version of 8.04 ubuntu studio.  It is working well so far.  I recorded 15 minutes of audio using my firebox with a 2.7ms latency with 0 x-runs. Looks like I will be using 8.04.

---

