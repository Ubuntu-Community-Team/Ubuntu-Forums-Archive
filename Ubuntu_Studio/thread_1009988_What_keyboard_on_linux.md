---
title: "What keyboard on linux?"
date: 2008-12-13
forum: Ubuntu Studio
---

### Post by LK_gandalf_ on 2008-12-13
Hi, I'm thinking to buy a keyboard like Yamaha psr-e 413 or other (M_audio, etc), to play it with and without my laptop (other brand and models options welcome! price around 200€)

Every instruments says it's compatible 100% with windows and mac (the usual story..), but what about linux? How can I know if it will works, expecially with the bundle software? (for example M-Audio's keyboards have always two software to program them)

I actually use kubuntu 8.04 64bit, but I'll swithc to 8.10 soon.

Thank you :)

---

### Post by babarosa on 2008-12-13
Hello Gandalf - cool name ;-)

Using an usb-keyboard (it uses a device class protocoll) you generally will not have problems to plug them into your computer and having them recognized by Ubuntu.
So you are able to record your playing the keyboard with a sequencer like rosegarden or muse and do all the nice editing stuff.
Additionally you won't have problems to change the sounds (and banks) and effects, settings **as long as they use the so called "midi-controller-protocol"**.

**The problem**
Generally you won't be able to use Windows-based editor software which uses "System Exclusive Messages" or even more product specific code, not even with Wine (it does not work with my Korg X5DR, Korg X-50, Korg MS 2000R, Akai SG01v, ...). Emagic's sounddiver program does not work with wine too. They too did not work as vst-plugins using reaper.
I did not find a fine synth editor for linux until now (jsynthlib, ...), winsysex partially works with wine but you have to program your own synth-definitions anyway.

**The solution**
,-) But you can send these "sysex-messages" using **"amidi-software"** which comes with ubuntu (being more tedious you have to send the individual messages opposite to a very nice editor-software).
This way **you can control all of the more hidden features** of your keyboard (for example changing the amount of effect on bus 1, ...), you get the "system Exclusive Messages'" code from the manual.
Additionally if new sound banks exist for your keyboard via "sysex" you can upload them to your instrument.

My conclusion is, although not that comfortable everything can be done also without the enclosed, product specific, very fine windows and mac editors.

My advice, take your Linux notebook to the dealer and test the combination.

Regards,
Michael

---

