---
title: "Disable laptop internal mic, but no option!"
date: 2009-11-27
forum: Ubuntu Studio
---

### Post by djbon2112 on 2009-11-27
Hello all. I'm setting up a little recording area with my laptop (Dell Vostro 1700, running Ubuntu 9.10), and I've got it all set up nicely. The problem is, apparently my laptop has an internal mic that I've never known about before, and Audacity records that as well as the line in (which is a huge problem because not only am I monitoring my guitar, but also music I play along with, which I don't want to record). However, looking through the new-fangled Ubuntu 9.10 default audio manager, I can't find a way to disable JUST the microphone (and not my line in). Any suggestions?

---

### Post by djbon2112 on 2009-12-02
Has no one else experienced this kind of issue?

---

### Post by mango42 on 2009-12-03
Yes - being of a paranoid nature with full understanding of 'Full Spectrum Dominance' and unwitting contributions to the NSA surveillance database, I make a point of checking that any internal mics are never connected to the net without my knowledge.

Audacity shows this up for me and proves that in the Alsa mixer it is necessary to mute capture as well as 'Mic' after boot-up. Snag for me is I have never been able to get sound out of Audacity when Jack is running so I can't really tell if 'line in' is coupled to 'capture'!

Use a dedicated sound card for recording and switch everything else off?

---

### Post by bcooperb on 2010-02-12
I have the same question. I am on a Dell Studio 1747 It has a good built in mic, But i want to go line in to the mic port to capture in Adacity

---

### Post by acarlstein on 2010-10-27
I have the last version of Mac Pro 15"

For the output of the sound, I don't have problems; however, my internal microphone isn't capturing at all. 

I am thinking seriously to return the Mac if this problem is not solved soon

---

### Post by acarlstein on 2010-10-27
OK I got something really fishy here.

In My Mac Pro 15", My internal mic seems to not work.

If I select "front mic" using QAMix 0.07 and unlock the capture, mi other program Gmerlin visualizar seems to capture the sound (Selecting Alsa as a recording device). However, my other programs such as skype and the recorder doesn't.

If I go to sound, and choose analog input, the mic level is disable. 

I think is problem of the code in the sound setting that is disabling the analog input or doesn't let use the analog input drivers.

There must be a way to forward the input of the front mic in ALSA to the other mic or something like that.

---

### Post by acarlstein on 2010-10-27
After trying many times I think I found the way.
Go to terminal and execute: sudo alsamixer

Press F4 (Or FN F4 if you are using a mac pro like me).

Go to <Front Mic> and press the space to selected. 

Now seems to be working (with a litle statics I have to say but better than nothing.

---

### Post by acarlstein on 2010-10-27
> **acarlstein said:**
> After trying many times I think I found the way.
Go to terminal and execute: sudo alsamixer

Press F4 (Or FN F4 if you are using a mac pro like me).

Go to <Front Mic> and press the space to selected. 

Now seems to be working (with a litle statics I have to say but better than nothing.

Nevermind, it didn't work. the system was forwarding the output sound to the internal input. Dammit :mad:

---

### Post by Brandon.Viking on 2010-11-27
Anyone know if this is possible, I borrowed a Dell Laptop and had no way of disabling the internal mic on the screen, need to if I am going to use the laptop for any recording. 
Man how does this happen? Hardware guys, Dell are you listening?;)

---

### Post by raumkundschafter on 2011-02-21
same problem here with macbookpro - there's no way to disabel the internal mic?!

---

