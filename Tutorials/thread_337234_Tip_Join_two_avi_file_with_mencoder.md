---
title: "Tip: Join two avi file with mencoder"
date: 2007-01-12
forum: Tutorials
---

### Post by kd7swh on 2007-01-12
Joining two or more avi files is easy with mencoder.

Here is a simple script that I use to do it:

```
# MjAVI - 2007
#Mencoder needs to be installed for this script to work
#The Numbers in this script could be changed to combine more than two files.
# Mencoder also supports mpeg files. So the .avi could also be changed to .mpg


echo "Script to combine two avi files, while syncing audio."
echo "usage: ./mjavi a1.avi a2.avi combined_temp.avi final.avi" 

cat "$1" "$2" > "$3";
mencoder -forceidx -oac copy -ovc copy "$3" -o "$4"


```

the cat command combines 1 and 2 into 3, but the audio isn't in sync. So, 3 is indexed with mencoder into 4 which has nicely synced audio. :)

---

### Post by neilp85 on 2007-02-06
There's no reason to cat the two files together before encoding because mencoder can handle that as well.
```
mencoder -forceidx -ovc copy -oac copy -o file.avi p1.avi p2.avi ... 
```

---

### Post by LucasLinard on 2007-02-11
> **neilp85 said:**
> There's no reason to cat the two files together before encoding because mencoder can handle that as well.
```
mencoder -forceidx -ovc copy -oac copy -o file.avi p1.avi p2.avi ... 
```

When I try to join 2 mpeg files, how can I make the oputput a mpg file?
If I try -of mpeg I get a lot of errores like this one:
ERROR: scr 6715.707, dts 0.000, pts 6714.866

ERROR: scr 6715.752, dts 0.000, pts 6714.962

ERROR: scr 6715.794, dts 0.000, pts 6715.058

ERROR: scr 6715.837, dts 0.000, pts 6715.122

ERROR: scr 6715.885, dts 0.000, pts 6715.218

ERROR: scr 6715.925, dts 6715.283, pts 6715.408

ERROR: scr 6715.927, dts 0.000, pts 6715.282

ERROR: scr 6715.979, dts 0.000, pts 6715.378

ERROR: scr 6716.025, dts 0.000, pts 6715.474

ERROR: scr 6716.066, dts 0.000, pts 6715.538

ERROR: scr 6716.090, dts 6715.575, pts 6715.700
Pos:6716.1s 161028f (88%) 473.28fps Trem:   0min 2904mb  A-V:0.066 [2976:192]
ERROR: scr 6716.162, dts 0.000, pts 6715.634

ERROR: scr 6716.210, dts 0.000, pts 6715.730

ERROR: scr 6716.254, dts 0.000, pts 6715.794

ERROR: scr 6716.302, dts 0.000, pts 6715.890

ERROR: scr 6716.358, dts 0.000, pts 6715.954

ERROR: scr 6716.369, dts 6716.034, pts 6716.159

ERROR: scr 6716.371, dts 0.000, pts 6716.050

ERROR: scr 6716.406, dts 0.000, pts 6716.146

ERROR: scr 6716.441, dts 0.000, pts 6716.210

ERROR: scr 6716.485, dts 0.000, pts 6716.306

ERROR: scr 6716.511, dts 6716.326, pts 6716.451
Pos:6716.9s 161046f (88%) 473.30fps Trem:   0min 2904mb  A-V:0.055 [2976:192]

---

### Post by DerArzt on 2007-02-21
Cheers neilp85. Worked PERFECTLY.

---

### Post by tzulberti on 2007-02-22
Thanks for the tip

---

### Post by z987k on 2007-03-15
> **LucasLinard said:**
> When I try to join 2 mpeg files, how can I make the oputput a mpg file?
If I try -of mpeg I get a lot of errores like this one:
ERROR: scr 6715.707, dts 0.000, pts 6714.866

ERROR: scr 6715.752, dts 0.000, pts 6714.962

ERROR: scr 6715.794, dts 0.000, pts 6715.058

ERROR: scr 6715.837, dts 0.000, pts 6715.122

ERROR: scr 6715.885, dts 0.000, pts 6715.218

ERROR: scr 6715.925, dts 6715.283, pts 6715.408

ERROR: scr 6715.927, dts 0.000, pts 6715.282

ERROR: scr 6715.979, dts 0.000, pts 6715.378

