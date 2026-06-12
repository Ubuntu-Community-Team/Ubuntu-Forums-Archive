---
title: "Audacity Problems"
date: 2009-04-04
forum: Ubuntu Studio
---

### Post by higashi on 2009-04-04
Hello.

I recently got more into multimedia production. I am learning to use lmms, and i am planning on using audacity (which i already know how to use)  to add vocals.

The problem is that audacity doesn't seem to be working. it refuses to play anything (i haven't even tried recording yet...)

I've been looking for solutions for this for quite a while. I found one tutorial that said to switch to pulseaudio. I did every step in the tutorial and it worked... for a while. I tried to change the playback settings to pulseaudio, so far so good. Everything worked! the audio was playing and everything. However. After pressing stop (or closing and re-opening audacity.. i dont remember) the audio wasn't working again!

So, i went back to see if it switched back to also, so that i can switch back to puleaudio. It actually had switched back to alsa. No big deal, just switch back, right? Wrong. I tried to select pulseaudio again, but all the playback options had disappeared! Everything was back to how it was in the first place. Alsa was my only option there, and i didn't want to re-do the entire tutorial just to go through that one more time.

Can anyone tell me how i can effectively get playback/recording to work properly in audacity?
Pleeeeeease?

---

### Post by B4RR13N705 on 2009-04-04
If you want to add voclas and record stuff, audacity is good but not professional. I seggest you to try Ardour, it has a perfect quality and its easy to use. I have a studio working along with ardour. If you really want to make good stuff, use Ardour. You can download it from the repositories:
```

$ sudo apt-get install ardour

```
Bye! ):P

---

### Post by higashi on 2009-04-04
Thanks :]

I already have ardour, but still want to get audacity working because i enjoy playing around and expirementing with audio files in my spare time (and audacity is my program of choice for this).

So.. i still want to get it to work. x]

---

### Post by babarosa on 2009-04-04
higashi,

at [www.getdeb.net](www.getdeb.net) you get the most recent versions of ardour and audacity.

To set up your system for recording audio, you have to
[LIST]
[*]install a RT-kernel (Hale Heron works better than Infelicious Ibex)
[*]install jack and qjackctl and adjust some files so jack/qjackctl work properly
[*]use a "professional" soundcard (the built in ones in computers are not fitting for more advanced needs)
[/LIST]

This forum is full of threads dealing with these topics, use the search function ;)

Regards, Michael

---

### Post by higashi on 2009-04-04
i have searched for threads many times for this, and haven't been able to solve my problem.

Recording isn't really an issue for me right now.. i first need to get the playback working.

I got the newest version from getdeb.net  , thinking that maybe this bug was fixed, but i'm getting the same problem.

---

### Post by B4RR13N705 on 2009-04-05
I had a problem with audacity a long time ago. The playback didnt function as you say. I solved it running JACK CONTROL as a guy on the forum told me.

---

### Post by markbuntu on 2009-04-05
Go here, it will fix almost any problem you have with sound in Ubuntu.

[http://ubuntuforums.org/showthread.php?t=843012](http://ubuntuforums.org/showthread.php?t=843012)

---

