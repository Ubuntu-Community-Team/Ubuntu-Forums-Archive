---
title: "Converting ogv/ogg to wmv"
date: 2009-03-18
forum: Ubuntu Studio
---

### Post by DBQ on 2009-03-18
Hi, does anybody know how to convert an ogv or ogg file to wmv file on intrepid?  My source file contains a video. Thank You!

---

### Post by lovinglinux on 2009-03-19
Please tell me why do you need wmv? There are better options, unless wmv is a requirement. Then you can use [WinFF]("http://code.google.com/p/winff/")

---

### Post by DBQ on 2009-03-19
I tried using winff.  It works but the quality of the resulting video is not so good.  Are there any other ideas to make it better.  Basically using wmv is requirement.

---

### Post by ssdt on 2009-03-19
Why don't you convert it to avi, it runs with any other OS and the quality is great. For me I would prefer xvid or divx and now divx is easy to play with linux.

---

### Post by lovinglinux on 2009-03-19
> **DBQ said:**
> I tried using winff.  It works but the quality of the resulting video is not so good.  Are there any other ideas to make it better.  Basically using wmv is requirement.

Could you be more specific why wmv is a requirement? Maybe we can help with a better solution.

---

### Post by wubijacq on 2010-01-19
> **lovinglinux said:**
> Could you be more specific why wmv is a requirement? Maybe we can help with a better solution.  I have Wubi so i may use  Windows and Super((c)) is a good converter on Windows . wmv is very specific of microsoft . Super((c))  (freeware) can do it but not hight  quality  ...so we are on ubuntu forum !

---

### Post by trulan on 2010-01-19
I would still recommend using WinFF.  There are several .wmv presets (depending on your version) and some are better quality than others.  If you need high-quality, you'll want to create your own preset and specify your resolution, bitrate, etc.  But I can understand your complaints if you used the 'microsoft powerpoint' preset when you used winff - the quality on that is unbearably low.

I also use WinFF for making .wmv's, necessary for making a powerpoint presentation portable (and reliable) to other non-linux computers.  I've found that the wmv2 generic preset is acceptible for my needs, but your version of WinFF may not have that one.  But you can certainly increase the quality, it just takes a bit to learn how the presets work.  And the WinFF developer has his own forum.  If you need help getting your high-quality wmv preset made, ask over there:
[http://www.biggmatt.com/forums/](http://www.biggmatt.com/forums/)

Edit:  Whoops, old thread.  Oh well what I said is true anyway...

---

### Post by wubijacq on 2010-01-20
> **wubijacq said:**
>  I have Wubi so i may use Windows and Super((c)) is a good converter on Windows . wmv is very specific of microsoft((r)) . Super((c))  (freeware) can do it but not hight  quality it's better with other converts  CONVERTING IN TWO STEPS  first step : download ogg_flv_Converter_v1.1.tar.gz (free downloads  on my site [http://www.wubijacq.com/topic1](http://www.wubijacq.com/topic1)) you may extract it on your Ubuntu desktop . It is very simple run script (merci Jean-Claude great work)   you'll get  hight quality FLV files with this program , then second step go on the web to [http://www.Zamzar.com](http://www.Zamzar.com)  and convert inline your FLV file to WMV   (free if no more than 100Mb) very good result but it is a WMV1 file -  with I.E8 you need activeX to read the video   with Firefox that's OK !

---

### Post by AutoStatic on 2010-01-21
Cher wubijacq, j'ai l'idée que vous utilisez un logiciel ou un site pour traduire vos messages. De cette façon vos messages deviennent illisibles.

Hello wubijacq, I get the idea that you're using software or a website to translate your postings. Your messages become illegible that way.

---

### Post by wubijacq on 2010-01-21
> **AutoStatic said:**
> Cher wubijacq, j'ai dans l'idée que vous utilisez un logiciel ou un site pour traduire vos messages. De cette façon vos messages deviennent illisibles.

Hello wubijacq, I get the idea that you're using software or a website to translate your postings. Your messages become illegible that way.I've done some corrections ,  is that better ? Lucky you are when you know many languages . Ton français est très correct , merci AutoStatic de m'avoir prévenu . I did not speak english since a long time .

---

### Post by andrew.46 on 2010-01-22
Hi,

This thread is a little old but since a few people have contributed now I feel justified in putting my 3 cents worth in :).

A decent copy of FFmpeg can convert almost anything to a wmv file, and this file will play flawlessly on any windows system. A commandline such as the following will accomplish this:

```

ffmpeg -i input_file \
       -vcodec wmv2 -b 800k \
       -acodec wmav2 -ab 128k \
       -f asf output_file.asf

```

Both video and audio bitrates should be adjusted according to the properties of the input file of course, and an option to seriously consider is *-qscale 5* rather than *-b 800k*. To get a recent copy of FFmpeg Ubuntu users are very fortunate in having the following wildly successful guide:

HOWTO: Install and use the latest FFmpeg and x264
[http://ubuntuforums.org/showthread.php?t=786095](http://ubuntuforums.org/showthread.php?t=786095)

And just to jump in ahead of what is an obvious quesion: Why use the file extension .asf? The simple answer is that for the most part wmv files are actually contained within an asf container and the extension .asf accurately reflects this. However if you name the file .wmv there will be no difference in the file itself or the container as generated by FFmpeg. Some [details here]("http://en.wikipedia.org/wiki/Windows_Media_Video") including Microsoft's own recommendation for naming conventions.

Of interest as well are details of FFmpeg and Windows compatibility which can be seen here:

1.8 Which codecs are supported by Windows?
[http://ffmpeg.org/faq.html#SEC9](http://ffmpeg.org/faq.html#SEC9)

All the best,

Andrew

---