ERROR: scr 6716.025, dts 0.000, pts 6715.474

ERROR: scr 6716.066, dts 0.000, pts 6715.538

ERROR: scr 6716.090, dts 6715.575, pts 6715.700
Pos:6716.1s 161028f (88%) 473.28fps Trem:   0min 2904mb  A-V:0.066 [2976:192]
ERROR: scr 6716.162, dts 0.000, pts 6715.634

ERROR: scr 6716.210, dts 0.000, pts 6715.730

ERROR: scr 6716.254, dts 0.000, pts 6715.794

ERROR: scr 6716.302, dts 0.000, pts 6715.890

ERROR: scr 6716.358, dts 0.000, pts 6715.954

ERROR: scr 6716.369, dts 6716.034, pts 6716.159

ERROR: scr 6716.371, dts 0.000, pts 6716.050

ERROR: scr 6716.406, dts 0.000, pts 6716.146

ERROR: scr 6716.441, dts 0.000, pts 6716.210

ERROR: scr 6716.485, dts 0.000, pts 6716.306

ERROR: scr 6716.511, dts 6716.326, pts 6716.451
Pos:6716.9s 161046f (88%) 473.30fps Trem:   0min 2904mb  A-V:0.055 [2976:192]

[http://www.mplayerhq.hu/DOCS/HTML/en/menc-feat-mpeg.html](http://www.mplayerhq.hu/DOCS/HTML/en/menc-feat-mpeg.html)

Also if you have two mpg's of the same format, couldn't you just "cat 1 2 > 3"?

---

### Post by kd7swh on 2007-11-16
if you just use cat, its my understanding that the index would not be preserved. this process creates a working index.

---

### Post by yabbadabbadont on 2007-11-16
How about just using avimerge which is included with transcode?  ;)

Edit: Wow!  Holy Thread Resurrection Batman!  :D

---

### Post by kd7swh on 2007-11-16
I created this thread almost a year ago, a lot has changed since then.

---

### Post by lad3391 on 2008-12-03
i just found it, and it works great for me. i guess my only suggestion to ppl reading this would be to type in 'cd ~/Desktop' into terminal (if thats where your files are at), no ' symbols, just the stuff between. type that before you do the mencoder command line

---

### Post by tdreyer1 on 2008-12-11
> **neilp85 said:**
> 
```
mencoder -forceidx -ovc copy -oac copy -o file.avi p1.avi p2.avi ... 
```

Awesome! That worked great! :mrgreen:

---

### Post by deadtom on 2009-01-20
Worked great for me too. Thanks for the info!

---

### Post by Lylex11 on 2009-06-14
Thanks neilp85! works a treat and real quick. Saves encoding all the files again!

---

### Post by HarshReality on 2009-10-10
I'd love it if there was a right click option to just run this (mencoder script).. would save alot of typing.

---

### Post by yunone on 2009-10-25
> **lad3391 said:**
> i just found it, and it works great for me. i guess my only suggestion to ppl reading this would be to type in 'cd ~/Desktop' into terminal (if thats where your files are at), no ' symbols, just the stuff between. type that before you do the mencoder command line


thank you very much for the simple tip about the file location...worked perfectly....Great little tip !

---

### Post by kvarley on 2010-02-06
> **neilp85 said:**
> There's no reason to cat the two files together before encoding because mencoder can handle that as well.
```
mencoder -forceidx -ovc copy -oac copy -o file.avi p1.avi p2.avi ... 
```
Thank you so much! Nice bit of code which has been much use to me. :P

---

### Post by mister_playboy on 2011-01-23
> **neilp85 said:**
> There's no reason to cat the two files together before encoding because mencoder can handle that as well.
```
mencoder -forceidx -ovc copy -oac copy -o file.avi p1.avi p2.avi ... 
```

Just what I was looking for... thank you. :KS

---

### Post by vedavrata on 2013-01-25
> **neilp85 said:**
>   **mencoder** can handle that as well.
```
mencoder -forceidx -ovc copy -oac copy -o file.avi p1.avi p2.avi ... 
``` Thank you! 
It works! [and much better than by ffmpeg! :)]

---

### Post by andrew.46 on 2013-01-27
> **vedavrata said:**
>  It works! [and much better than by ffmpeg! :)]

Good to see that you have achieved the desired outcome but have a look at a modern copy of FFmpeg and you might find that there have been some considerable improvements in video concatenation just recently.

---

