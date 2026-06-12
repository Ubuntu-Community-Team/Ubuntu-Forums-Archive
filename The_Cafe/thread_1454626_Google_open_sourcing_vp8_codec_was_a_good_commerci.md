---
title: "Google open sourcing vp8 codec was a good commercial strategy?"
date: 2010-04-14
forum: The Cafe
---

### Post by madjr on 2010-04-14
well 1st i got to say that the quality looks good

[IMG]http://www.muylinux.com/wp-content/uploads/2010/04/VP8_vs_H.264.jpg[/IMG]



well i know they purchased on2 and the codec, cause they would be paying lots of royalties in a few years

now they've been helping dev/optimize Ogg Theora for arm
TheorARM

i think the motive for opening it up was because Ogg Theora was voted down over H.264 as the html5 standard by Apple, microsoft and others

ogg Theora wasnt ready (but it might be in a few years)

since the clock was ticking they acted fast and went with the v8 head on for the standard

well thats what i think

---

### Post by JDShu on 2010-04-14
What is the advantage to Google though by opening up vp8? This is what has confused me.

---

### Post by chris200x9 on 2010-04-14
w00t good news I was just reading about them maybe doing it the other day I'm glad it happened now flash can die! I'm especially happy because I just switched my server / desktop to freebsd.

---

### Post by loell on 2010-04-14
> **JDShu said:**
> What is the advantage to Google though by opening up vp8? This is what has confused me.

for the HTML5 Video plan domination. :D

---

### Post by Judo on 2010-04-15
That comparison is a lie.  For an expert opinion on VP8, see Dark_Shikari's posts in [this doom9 thread]("http://forum.doom9.org/showthread.php?t=141107").  (Dark_Shikari is x264's developer for those that don't know.)

Personally, I rather like it.  Although some of VP8's techniques are a little odd, it does seem quite efficient with current hardware.  If nothing else, it's vastly better than Theora.  However, I'm certain it won't get anywhere without an implementation as good as x264.

---

### Post by ad_267 on 2010-04-15
"was"?

They haven't actually done it yet, it's just a rumour.

---

### Post by chappajar on 2010-04-15
> **Judo said:**
> That comparison is a lie.  For an expert opinion on VP8, see Dark_Shikari's posts in [this doom9 thread]("http://forum.doom9.org/showthread.php?t=141107").  (Dark_Shikari is x264's developer for those that don't know.)

Personally, I rather like it.  Although some of VP8's techniques are a little odd, it does seem quite efficient with current hardware.  If nothing else, it's vastly better than Theora.  However, I'm certain it won't get anywhere without an implementation as good as x264.

Dark_Shikari seems about as far from impartial as it's possible to be.
No-one outside of On2 and maybe Google has seen the source code for VP8 yet, so I don't think he would be able to offer an expert opinion yet even if he were impartial.

---

### Post by Guitar John on 2010-04-24
I can't help but wonder how this will effect Theora, which itself was based on vp3.

---

### Post by Xbehave on 2010-04-24
> **JDShu said:**
> What is the advantage to Google though by opening up vp8? This is what has confused me.
1) All browsers implementing vp8
2) All websites using vp8 over flash/h.264/etc
3) a better web experience for most users
4) people spending more time on the web
5) profit

---

### Post by gnomeuser on 2010-04-25
> **loell said:**
> for the HTML5 Video plan domination. :D

The problem of gaining an open and redistributable best of breed video format is independent of the web platform wars. There is no reason why e.g. Silverlight might not also include support.

Regardless for this to make "html5 dominate", you'd still have to get Nokia, Apple and Microsoft to ship it. Not unlikely but certainly not likely either as each has their own horse to play on in this race or have problems with Google.

The things I believe matters for Google is long term standardization on an open format. This would increase the web as a platform and bring them more users. It is also a way to one day stop sucking on the MPEG-LA licensing tit for ffmpeg in Chrome.

Finally Google sets the standards for being able to call a device a certified Android or ChromeOS, they could make it a demand that you be able to decode 1080p VP8. Because with VP8 they got something infinitely more useful, namely working optimized hardware implementations. These they can license to people, while the VP8 codec is open implementing a hardware decoder is likely going to be to expensive compared to licensing a chip from Google.

The presence of a high quality codec available patent free with hardware decoders would remove a lot of complaints we saw with Theora. It isn't much different from what we have with Dirac (or Ogg Schrondinger) but with Google we are likely to see stronger leadership and a stronger push to get it to the market than we have seen with the BBC.

---

### Post by sdowney717 on 2010-04-25
[http://www.on2.com/index.php?599](http://www.on2.com/index.php?599)

full screen the video and you will see vp8 does look much better.

---

### Post by FakeOutdoorsman on 2010-04-26
> **sdowney717 said:**
> [http://www.on2.com/index.php?599](http://www.on2.com/index.php?599)

full screen the video and you will see vp8 does look much better.

Unconvincing.  How old is this comparison video?  If it is relatively recent, why would they use such an old x264 (r915)? x264 is currently at r1564.   Why don't they provide the source video and the x264 command so others can test this?  Also, I would like to see a third image in that [screenshot](http://www.on2.com/image.php?blob_id=539) showing how both encoded images compare to the original frame.

Assuming that input was "clean" I don't know how they got x264 to create such a bad output.  Bad settings can make any decent encoder look awful.

---

