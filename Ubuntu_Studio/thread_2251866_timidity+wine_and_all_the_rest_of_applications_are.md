---
title: "timidity+wine and all the rest of applications are soundless"
date: 2014-11-07
forum: Ubuntu Studio
---

### Post by kbanelas on 2014-11-07
Hello to everybody!!


I have a problem when I use timidity on wine. For example, I'm using Band in a box and works fine with timidity.
But, however all the rest of applications while Band in a Box is running, are soundless either don't work. For example I cannot play any video on youtube. Directly youtube doesn't work.


Any ideas?

Thanks and regards

---

### Post by jejeman on 2014-11-07
Is JACK active?

---

### Post by kbanelas on 2014-11-07
Hello jejeman!!

Thanks for your support.
No it isn't. But if I connect it, it isn't necessary open Band in a Box, for example youtube doesn't work.


Please, ask me more info, because I don't know, in this case,  what is necessary for you can help me.


I realize that it's possibly, it's about a conflict between pulseaudio and alsa.
But I don't obviously know how fix it.


Thanks again


Cheers!!

---

### Post by kbanelas on 2014-11-08
Hello!!


It was about the timidity daemon. I don't know why but it seems. that this daemon don't work fine, at least for me.


I'm sure that there are a lot of solutions for this problem.


I did what follow:


1st Remove all timidity rundevels, that is, remove in /etc/rdX.d/ (where X is a number between 0 and 6) all links related with timidity. For example:


```
sudo rm /etc/rd0.d/K01timidity

```

Similar way with all rundevels. So timidity daemon will not start.


2nd Create into Settings -> Session and Startup -> Automatically starting applications
a new  item, for example push Add and write: Name: Timidity Startup (for example); Desciption: Startup of Timidity (you write what you want); and finally command, here write: 

```
/usr/bin/timidity -iA -B2,8 -Os
```


Then when you turn on your computer timidity works fine, and you will be able to run all applications at the same time.

Cheers!!

---

