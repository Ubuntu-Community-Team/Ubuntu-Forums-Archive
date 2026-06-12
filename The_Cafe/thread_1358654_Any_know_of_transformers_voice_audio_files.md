---
title: "Any know of transformers voice audio files?"
date: 2009-12-18
forum: The Cafe
---

### Post by s3a on 2009-12-18
Instead of the regular introductory music of Ubuntu, it is possible to change to another audio file because I would love to have something like an Optimus Prime (from the movie) say "Welcome" or something in a robotic way.

Thanks! :)

---

### Post by Kingsley on 2009-12-18
You could find a video file of Optimus Prime speaking, rip the audio from that with ffmpeg, and then cut out the sound bite you're interested in with audacity.

---

### Post by Crunchy the Headcrab on 2009-12-18
How about: "Autobots!  Transform and roll out!"

Oh, man.  I'm totally doing this.

---

### Post by jerrrys on 2009-12-18
never did it, but i can point you here

[http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=change+startup+music&as_qdr=all&sa=Google+Search&lang=en#929](http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=change+startup+music&as_qdr=all&sa=Google+Search&lang=en#929)

and here

[http://www.google.com/search?q=transformers+voice+audio+files&ie=utf-8&oe=utf-8&aq=t&rls=org.mozilla:en-US:official&client=firefox-a](http://www.google.com/search?q=transformers+voice+audio+files&ie=utf-8&oe=utf-8&aq=t&rls=org.mozilla:en-US:official&client=firefox-a)

---

### Post by stinger30au on 2009-12-18
a quick google search and i found what your looking for

[http://www.moviesoundclips.net/sound.php?id=111](http://www.moviesoundclips.net/sound.php?id=111)

---

### Post by s3a on 2009-12-18
Here's a specific site I found if the rest of you want which has audio files from the movie but not quite the "Autobots - Assemble!" (or something welcoming) or whatever that I want: [http://quotableoptimusprime.blogspot.com/](http://quotableoptimusprime.blogspot.com/)

If someone finds something better, please post the exact link of the site :)

---

### Post by Crunchy the Headcrab on 2009-12-19
Okay.  This is what I want to do.  I want the sound that occurs at GDM to be the transforming sound.  You know the one that's like "kukukishkish"... hmm.... yeah that's exactly what it sounds like (rolls eyes).

Anyway, that's what I want and then I want the sound that plays when the desktop actually appears to be "Autobots, transform and roll out!"

I'll see what I can come up with, I haven't tried to find sound files yet.

---

### Post by juancarlospaco on 2009-12-19
> **crunchy the headcrab said:**
> "autobots, transform and roll out!"


**epic**

---

### Post by Puck7 on 2009-12-19
I'd so love to have this :D

---

### Post by Crunchy the Headcrab on 2009-12-21
I changed my audio, as to what I changed it to that's a secret.

I had to lower the volume of both sounds because they were too loud (audacity).If anyone is interested a simple way to change your startup sounds: backup system-ready.ogg and desktop-login.ogg in /usr/share/sounds/ubuntu/stereo and then replace them with an audio clip that has been named the same thing.  (the backup is in case you want to go back to the originals).  You can convert audio to .ogg using audacity.

The easiest way for a noob to do this is to open a terminal and sudo nautilus.  Keep in mind that you've just given nautilus root privileges and you can totally mess up your system.  If you do this method you can just drag and drop the files into the sudo nautilus window (first navigate to the proper folder) and click replace when it asks you.  Make sure to exit the terminal and close the nautilus window.

---

