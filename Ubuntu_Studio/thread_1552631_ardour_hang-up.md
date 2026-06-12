---
title: "ardour hang-up"
date: 2010-08-13
forum: Ubuntu Studio
---

### Post by il lupo on 2010-08-13
Hi, All--

I've been teaching myself to use Ardour and have come against a problem I don't know how to resolve.  When I record a track, I can't hear what I'm recording.  Specifically, I've plugged the ZynAddSubFX into a track and armed it to record.  When playing the keyboard, the level meter tells me I'm getting sound.  I just can't hear it.  This is also true when I've armed the entire system to record and also when I begin recording.  It is only upon playback that I can hear what I've done.

Everything looks as though it's been plugged in correctly.  The Track Audios are going into the Master, which then goes Out to the System Playback. I use Patchage, but get the same results when making the connections through JACK, itself.

My current version is 2.8.8.  Is 2.8.11 available for Linux and would that solve the problem?  I'm not quite experienced enough to compile from source.  Given a good set of directions, though, I believe I could manage.

Many kind regards for any help I get.

il lupo

---

### Post by cchhrriiss121212 on 2010-08-14
Can you connect zyn directly to your system output?

---

### Post by il lupo on 2010-08-14
Yes, Cchhrriiss, I can run Zyn directly into my output.  That solves the problem, per se, but doesn't help me with what I don't understand about Ardour.  Also, once I made the recording, I would have to go back into Ardour and readjust the levels to fit with the other tracks.  I prefer to do it all in one fell stroke, much as a good chamber musician weighs his own sound against the player sitting next to him and the player farthest from him.

Might I comment you on the fine Star Bass and pic?  That is Bootsy, isn't it?  He's the only one I can remember using one.

Thanks, Cchhrriiss!  Send me any more ideas, if you have them.

il lupo

---

### Post by cchhrriiss121212 on 2010-08-14
Yeah that's Bootsy Collins, he had a few different star basses. I always find that image inspirational.

Regarding Ardour, I think it has been designed to perform this way. It was created with recording live musicians in mind, so that might be why there is no monitoring of armed tracks. You might have better luck with Qtractor (though I forget whether it performs differently in this regard).
Do the levels change that much when they have been recorded?

---

### Post by il lupo on 2010-08-14
How odd, Cchhrriiss.  I just installed Qtractor.  I've yet to really play with it, but here's what I've discovered, so far.  When Zyn is plugged into a track (and not the Output), I get sound, even when the track is armed.  When I arm the entire system and begin recording, I get no sound.  Again, how odd.

I won't know if the levels change that much until I start making songs.  But I'm unnerved to know that I will have to go back in and discover what really happened, rather than know what's happening as I'm doing it.  When I studied piano heavily, I would record a take of my piece, make suggestions to myself after listening, and then repeat the process.  Shortly after starting this procedure, my teacher started telling me that I wasn't listening to myself and hadn't any idea just what sounds I was making.  After a month of those lessons, I was practising--with recorder running, as usual--and suddenly heard what my fingers were doing.  It didn't sound too good.  I immediately turned off the recorder, realizing it had become an unnecessary step in a feedback loop--a hindrance, even.  That's what I feel like when I can't hear the sounds as I'm recording.

But I'm a neophyte, here, Cchhrriiss, that's for sure.

---

### Post by madeinfamous on 2010-08-14
allo,

you need to tell ardour to do monitoring,

[https://sites.google.com/site/nueusx/ardourdoesmonitoring.png]("https://sites.google.com/site/nueusx/ardourdoesmonitoring.png")

sorry mine is in french, but a capture will help,

if i remember, in english the line said "ardour do monitoring",

something like that, it work, but i don't use it, :)

---

### Post by il lupo on 2010-08-15
Madeinfamous,

Your solution worked perfectly.  Thank you very much.

il lupo

---

