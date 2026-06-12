---
title: "Weird -really funny- speakers issue..."
date: 2007-11-20
forum: The Cafe
---

### Post by odiseo77 on 2007-11-20
Hi folks, I don't post this in the 'Hardware & laptops' section of the forum because I've realized it's not directly related with the OS (and since it's very funny -in all the meanings of the word-  to me, I'm posting this here; however, if someone has experienced something similar or has some advice, I'd appreciate it, because besides being funny it's a bit uncomfortable too, sometimes). 

Ok, some weeks ago I bought a cheap speaker set (a pair of speakers; Genius SP-S110, to be precise (the box says P.M.P.O 100 watts)). Well, when I'm not listening music, I've noticed some music and voices playing through the speakers at a very low level (started noticing this a few days ago); so I lowered the volume level to zero and I still could hear it. Then I paid attention to it and noticed it's probably a radio station. I also noticed the sounds playing while rebooting, when the mobo splash screen is being displayed, so I assume it has nothing at all to do with the OS (it also happens on Ubuntu and Debian). I supposed that maybe the wireless net card antenna was causing some type of interference with the speakers, so I put the antenna in the floor, nearly one meter from the speakers, but the interference continued there. So, maybe it's just the speakers? What do you people think could be causing the interference; simply a bad speaker set? 

First it was simply funny because it seemed to occur randomly, but I don't know whether it's me being more perceptive about it or the issue has worsen, because it's starting being annoying (maybe because today I've been on Debian and maybe it's more noticeable on Debian? I'm not sure).

By the way, someone told me Genius was owned by M$; is it true? (It would make this situation even funnier :lolflag:).

---

### Post by Lostincyberspace on 2007-11-20
its very possible that it is just the speakers I know their are a lot of cheap speakers that pick up the hand shake of cellphones before it rings.

---

### Post by odiseo77 on 2007-11-20
Hi, yep, I've noticed the issue you describe with some cellphones (and other speakers), so it's probably a cheap and bad speaker set as you say, but this is really weird, and besides it's becoming really annoying now... well, I guess I just have to buy a better speaker set :-/

---

### Post by Palmyra on 2007-11-21
Just saying that the speakers are cheap doesn't actually explain what allows the speakers to play radiostations in a technical way.  Does anyone have a technical explanation?

---

### Post by odiseo77 on 2007-11-21
> **Palmyra said:**
> (...)Does anyone have a technical explanation?

I'm curious too, I don't know much about hardware (and even less about speakers), but maybe, for some odd reason they have some transistor(s) inside? (can't open them to check because they're sealed; don't have screws or anything like that).

BTW, gonna switch to Ubuntu to check, because it's very annoying now here on Debian ](*,)

Greetings.

---

### Post by p_quarles on 2007-11-21
> **Palmyra said:**
> Does anyone have a technical explanation?
Not me, but I do have a wild guess that's probably wrong. :D

If someone nearby has a radio set that uses a similar connection between the receiver and speakers, and both that person's connection and the OP's connection are poorly shielded, then maybe the signal is simply leaking between the two sets of speakers. 

I mean, I can't imagine that cheap computer speakers could possibly have a radio receiver.and wireless connections are (supposed to be) on a completely different spectrum than any public radio station. 

Like I said, this is a wild guess, and shouldn't be taken seriously, as I know nothing about radio signals, other than that they consist of photons. On the off chance that I'm right, though, the problem could be solved with electrical tape.

---

### Post by odiseo77 on 2007-11-21
> **odiseo77 said:**
> BTW, gonna switch to Ubuntu to check, because it's very annoying now here on Debian ](*,)

Well, it definitely was not Debian, as I guessed before. I turned off the PC, with the speakers on and the interference was still there. It's just that it's late here and I'm listening soft music at a very low level, so the interference becomes more noticeable. 


> **p_quarles said:**
> Not me, but I do have a wild guess that's probably wrong. :D

If someone nearby has a radio set that uses a similar connection between the receiver and speakers, and both that person's connection and the OP's connection are poorly shielded, then maybe the signal is simply leaking between the two sets of speakers. 

I mean, I can't imagine that cheap computer speakers could possibly have a radio receiver.and wireless connections are (supposed to be) on a completely different spectrum than any public radio station. 

Like I said, this is a wild guess, and shouldn't be taken seriously, as I know nothing about radio signals, other than that they consist of photons. On the off chance that I'm right, though, the problem could be solved with electrical tape.

If this helps, I'm behind a router and my wireless connection has WPA-TKIP encryption (it's supposed to be a strong encryption; or at least better than WEP). But after reading your post, I happen to test the speakers by changing the distance between them; at about 40+ cm's between them (which is how they're always set), the interference is there (annoying), but if I shorten the distance to, let's say, 10+ cm's the interference level becomes lower (or disappears completely). I also noticed that the interference increases when lowering the volume level to zero and decreases a bit when taking the volume levels to nearly the half. I'm too sleepy and lazy now to do this (it's 1:40 am here), but tomorrow I'll test the speakers far away from the PC to see what happens...

