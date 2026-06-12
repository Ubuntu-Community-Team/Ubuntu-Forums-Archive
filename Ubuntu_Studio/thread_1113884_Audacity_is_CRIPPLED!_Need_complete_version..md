---
title: "Audacity is CRIPPLED! Need complete version."
date: 2009-04-02
forum: Ubuntu Studio
---

### Post by trlkly on 2009-04-02
I'd been trying forever to use the pitch changing functions in Audacity that I found in the documentation. I tried various plugins, but they all sound horrible. 

Turns out audacity is supposed to have pitch change built in, just like the Windows version. The problem is that the audacity in the universe repo has SoundTouch DISABLED. Why the heck would you cripple a program like that? (And especially making it work better on M$ platforms!)

Anyways, anyone know where I can get a build that has EVERYTHING enabled? I don't want to build it myself, as I always have to download 500 extra libraries when I do that.

---

### Post by eye208 on 2009-04-02
Audacity in Ubuntu 8.10 includes SoundTouch.

---

### Post by Dougie187 on 2009-04-02
> **trlkly said:**
> I'd been trying forever to use the pitch changing functions in Audacity that I found in the documentation. I tried various plugins, but they all sound horrible. 

Turns out audacity is supposed to have pitch change built in, just like the Windows version. The problem is that the audacity in the universe repo has SoundTouch DISABLED. Why the heck would you cripple a program like that? (And especially making it work better on M$ platforms!)

Anyways, anyone know where I can get a build that has EVERYTHING enabled? I don't want to build it myself, as I always have to download 500 extra libraries when I do that.

What version are you running? You might check their site to see if there is a more up-to-date version in .deb format that you could use.

---

### Post by clubsoda on 2009-04-02
Do you have the libsoundtouch1c2 library installed?

---

### Post by babarosa on 2009-04-02
Hello everyone,

on [www.getdeb.net](www.getdeb.net) you can download audacity v1.3.7 for hardy which is the latest stable version.
Compiling audacity is not that hard, although the most recent CVS of v1.3.8 is 115 MB large!

Ardour v2.7.1 also can be downloaded from [www.getdeb.net](www.getdeb.net), to my mind it also includes soundtouch-features. Ardour v2.8 can be compiled quite easily and the tarball is only 3.5MB large.

I don't recommend Inarticulate Ibex for audio purposes, better to stay with Heroic Hardy and compile jackd, qjackctl, ... by yourself. You'll learn a lot and the system's performance is better than using repo versions.

Regards,
Michael

---

### Post by trlkly on 2009-04-02
yeah, so far the repo'd jackd hasn't worked very well, anyways. (I wanted to use Totem to view Youtube videos of songs I'm supposed to learn. But I have to learn them in a different key, so I thought I'd run it through Jack Rack. Being a total newb on this, the instructions I found didn't quite work.) 

Anyways, I'll look into the other solutions and report back.

---

