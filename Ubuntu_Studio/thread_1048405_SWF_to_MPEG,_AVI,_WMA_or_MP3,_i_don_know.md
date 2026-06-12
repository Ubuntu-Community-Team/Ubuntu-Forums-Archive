---
title: "SWF to MPEG, AVI, WMA or MP3, i don know"
date: 2009-01-23
forum: Ubuntu Studio
---

### Post by federey on 2009-01-23
i´m trying to compile a track, is the backgroung track of a main web page, i have downloaded the page with HTTrack and i´ve got a .swf file, i have downloaded swftools and try to convert it to AVI or other format, do i have to keep the original format, the thing is that that i got the hole page made on a shokwave format, and the soung in macromedia when i extract i dont know the format or how to complile succesfully
first of all i got to run swfextract file.swf to get the decription of all the files
i get something like this

root@federey-desktop:~/path# swfextract file.swf
Objects in file file.swf:
 [-i] 18 Shapes: ID(s) 1, 5, 6, 8, 9, 14, 15, 27, 38, 46, 54, 66, 92, 94, 100, 103-105
 [-i] 14 MovieClips: ID(s) 7, 10, 18, 19, 39, 40, 44, 45, 47, 60, 65, 95, 96, 107
 [-j] 3 JPEGs: ID(s) 2-4
 [-p] 2 PNGs: ID(s) 52, 53
 [-f] 1 Frame: ID(s) 0

wich one are the souds ID´s, the Shapes or the Moviefiles, both of them?, how can i complie this so i can listen to the song on mi PC?

i have successfully made a flv file from the swf! but cant listen to it

i cant make edit.py work so i´m using swftools is there a problem with that

---

### Post by sgx on 2009-06-21
Hi, I use this command to make mp3 from flv, you need ffmpeg and avi related apps, misc codecs installed

ffmpeg -i my.flv -ar 44100 -ab 320k -ac 2 my.mp3

This assumes the flv is in your /home/user folder, and you want the new mp3 there also

Cheers

---

