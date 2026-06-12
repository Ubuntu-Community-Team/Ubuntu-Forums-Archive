---
title: "A GStreamer error has occured in Jokosher"
date: 2010-01-04
forum: Ubuntu Studio
---

### Post by Oasu4g on 2010-01-04
Hi,

Every time I try to record something in Jokosher I get this error message: "The stream is in the wrong format.
gstbasesrc.c(2522): gst_base_src_start (): /GstPipeline:timeline/GstBin:playbackbin/GstBin:Click_Track_Bin/GstAudioTestSrc:Click_Track_AudioSource:
Check your filtered caps, if any"

I'm using Linux Mint 7 Standard. I'm trying to set Jokosher up to work with Jack. Can anyone point me in a general direction toward getting this resolved? I'm really lost on this one.

Thanks,

Tim

---

### Post by nasreen888 on 2010-01-07
When I'm try playback the track record somethings wrong with the jokosher. it says "GStreamer encountered a general resource error. If this problem persists consider reporting a bug using the link in the help menu." 

I try jokosher with my Ubuntu 9.10 Karmic Koala. Has anyone know to solve this problem
______________________________________________
[CMH Bulbs](http://www.growlightexpress.com/ceramic-metal-halide-bulbs-9/)
[wall décor for girls room](http://artcreations.com/eShop/products.asp?mcid=11&mctgy=Baby%27s+Room&scid=59&sctgy=Girls+Room)

---

### Post by aimpau on 2010-01-07
same problem here.

---

### Post by Oasu4g on 2010-01-12
Really? Nobody knows?

---

### Post by Oasu4g on 2010-02-06
Check this bug if you have playback problems; make sure to add yourself as an affected person if it applies:

[https://bugs.launchpad.net/jokosher/+bug/405056](https://bugs.launchpad.net/jokosher/+bug/405056)

Consider joining #jokosher on irc.freenode.net if you want more help. Post any results here please. :)

Thanks,

Tim

---

### Post by abdoamcig on 2010-02-07
i have the same problem and i have search in multi forums, no one have any idea about this, i have back to the bugs, also no answer, i think now the program is under developing as i read in many replies in many froums ...

..

any body tell us any more new news ..

Regards to all,
Abdulatif Mahgoub

---

### Post by phil_bell on 2011-03-26
I received the same gstreamer error. I noticed that ALSA was not an option in the playback or recording sound system preferences, yet my computer uses the ALSA sound system. I know that gstreamer has many plugins for compatibility with different sound systems and that gstreamer0.10-alsa was not installed on my computer. I installed gstreamer0.10-alsa and now audio works in Jokosher. I hope this helps.

By the way, I'm running Kubuntu 10.10.

---

### Post by zettberlin on 2011-03-27
Some 12 months ago the project announced, that Jokosher works with Jack. Since Jack is the gold-standard for musicians under Linux whatsoever, this should have solved all basic problems as those discussed here.

12 months...

I warmly recommend to have a close look upon Ardour -- you will find that its "overwhelming complicity" is a myth.

---

### Post by kamhh_94 on 2011-05-04
if you record something and you cant hear it (like in my case) then do the following:

1.open jokosher
2.go to edit
3.click preferences
4.under 'playback sound system' pick Autodetect'

that should detect ur playback driver and play it automatically

it worked for me,hope it works for you too :popcorn:

---

### Post by defis on 2011-05-21
Well, same problem. And as I can see it will not go away, since none seems to care any more... too bad because I think it worked like a charm in previous versions (I run 11.04) and I don't want to hear all the time "...yes but linux doesn't have the programs mac do..."


Found a way to somehow pass this error. Set your recording system at custom and then you can rec any instrument you want. BUT be careful if you want to rec again DO NOT rec upon your first recordings or Jokosher will crash. Delete the previous recs or move them.

---

### Post by geek373 on 2011-07-14
FIRST POST EVER! Hope it works for you.

1. Go to Edit > Preferences
2. Under "Recording Format" change "Encoding" to "WAV (.wav)"

That did it for me! Hope it works for you too...

---

### Post by stefan.hattrell on 2011-08-19
Thanks geek373! That did it for me too. Shame for people who might want to use flac to encode...

---

### Post by y2b4u3d on 2012-06-12
OMG! Thanks a lot @[geek373]("http://ubuntuforums.org/member.php?u=1347430") that help me!
as you said @[stefan.hattrell]("http://ubuntuforums.org/member.php?u=402798") shame on them Jokosher team to make flac as default sitting :(

---

### Post by yanike on 2013-04-09
@[geek373]("http://ubuntuforums.org/member.php?u=1347430") THANK YOU! Now I can try Linux recording :)

---

### Post by wildmanne39 on 2013-04-17
Thread closed. Please do not post in old threads.

---

