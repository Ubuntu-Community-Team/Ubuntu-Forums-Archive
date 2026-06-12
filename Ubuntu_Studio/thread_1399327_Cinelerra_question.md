---
title: "Cinelerra question"
date: 2010-02-05
forum: Ubuntu Studio
---

### Post by LuridCinema on 2010-02-05
In having an issue w/ cinelerra. Im woring w/ an HDV file 1440x1080. I set the Settings>Format to the correct size and the aspect to 16:9 and after rendering, it comes out as 4:3 aspect. I know it has to do with pixel dimensions somewhere, How do I change this inside Cinelerra to get 16:9 output when rendering ?

---

### Post by cooper77z on 2010-02-06
You might want to try the method described on this page [http://crazedmuleproductions.blogspot.com/2007/06/beginners-guide-to-exporting-video-from.html](http://crazedmuleproductions.blogspot.com/2007/06/beginners-guide-to-exporting-video-from.html)

It looks like the best rendering you are going to get is 
HDV720P      MPEG2               YUV4MPEG          MPEG, Layer II (384Kbps)

The audio and video need to be rendered separately and then muxed togeter.

good luck :) Alternatively, you could ask on cinelerra chat on freenode.

---

### Post by LuridCinema on 2010-02-06
Thanxxx that did it.. still renders at 4:3 if I do .mov but under mpeg2 it renders @ 16:9

---

### Post by cooper77z on 2010-02-06
I am glad that worked for you. Were you able to render at the full resolution or did you have to step down to 720p? If I understand containers correctly, a .mov can contain an mpeg codec. . mov is just a container right?

---

### Post by LuridCinema on 2010-02-06
I was rendering as a .mov and it was coming out 4:3..I rendered out as MPEG2 and it came out 16:9. I will then use ffmpeg to make 2 resolutions 1280x720 and then 640x360 for the web

---

### Post by cooper77z on 2010-02-06
Interesting, because when I use ffmpeg to convert my MP4's to mjpeg the result is a .mov extension/container. So, when you bump up after rendering is the image more defined?

---

### Post by LuridCinema on 2010-02-06
I have some 1440x1080i m2t files, Im dropping them into cinelerra, editing and rendering now as YUV4mpeg stream and saving w/ m2t extension, the mpeg2 pipe per the page you linked ( using the file for possible DVD use later )and rendering audio. I then am using ffmpeg and going 1280x720 w/ h.264 mp4 and another pass for 640x360 h.264 mp4


```
ffmpeg -i ravi264444.ac3 -i ravi264444.m2t -acodec libfaac -ac 2 -ab 128k -vcodec libx264 -vpre hq -wpredp 0 -s 1280x720 -crf 24 -threads 0 ravi1280.mp4

```

---

### Post by cooper77z on 2010-02-06
That's over my head, maybe I'll think about it for a while.

---

### Post by LuridCinema on 2010-02-06
Hey it's over my head too.. Im kind of out in the woods, but it looks good ;)

---

### Post by Frak on 2010-02-07
> **cooper77z said:**
> I know what you mean because when I transform the MP4 into mjpeg, the copy/transfer LOOKS better than the original. Wierd/Where_Was_The_Extra-Info_Hiding ?

I thought m2t files was a rf trunking protocol. I don't even know what that means in terms of a production. What the hell is m2t?

You are talking about maybe broadcasting on the airwaves your productions on rf radio frequency, right? It's important to be able to broadcast rf and internet stuff, I think that's why Cinelerra is such a bi$tc* when it comes to rendering :( :) Cinelerra is such a_+_+_ because she intends to broadcast your productions. That's why. :)) [_+_+_=HCTIB] Cinellera is a chum.

O, so, if ou inasd ad jite dosa asd;lkfj;as;  dkdk code dkslla

Yea right, sounds like bs, it is. How much does final cut pro cost? Double that, because if you were to pay cash money for Cinelerra, that's how much you would have to pay :)

I sware, people talk about limitations of money. Is there something you wanted to create, that technology failed to maike real, and if you used cinelerra then you never had an real man editing for you idea.. l .. ... . . l

It's really ridicoulous, I am mostly jokihg with you all. Cinwlerrwdjsa is the perksecect editing program. Maybe aosodifIWONTgiveITaaaaaalll awwar away for free how foogodogohofoodoogood cinelerra is...

anti editing is fun for us without intelligence requirements...}

if your iq is 90-110 don't even try

if 125 to 140 use bullet weapons

if + 125-190 op please help me understand how to kill and save ::: HOW TO SAVE LIFE

tHE CHIHUAHUA IS HIDING... HIDING  THE CHIHUAHUA sHE MAKES ME LOOK PREGNANT... ... Dog god dog me loves me dog :) I dare you d=t to be better than me chihuahua,  i dare  you. l. ..  laugh out t lous loud laugh out loud, ...

==ot D  s sorry I mean a p = b minus all the bullshj

final conversion = a gppd vamo;;a ,o; sjale/ lll vanilla milkshake wiht with wiii half and half milkshake :) :)

it was a vanilla milkshake, and if you interfere with my desert, then you are OVER just kikkine kidding kikking... you my enemy,. ,. ,. that is funny i will kill you my ememy you arwe aew arw are deas yea you lll kkk nO NO i AM NOT K LIKE L= THAT GO ON AND LIVE YOU NIGGGGG HUMAN

> **cooper77z said:**
> ok, I wil ll  go easy on you, if you want ro to use a real editing app like cinelerra,

Complain at first, cause yo you don't know hoe how to edit/

then wonder

then make it real, you know a real program edited from faulyty faylty faulty cinelerra coe3 ci code,,, ...

> **cooper77z said:**
> honestly, I am older trh thans sh shi shi* older than shot. and ho you hor can not ef ege ece v evan woe eo work a re a ho fh worka a real ho p p aoi io or d:popcorn:

wut

---

### Post by wetinwales on 2010-02-20
Lurid Cinema
It shows you are using Karmic 9.10 and perhaps on a 64bit ?
Which of the various Cinelerras are you using?
I heard of a 4.1 CV but cannot find it.
I still can not find any version which works in practise - must be me!

D

---

### Post by LuridCinema on 2010-02-20
Im using 32bit and yes 9.10.. there ia another version called Cinecutie that also installed on my machine. It has a somewhat different GUI. Mebbe that will work

---

