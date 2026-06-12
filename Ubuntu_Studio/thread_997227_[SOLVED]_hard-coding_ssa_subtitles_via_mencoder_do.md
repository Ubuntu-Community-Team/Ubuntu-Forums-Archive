---
title: "[SOLVED] hard-coding ssa subtitles via mencoder doesn't work at all"
date: 2008-11-29
forum: Ubuntu Studio
---

### Post by HungryMan on 2008-11-29
I've searched google and the forums for an answer, i've tried avidemux and mencoder, but both fail miserably.

My goal is to hard-code subtitles and an avi file into a vcd-compliant mpg

avidemux was able to hard-code the subtitles, but will refuse to encode the sound. no matter what configuration I put in the audio, during encoding, video codec says "mpeg2", but audio codec says "none". one more thing is that avidemux takes twice as long as mencoder.

mencoder did not seem to do anything except convert mpg to avi. the sound was there and it was ,contrary to what I expected, synced.

here is my mencoder options:
```
$ mencoder -oac lavc -ovc lavc -of mpeg -mpegopts format=xvcd -vf scale=352:288,harddup -sub sub.ssa -srate 44100 -af lavcresample=44100 -lavcopts vcodec=mpeg1video:keyint=15:vrc_buf_size=327:vrc_minrate=1152:vbitrate=1152:vrc_maxrate=1152:acodec=mp2:abitrate=224 -ofps 25 -endpos 2:00 -o out.mpg in.avi
```

I'd appreciate if someone could shed some light on my situation. Or tell me that mencoder can't encode ssa. I don't mind using either, just tell me how to make ssa work on mencoder or sound on avidemux.

---

### Post by nowardev on 2008-11-30
mmm i know mencoder uses, in the most of cases well, srt files 

i suggest to create srt file. that works for me 

to edit srt file you can always use a normale text editor like gedit or kate for kubuntu

---

### Post by HungryMan on 2008-11-30
thanks for the help!
how can I convert ssa subtitles into srt?

---

### Post by nowardev on 2008-11-30
google says

[http://www.akira.ru/osc/ssa2srt.php](http://www.akira.ru/osc/ssa2srt.php)

---

### Post by HungryMan on 2008-11-30
Through some bizarre twist, the stand-alone dvd player recognizes .ssa subtitles, but it renders only one line at a time.

Thanks for the link! I'll try encoding subtitles with srt later, I have some important matters to do first.

---

### Post by HungryMan on 2008-12-04
I know what's the problem already.

```
New_Face failed. Maybe the font path is wrong.
Please supply the text font file (~/.mplayer/subfont.ttf).
subtitle font: load_sub_face failed.

```

I did not see this because mencoder flooded the terminal with status messages before. I only saw this when I converted less verbosely.

---

