---
title: "dumb question"
date: 2010-10-11
forum: Ubuntu Studio
---

### Post by clipt on 2010-10-11
i guess i have a dumb question, i own a m-audio keystation 49e, curious to kow what i can install on my netbook to mess around and make some tunes, pretty much something easy to use and not time consuming to set up

---

### Post by Pablo_F on 2010-10-12
See [http://ubuntuforums.org/showthread.php?t=1591788](http://ubuntuforums.org/showthread.php?t=1591788)

---

### Post by AutoStatic on 2010-10-12
Maybe this video tutorial could be helpful: [http://www.youtube.com/watch?v=kBEzMC35gt8](http://www.youtube.com/watch?v=kBEzMC35gt8)

---

### Post by clipt on 2010-10-12
thank you the video and the thread helps

---

### Post by clipt on 2010-10-12
is there any other things i should install ontop of JACK? want to make sure i have them all loaded before i dive into this.\
thanx

---

### Post by Pablo_F on 2010-10-13
> is there any other things i should install ontop of JACK? want to make sure i have them all loaded before i dive into this.\

No, but you need to make a couple of tweaks in your system so that Jack can run in realtime mode.

sudo dpkg-reconfigure -p high jackd

Answer YES to rtprio and memlock security limits. And add your user to the audio group:

sudo adduser your_user_name audio

And then reboot.

These are the basic tweaks and hopefully, it will be enough to have fun with your keyboard. 

Please, the question is not dumb at all but the title does not help others in your shoes.

Cheers! Pablo

---

### Post by AutoStatic on 2010-10-13
Yes, you will need a softsynth. amSynth might be a good one to start with. Or you could download PHASEX from my PPA: [https://launchpad.net/~autostatic/+archive/ppa](https://launchpad.net/~autostatic/+archive/ppa)

---

### Post by clipt on 2010-10-13
ok sounds good. thank you guys for the help.

---