Greetings and thanks for your input, folks :)

---

### Post by mridkash on 2007-11-21
This is called resonance in physics I think. 
There is a coil of wire inside the speaker that is making an inductor of nearly or exactly the same frequency as the radio station. So it amplifies the signal. 
But still I wonder how the modulated signal from radio is demodulating inside the speakers.:confused:

By the way, do you know which type of radio station it is, my guess is it must be AM radio not FM.
Its a guess, may be wrong.

---

### Post by popch on 2007-11-21
> **mridkash said:**
> This is called resonance in physics I think. 
There is a coil of wire inside the speaker that is making an inductor of nearly or exactly the same frequency as the radio station. So it amplifies the signal. 
But still I wonder how the modulated signal from radio is demodulating inside the speakers.:confused:

By the way, do you know which type of radio station it is, my guess is it must be AM radio not FM.
Its a guess, may be wrong.

Presumably it is not the speaker which produces the phenomenon but the amplifier built into the speaker. Some of the leads picks up a fairly strong AM radio signal, and the amplifier 'somehow' demodulates it.

Back when I was a kid we built radios consisting of a diode, a spool of wire and a capacitor. It produced enough of a signal to drive an earphone.

---

### Post by odiseo77 on 2007-11-21
> **mridkash said:**
> This is called resonance in physics I think. 
There is a coil of wire inside the speaker that is making an inductor of nearly or exactly the same frequency as the radio station. So it amplifies the signal. 
But still I wonder how the modulated signal from radio is demodulating inside the speakers.:confused:

By the way, do you know which type of radio station it is, my guess is it must be AM radio not FM.
Its a guess, may be wrong.

> **popch said:**
> Presumably it is not the speaker which produces the phenomenon but the amplifier built into the speaker. Some of the leads picks up a fairly strong AM radio signal, and the amplifier 'somehow' demodulates it.

Back when I was a kid we built radios consisting of a diode, a spool of wire and a capacitor. It produced enough of a signal to drive an earphone.

I don't know about physics and stuff, but what you guys say makes sense and seems to clarify this issue a bit. About the radio station, I can't determine whether it's AM or FM because it sounds very low, but for the type of music they play seemed to be FM (here at least, AM stations play old/traditional music and FM stations play most modern music like rock, etc., and this station plays rock; but I might be wrong, since I don't use to listen radio, so it might perfectly be an AM station).

Greetings, and thanks for clarifying this issue; I guess I ask a pair of good speakers as a christmas gift ;-)

---

### Post by Nunu on 2007-11-21
Please don't take me serious 

But Maybe its your neighbors radio thats playing that you are hearing. :D 

Ok sorry i will take my coat and leave. but to be honest the Radio built with wire, cap and a diode  is probably the best explanation. I had a guitar amp that use to catch Radio channels. Now that was annoying i was probably the only person that had a air guitar amp

---

### Post by mips on 2007-11-21
If you can open the speakers up you could always glue tinfoil to the inside of the speaker housings to minimize interference.

---

### Post by odiseo77 on 2007-11-21
Hi, thanks for the suggestion, but the speakers seem to be completely sealed; don't have any type of screws or sliders, something that allows one to open them, something like that :( so I guess I'll have to get some electrical tape as p_quarles suggested (or maybe stick with heavy music at high volume levels while I don't get a good set of speakers, lol).

Greetings!

---

### Post by bastiegast on 2007-11-21
The cellphone thing has nothing to do with "cheap" speakers! The aplifier picks up the signal somehow.And your problem has nothing to do with your computer. I think as others have said the amplifier circuit in your speakers is causing it. Place a metal cage offer your speakers and it should be solved.

Its not a very practical solution but it should work.

---

### Post by Lostincyberspace on 2007-11-21
What I meant is that the cheap speakers are the ones that aren't shielded. I wasnt thinking well that night.

---

