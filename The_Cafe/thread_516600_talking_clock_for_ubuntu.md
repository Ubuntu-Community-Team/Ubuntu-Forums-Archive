---
title: "talking clock for ubuntu?"
date: 2007-08-03
forum: The Cafe
---

### Post by asnd16 on 2007-08-03
has anyone been able to find a talking clock for ubuntu? Like talking as in speaking on every hour. . ? :guitar:

---

### Post by Onyros on 2007-08-03
> **asnd16 said:**
> has anyone been able to find a talking clock for ubuntu? Like talking as in speaking on every hour. . ? :guitar:Hahaha, that would be... errm... actually, I'd be afraid of throwing my laptop against the wall.

I hate time. :P

---

### Post by tennisplaya05 on 2007-08-03
well, here's what i could find:
[http://www.jumpstation.co.uk/scripts/talkingclock/](http://www.jumpstation.co.uk/scripts/talkingclock/)

It seems to utilize alsa and bash, so i'd assume it should work in ubuntu.
all you need now are the wav files of the numbers themselves. I guess you could download those from somewhere. Or if you have a nice microphone, you could do them yourself, or find someone with a sexy voice to record them for you :)

---

### Post by reclusivemonkey on 2007-08-03
> **tennisplaya05 said:**
> well, here's what i could find:
[http://www.jumpstation.co.uk/scripts/talkingclock/](http://www.jumpstation.co.uk/scripts/talkingclock/)

It seems to utilize alsa and bash, so i'd assume it should work in ubuntu.
all you need now are the wav files of the numbers themselves. I guess you could download those from somewhere. Or if you have a nice microphone, you could do them yourself, or find someone with a sexy voice to record them for you :)

There's a much easier way. Just install festival, and use the script I've attached (save it as clock.sh, make it executable). Run it via cron at whatever frequency you require.

---

### Post by init1 on 2007-08-03
There is something in the repos called saytime
```

sudo apt-get install saytime
watch -n 360 saytime

```

---

### Post by bicchi on 2007-08-12
I really like the idea of doing this from a cron job that runs on the hour. 
I also noticed that if I am playing music in the background festival does not work. 
A workaround is to use the aoss command before festival. You might need to install: alsa-oss
```

echo "Its" `date "+%l oclock"` | aoss festival --tts

```

---

### Post by ways on 2008-09-08
my script for this, partly inspired by posts above

```

#!/bin/bash
#
# call out the hour. run in crontab

HOUR=`date "+%k"`
FIRST=8
LAST=18
#SPEAK="espeak"
SPEAK="aoss espeak" #for multiple access to soundcard

#shh! its night time
[ $HOUR -lt $FIRST ] || [ $HOUR -gt $LAST ] && exit 1

#english
echo "Its $HOUR oclock" | $SPEAK

```

---

### Post by Tomosaur on 2008-09-08
Simple command will do it:
```

date +"%A, %B %e %Y, %l:%M %p" | espeak

```

I have it bound to an alias called 'speaktime' in my ~/.bashrc file:
```

alias speaktime='date +"%A, %B %e %Y, %l:%M %p" | espeak'

```

---

### Post by qwill on 2008-10-10
flite_time does the job too...

---

### Post by snova on 2008-10-10
There was an entry to the IOCCC that did this. :)

---

### Post by rbolio on 2008-10-20
I found this code somewhere in the net.... need2 more minutes to find out if it worked or if i need to keep terminal open...but here it is

> 
(crontab -l;echo "0,15,30,45 * * * * (echo it is now;date +%I:%M%p )|espeak --stdout|sox -q -V0 -t wav - -t alsa pulse")|crontab -



---

### Post by rbolio on 2008-10-20
> **init1 said:**
> There is something in the repos called saytime
```

sudo apt-get install saytime
watch -n 360 saytime

```


with this, how often will the time be said? hourly?

---

### Post by rbolio on 2008-10-20
wait! raincheck.... i wrote a simple tutorial from what i have found on the net.... just waiting for it to be aproved... (pwnd)  its really simple...ill post link as soon as i can.

---

### Post by Rodney9 on 2008-11-05
> **rbolio said:**
> wait! raincheck.... i wrote a simple tutorial from what i have found on the net.... just waiting for it to be aproved... (pwnd)  its really simple...ill post link as soon as i can.


I'm searching for a talking clock that will announce the time every half hour even when other audio is playing.

---

### Post by Rodney9 on 2008-11-05
> **bicchi said:**
> I really like the idea of doing this from a cron job that runs on the hour. 
I also noticed that if I am playing music in the background festival does not work. 
A workaround is to use the aoss command before festival. You might need to install: alsa-oss
```

**[SIZE="4"]echo "Its" `date "+%l oclock"` | aoss festival --tts[/SIZE]**

```

Cool, this does play with streaming audio, so now I have to work out how to get it to run each half hour, any ideas ?

---

### Post by Rodney9 on 2008-11-05
I have tried adding 
 
echo "Its" `date "+%l oclock"` | aoss festival --tts

to Gnome-Schedule, but it will not allow the percentage symbol %

How else can I run it every half hour, or is there some workaround with the % symbol ?

---

### Post by DougieFresh4U on 2008-11-06
> **rbolio said:**
> with this, how often will the time be said? hourly?

My machine is doing it on the half hour and hour

---

### Post by Rodney9 on 2008-11-06
> **Rodney9 said:**
> I have tried adding 
 
echo "Its" `date "+%l oclock"` | aoss festival --tts

to Gnome-Schedule, but it will not allow the percentage symbol %

How else can I run it every half hour, or is there some workaround with the % symbol ?

> My machine is doing it on the half hour and hour

What did you use, can you hear it over music ?


echo "Its" `date "+%l oclock"` | aoss festival --tts

does work well, if only in Gnome-Schedule

---

