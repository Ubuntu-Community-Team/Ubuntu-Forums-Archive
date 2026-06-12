---
title: "Remux MKV to MP4 with AAC on Ubuntu"
date: 2018-10-27
forum: Ubuntu, Linux and OS Chat
---

### Post by mallinea on 2018-10-27
Hello there.


I    recently started my own dedicated ubuntu server and its a mouthful to    be honest. Especially if you all your life has been used to windows.
Im    moving my whole movie collection to the server. Its a movie folder   with  hundreds of subfolders where the movie files are stored.


I    would like to create a script that can search through all the    subfolders and remux the video file and then make a new folder in a   specific location and copy the file to that folder.
I    have found lots of scripts that can do the directory Im in but that    would mean I would have to swap to the next folder a hundred times..  Any   experts who can lend a hand? :)


How would this script work with a few changes?


```
mkdir output   
for f in *.mkv;do ffmpeg -i "$f" -c:v copy -c:a aac "output/${f%mkv}mp4";done  


```

---

### Post by TheFu on 2018-10-28
There are 500 ways to skin this problem.  Coming from Windows, your solution might not be the best option. If you can show a before directory and an after directory, perhaps someone could help?

A few thoughts ... 
If you setup a Plex server, then the streamed media will be transcoded as needed for the client. You won't lose the extra audio, SRT or sub tracks this way.  

I would do the conversions in the same directory as the source files myself.  Later, you can use find and clean up and old files you don't want anymore.

There are hundreds of text processing commands on Unix systems. basename, dirname and sed or awk should be enough.  If you want to stay inside a single language, I'd suggest staying with one like perl, ruby, or python. If you don't know any of those, there are many, many, awk examples around the internet.

Personally, I wouldn't change from the most capable container (mkv) without some VERY, VERY, good reasons. I'd use **mkvinfo** to take a look at the different tracks in each file, then decide, programmatic how to proceed.  Using a script to make another script is a common solution.  I use it all the time.

---

