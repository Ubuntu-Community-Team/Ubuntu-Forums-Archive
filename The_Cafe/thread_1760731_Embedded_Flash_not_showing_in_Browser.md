---
title: "Embedded Flash not showing in Browser"
date: 2011-05-17
forum: The Cafe
---

### Post by Athos1234 on 2011-05-17
I'm using Ubuntu 10.10 and building my web-site using Apache, MSql + php.
my problem is that i can play .flv on my web browser when i go to sites (youtube or any
other flash video streaming site) but when i embed a file from my folder they do not play.
The file loads but it the area it should be stays black and if you right ckick it the usual flash menu appears not the one that says 'video not loaded'    can anybody help or have had the same problem.

The code I'm using is

<object classid="clsid:D27CDB6E-AE6D-11cf-96B8-444553540000"
codebase="http://download.macromedia.com/pub/shockwave/cabs/flash/swflash.cab#version=9,0,16,0"
width="320" height="400" >
<param name="movie" value="MinimaFlatCustomColorPlayBackSeekCounterVolMuteFull.swf">
<param name="quality" value="high">
<param name="play" value="true">
<param name="LOOP" value="false">
<embed src="Myfile.flv" width="320" height="400" play="true" loop="false" quality="high" pluginspage="http://www.macromedia.com/go/getflashplayer"
type="application/x-shockwave-flash">
</embed>
</object> <object width="370" height="277">

I Need Help I'm Getting Nowhere   ](*,)

---

### Post by Athos1234 on 2011-05-17
By the way The file name is Myfile.swf  not .flv + it works ok when i tried on a windows system (dose it have to be streamed to ubuntu?:confused:?) i'm trying yo convert totally to Ubuntu but i have to do my development on it so i need all these things to work.:KS

---

### Post by Fedz on 2011-05-17
From what I can see the:
<param name="movie" value="MinimaFlatCustomColorPlayBackSeekCounterVol MuteFull.swf">
and
<embed src="Myfile.flv"
have to be the same file.

---

### Post by Athos1234 on 2011-05-17
Thanks Fedz  :smile:
I'v had them both with the same file name but the same thing happens. The first file name(The long one) just puts my own control panel at the bottom of the video. and work ok on windows;    I'm using firefox on both the Windows and Ubuntu machines

---

### Post by Fedz on 2011-05-17
The problem playing them locally is you might have to use absolute path (/home/USERNAME/file.swf) & not relative (file.swf)

Do you have the html or php file in the same folder as the .swf file?

Personally I'd put the .swf paths to the actual url you've uploaded it too (if any)

---

### Post by Athos1234 on 2011-05-21
Thanx [Fedz]("http://ubuntuforums.org/member.php?u=152570") 

Changed the file path and all is working:D

---

### Post by Fedz on 2011-05-21
> **Athos1234 said:**
> Thanx [Fedz]("http://ubuntuforums.org/member.php?u=152570") 

Changed the file path and all is working:D
Result! & thank-you :)

---

