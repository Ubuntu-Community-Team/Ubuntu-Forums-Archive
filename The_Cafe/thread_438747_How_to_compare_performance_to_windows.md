---
title: "How to compare performance to windows"
date: 2007-05-10
forum: The Cafe
---

### Post by D!mon on 2007-05-10
Hi,

I and my co-worker have 2 computers with exactly the same hardware (Core2 Duo 2.13), one with Vista x64 installed and another with Feisty amd64.
The question is if there is any way to compare ubuntu vs. vista performance?
Ubuntu works better with memory for sure, my co-worker even had to get one more gig of ram to run vista smoothly.
We tried to archive quite a big directory with 7zip, first time ubuntu was the winner but that was mainly due to 'scanning files' stage on vista; after second run it was gone and the archiving time was almost identical.
So does anybody know the 'true' way to compare linux vs. windows performance?:)
Actually it's interesting whether one of them will be the 'winner' or there won't be so much difference between linux and windows?

---

### Post by rai4shu2 on 2007-05-10
I don't know if this works with Vista, but if you have 3D going smoothly you could try:

[http://www.futuremark.com/download/3dmark03/](http://www.futuremark.com/download/3dmark03/)

---

### Post by D!mon on 2007-05-10
3dmark for linux? don't think so. Btw, we have Beryl and Aero running with the integrated i965Q video. Beryl looks so much better, btw)) In Aero the best have is 'floppy windows' feature (similar to Win-Tab in beryl); they even have the quickstart button to enable it :D

---

### Post by rai4shu2 on 2007-05-10
3dmark03 works in wine. I don't see how else you can do a fair comparison.

---

### Post by deadlydeathcone on 2007-05-10
It barely, barely works in Wine. It's more of a proof of concept application at this point, really.

I can't really be much of a help, but 
[http://www.phoronix.com/]("http://www.phoronix.com/") is a Linux based site that does a lot of cross platform testing, although it's usually done with cross platform games. It's a lot like an arstechnica for the *nixes, really, so you might have some luck gleaming some good secrets.

---

### Post by aeiah on 2007-05-10
you could try something like the quake 4 or doom 3 demo, and you could also time a mencoder video encode perhaps. if you want a random video to use then grab the elephants dream, since its free and in large file sizes.

---

### Post by starcraft.man on 2007-05-10
I don't think there's any real way to get exact numbers for the two. Isn't it good enough that a comparison can even be made between an OS that costs 2-400 dollars and a free one? It is for me.

Not to mention, there is vastly different technology behind the both of them. For instance, vista is a ram hog because of two things, first its graphical and hardware requirements and secondly because of its need to cache things to ram, without its latter ability it would likely be somewhat slower. There are many more differences too, I could go on and on but in the end I don't think theres any such thing as a "definitive test" between the two, they are just two different fruits in a fruit basket :)

And me, I like the sweet orange that is Ubuntu :D

---

### Post by D!mon on 2007-05-10
starcraft.man, you re right, that's the reason why I've started this thread. It really may be apples and oranges; because of different filesystems etc. so it was just interesting for me is there any known 'standard' way (maybe like video encoding)  to compare the performance.

---

### Post by starcraft.man on 2007-05-10
> **D!mon said:**
> starcraft.man, you re right, that's the reason why I've started this thread. It really may be apples and oranges; because of different filesystems etc. so it was just interesting for me is there any known 'standard' way (maybe like video encoding)  to compare the performance.

Well, if all ya want is a straight up speed test to see which is fastest for a given app, then just pick any DVD encoder(thats compiled for windows and ubuntu) and take a large AVI, and transcode it to Mpeg for movieplayers, see how long it takes.

You can do the same for audio batch conversion and photo rendering.

Make sure the app isn't using wine to emulate wine, cuz then its not a fair test. Ya want something thats natively coded for both. 

Post the results if you do it :)

Note: [Linuxappfinder]("http://linuxappfinder.com/") will probably help you find such a program.

---

### Post by YokoZar on 2007-05-10
Performance varies depending on the application, and this variance changes between operating systems.  So, if you want to compare performance, you'll need to test the actual application you want to run.

---

