---
title: "Converting"
date: 2009-03-10
forum: Ubuntu Studio
---

### Post by lil_kid1333 on 2009-03-10
Hi! I currently need help converting .flv to .mp4 for ipod.

I use avidemux for .avi to .mp4 and everything goes good but for some reason when I choose a .flv file it says it converts(btw the conversion takes like a second :s ) it but then when I use gtkpod to put the .mp4 file onto ipod, it says it can't recognise or it may not even be an .mp4 file :s

any help guys? any other way of converting? thanks

here is what gtkpod says

Could not open '/home/leo/Desktop/chencho/fl.mp4' for reading, or file is not an mp4 file.
The following track could not be processed (filetype is known but analysis failed): '/home/leo/Desktop/chencho/fl.mp4'

---

### Post by inobe on 2009-03-10
1) make sure you have all your updates.

2) make sure you have ubuntu restricted extra's, run this in terminal.

```
sudo apt-get install ubuntu-restricted-extras
```

3) make sure you have these' run this in terminal.

```
sudo aptitude install \
libavcodec-unstripped-51 \
libavdevice-unstripped-52 \
libavformat-unstripped-52 \
libavutil-unstripped-49 \
libpostproc-unstripped-51 \
libswscale-unstripped-0
```

check in synaptic package manager to see if you have **ffmpeg** installed.....

now that's done' we need to enable open terminal from nautilus file browser, you can right click in the directory where the video files are and open terminal, in terminal type

```
sudo apt-get install nautilus-gksu nautilus-open-terminal
```

"i would suggest either login out and back in' or a reboot at this point"

you will need all the cpu power you got for what we are about to do' and that will clear up some unneeded cache and services previously accessed ;)


open the directory where your flv, mpeg, avi or whatever

right click in that directory and select "open terminal"

in terminal type

```
ffmpeg -i "file name here without quotes".flv -vcodec libx264 -s 480x320 -r 24  -b 100k -acodec libfaac -ac 2 -ar 32000 -ab 128k -qscale 1 "file name here without quotes".mp4
```

that's a basic for i-phone, you can set the resolution accordingly' it's currently 480x320, the sound is 128k, video frame rate is 24, you can change libx264 to h264 if you wish...........

good luck

to learn more ffmpeg docs [http://ffmpeg.org/ffmpeg-doc.html#SEC5](http://ffmpeg.org/ffmpeg-doc.html#SEC5)

---

### Post by lil_kid1333 on 2009-03-10
O.o xD lol thank you very much but I somehow made it happened with avidemux, but imma try it your way cause I've always wanted to convert using the terminal xD it looks cool >_> =D thank you ^^

---

### Post by inobe on 2009-03-10
it wont hurt' actually it's kinda painless after you convert your first vid ;)

---

### Post by binbash on 2009-03-12
you may also want to check out handbrake which is very handy

---

### Post by inobe on 2009-03-12
there are a few apps with GUI that would probably do the same thing, the only difference between CLI and GUI is you can't really tweak the settings like you can in CLI.......


look at mme' that's also a great app' it does well with .flv

i don't really like it, one because you can see what's going on, two' the settings are limited to the design of the app, it does work.

---

### Post by michael37 on 2009-03-15
My favorite is WinFF which has Ipod presets.

Makes encoding of FLVs and AVIs into MP4s a breeze.

Look for Video Conversion section in the first post of [thread=766683]this super thread[/thread].

---

### Post by inobe on 2009-03-15
challenge of app

i still prefer CLI lol's but i don't mind helping decent folks

[tar.gz for other flavors]("http://www.miksoft.net/products/mmc-lin.tar.gz")

[ubuntu 1386 deb]("http://www.miksoft.net/products/mmc_1.4.1_i386.deb")

[the site]("http://www.miksoft.net/index.html")

---

