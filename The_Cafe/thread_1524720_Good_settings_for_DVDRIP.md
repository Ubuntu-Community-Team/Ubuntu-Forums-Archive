---
title: "Good settings for DVD::RIP"
date: 2010-07-05
forum: The Cafe
---

### Post by Nonno Bassotto on 2010-07-05
I have a lot of DVD that I'd like to turn into avi for easier portability. In the past I have tried DVD::RIP with the default settings, but the result has not been completely satisfying. I'm not an expert of this stuff, so my question is: can you suggest me some reasonable settings to use?

For the size, I would like to stay around 700MB for a 90 minutes film. I mean, I know I can obtain wonderful results with 3GB per movie, but it is not what I'm trying to do.

---

### Post by Dustin2128 on 2010-07-05
well when I ripped LOTR, I needed at least 2GB for acceptable quality.

---

### Post by Nonno Bassotto on 2010-07-05
LOTR is particularly long. Still for medium-sized movies you can find 700MB files of acceptable quality. Any suggestions?

---

### Post by mamamia88 on 2010-07-05
I know this isn't exactly a setting but have you tried k9copy?  works great for me

---

### Post by Nonno Bassotto on 2010-07-05
I read from their site
> Conformément aux dispositions de la loi DADVSI, k9copy ne contient pas de code permettant de contourner la protection des DVD vidéos, ce qui rend impossible la copie des DVD commerciaux.

Still I'd like to archive my DVDs, which are of course commercial. In Italy it is allowed to make personal copies.

---

### Post by mamamia88 on 2010-07-05
> **Nonno Bassotto said:**
> I read from their site


Still I'd like to archive my DVDs, which are of course commercial. In Italy it is allowed to make personal copies.

i say legal schmegal.  make as many copies as you want just don't sell the original or the copies.

---

### Post by NightwishFan on 2010-07-05
These should be of some help.

[https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs](https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs)
[https://help.ubuntu.com/community/K9Copy](https://help.ubuntu.com/community/K9Copy)

---

### Post by cariboo on 2010-07-05
I just finished ripping my DVD collection using vobcopy, it strips out all the extras and just creates a single .vob, while keeping the quality. You end up with some fairly large files, but with the cost of large hard drives who cares.

---

### Post by Directive 4 on 2010-07-05
> **Nonno Bassotto said:**
> I have a lot of DVD that I'd like to turn into avi for easier portability. In the past I have tried DVD::RIP with the default settings, but the result has not been completely satisfying. I'm not an expert of this stuff, so my question is: can you suggest me some reasonable settings to use?

For the size, I would like to stay around 700MB for a 90 minutes film. I mean, I know I can obtain wonderful results with 3GB per movie, but it is not what I'm trying to do.


i find 

Autoadjust, Clipping only (anamorph)

gives good results, the computer don't have to guess what pixels would be if there was 422or something instead of 720pixels in a line.

apart from that 

just transcode by target size to whatever you are happy with,

and i'd just keep the audio as AC3

in case you need to adjust it's timing or such.

deinterlacing as required (zoom to full frame seems to be the only way)

good luck

---

### Post by Nonno Bassotto on 2010-07-06
> **Nonno Bassotto said:**
> For the size, I would like to stay around 700MB for a 90 minutes film. I mean, I know I can obtain wonderful results with 3GB per movie, but it is not what I'm trying to do.

> **cariboo907 said:**
> I just finished ripping my DVD collection using vobcopy, it strips out all the extras and just creates a single .vob, while keeping the quality. You end up with some fairly large files, but with the cost of large hard drives who cares.

Why do people keep asnwering question which are explicitly not asked? This puzzles me a lot.


> **Directive 4 said:**
> i find 

Autoadjust, Clipping only (anamorph)

gives good results, the computer don't have to guess what pixels would be if there was 422or something instead of 720pixels in a line.

apart from that 

just transcode by target size to whatever you are happy with,

and i'd just keep the audio as AC3

in case you need to adjust it's timing or such.

deinterlacing as required (zoom to full frame seems to be the only way)

good luck

Thank you very much for your advice! I will try this way.

---

### Post by aeiah on 2010-07-06
you can't really go wrong with following the same sort of rules that the piracy scene follow for releasing DVD rips. the current ruleset in english is here:
[http://rules.nukenet.info/t.html?id=2009_XViD.nfo](http://rules.nukenet.info/t.html?id=2009_XViD.nfo)

and here's the 2008 italian version:
[http://rules.nukenet.info/t.html?id=2008_IT_XVID.nfo](http://rules.nukenet.info/t.html?id=2008_IT_XVID.nfo)

it should give you acceptable quality and give you an indication of what res is optimal and when to jump from 700mb to 1.4GB for your rips. however, you may find that you want to retain more quality and go up to 2.2gb for all movies, in which case i guess you'll have to experiment. you could also look at x264.

oh, and perhaps check the doom9.org forums. there'll be a lot of discussion on there about video compression.

---

### Post by Nonno Bassotto on 2010-07-06
Wow, these rules seem very detailed! I think this settles my problem. Thank you very much.

---

### Post by stmiller on 2010-07-08
My settings for dvd::rip are: use Handbrake. :)

[http://handbrake.fr/](http://handbrake.fr/)

---

