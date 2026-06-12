---
title: "Jack-duplex mode Mackie ONYX 1640"
date: 2009-01-29
forum: Ubuntu Studio
---

### Post by bagwanram on 2009-01-29
Hello!

I have Jack running in 8.10 32bit and I cannot run in Duplex mode, 'capture only' is the only setting that works w/o xruns (records all 16 channels with no probs) but I would like to listen back....

I have tried both the latest reg kernel and the RT Kernel.

Dell Inspiron 1721 laptop 2ghz dual-core 2gb ram 
Mackie Onyx 1640

Also running 8.04 64bit on a dual-core w/6gb ram and it works good in duplex mode.

ALSO!!!!! Many Thanks to all who helped with UbuntuStudio! It is simply amazing to record music with Linux, after about 10 years of Windows recording(cakewalk-->cooledit pro-->Nuendo)! Now let's get some plugins that are as good as Waves and Sonnox.

---

### Post by cobrapatrol on 2009-02-14
Interesting bagwanram.

First off, I'm sorry I cannot suggest any fixes.  I'm fairly new with this.  But I would be interested if any good suggestions come in.

I have been running 8.10 with 2.6.27-11-genaric SMP kernel (64-bit) Quad Core with my Mackie Onyx 1220 with the same result.  Although mine works in duplex, I get no xruns during recording but playback has xruns, audible dropouts and screeches.  And you've tried the rt kernel with no success?  And your 8.04 runs well on a different machine through the same Mackie?  Also 64 bit and SMP?

I have been scanning the forums looking for solutions to either downgrade to 8.04 RT or try the 8.10 RT kernel.  Apparently, I don't need to try 8.10 RT.

---

### Post by neu2buntu on 2009-02-15
post the screenshot of your qjackctl settings ,this may help.also if im not mistaken realtime is broken on 8.10 and most users revert to 8.04..

---

