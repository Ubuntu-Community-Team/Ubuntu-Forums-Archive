---
title: "running winamp with wine"
date: 2009-06-02
forum: Wine
---

### Post by andrea000 on 2009-06-02
Hello all

here is what i am trying to do i can not sync a mp3 player with
any piece of software in ubuntu but what if i use winamp or
something like that in wine would i be able to sync it that way?

Thank you so much

---

### Post by Random-penguin on 2009-06-02
Have you checked if wine supports winamp? And if so which version..

---

### Post by gvoima on 2009-06-02
I doupt. Don't know about winamp, but if it uses some hardware layer to connect to the mp3 device (and it most certainly will), it might not be directly possible.

What device is it that you are using?

[edit]
And seems that most of the stuff in winamp with wine doesn't work + it's very slow.
But try the winamp lite version, it should work just fine.
[/edit]

---

### Post by andrea000 on 2009-06-02
I am using a sansa connect wifi player it would like to use something in
ubuntu but i can't get it to sansa tell's me that there no support for
linux but people have been using mp3 players with linux for years.The 
player is a mtp player and there's no way to change it that's what sansa
tells me anyway.I am using wine 1.1.22 and the will be using the newest
winamp.Winamp is not in wines database i may use media monkey or something
like that media monkey is in there db.

Thank you

---

### Post by Random-penguin on 2009-06-03
Hi, I must admit I'm not an expert at MTP devices but oddly enough there is a feature on this very subject in this months "Linux Magazine"!!!!! I not sure how available this is in The States though!

Basically you need to get hold of th "libmtp" library (preferably the latest version) which is an open source project designed to implement MTP support to Linux and Unix systems.

Hope this helps;)

---

### Post by Random-penguin on 2009-06-03
Hi, just read the article and Amarok and RhythmBox support MTP out of the box...... you just need to enable it.

So in RhythmBox got to edit; pluggins. Then scroll down and enable "portable player - MTP". 

That's it!!!! Then when you connect RythmBox should find it.

Hope this works for you and saves all that hastle with wine..........

---

### Post by andrea000 on 2009-06-03
I have the latest libmtp tools and i have enabled it still doesn't help.

---

