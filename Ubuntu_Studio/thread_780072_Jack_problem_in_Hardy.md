---
title: "Jack problem in Hardy"
date: 2008-05-03
forum: Ubuntu Studio
---

### Post by Elphizo on 2008-05-03
Hi all! I'm having a lot of problems with jack. Under Gutsy I had a lot of trouble starting the application, but after some experiments it worked fine and i was able to use Ardour.
I recently upgraded to Hardy, always with Ubuntustudio, and jack starts without any problem, but the audio quality is horrible. With ardour the quality is horrible even if I try to play the files recorded under Gutsy. I tried to change some options, but the only thing that change the quality is the Frames/Period option: it is on 1024, if i try less the things get worse, if i try a higher value jack simply doesn't start. 
Could someone help me, please?

Thanks for reading!

EDIT: I found out that my jack tray icon turns red every time. I read that that is an XRUN signal, and if it occurs I have to try to disable realtime and increase the Frames/Period value, but, as I said before, I can't go over 1024...

---

### Post by luctor on 2008-05-03
[LIST=1]
[*]Could you post the output of grep audio /etc/security/limits.conf 
Here's mine
```
grep audio /etc/security/limits.conf 
@audio          -       memlock         250000
@audio          -       nice            -10
@audio 		- 	rtprio 		99
```
[*]Have you got the realtime kernel (linux-rt) installed ?
[/LIST]

---

### Post by Elphizo on 2008-05-03
This is my output:
```
@audio          -       rtprio          99
@audio - rtprio 99
@audio - memlock 250000
@audio - nice -10

```
and yes, i have the real time kernel, which is auto installed with ubuntustudio.
Anyway, I don't know why but now it works correctly. I was trying some settings and the sound disappeared totally. After a reboot, with the same settings as before(realtime on, frames/period:128,sample rate: 48000), jack worked properly.
Thanks for the help!

---

