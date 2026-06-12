---
title: "Convert from rmvb to avi."
date: 2009-02-11
forum: Ubuntu Studio
---

### Post by Bigneil on 2009-02-11
How to convert rmvb to avi.  ?  i have 4 series of a classic sci-fi show backed up on data dvd disk.  they were originally encoded from dvd using realplayer (.rmvb)  i would like to convert them to avi's to watch on my telly.

I tried avidemux, i also tried acidrip. 

can anybody help

---

### Post by howefield on 2009-02-11
Can't help other than give you a link

[http://coolans.blogspot.com/2008/05/how-to-convert-rmvb-to-avi.html](http://coolans.blogspot.com/2008/05/how-to-convert-rmvb-to-avi.html)

---

### Post by Bigneil on 2009-02-11
Thanks for replying.

This looks like it could help me, but i have to read it a couple of times before i will understand it.

thanks :)

---

### Post by Bigneil on 2009-02-11
mencoder in.rmvb -oac mp3lame -lameopts preset=128 -ovc lavc -lavcopts vcodec=mpeg4:vbitrate=1200 -ofps 25 -of avi -o out.avi


in the command above, 'in.rmvb' i assume that i need to substitute the full name of the file i want to convert. but also how would i indicate that the file is to be retrieved from my dvd drive?

/dev/dvd1

?

---

### Post by howefield on 2009-02-11
Navigate to the folder that contains the file and run the command from that folder ? eg, 

cd /dev/dvd1

---

### Post by Bigneil on 2009-02-11
thans again:P

---

