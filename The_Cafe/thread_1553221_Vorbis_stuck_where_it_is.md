---
title: "Vorbis stuck where it is?"
date: 2010-08-14
forum: The Cafe
---

### Post by spoons on 2010-08-14
So, we've seen Google embrace vorbis as the audio codec for it's WebM container along with VP8 for the video. But in the last year, there doesn't seem to have been any improvements to Vorbis' sound quality. Has Vorbis reached it's peak? Or is there more quality to squeeze from it? Being an great codec and an excellent example of what open source can achieve, where do we go from here?

---

### Post by phrostbyte on 2010-08-14
Vorbis is lossy so it will not be better quality than something like FLAC. I think Vorbis's quality/compression ratio is pretty competitive, and it is unlikely to improve in any major way unless some fundamental laws of mathematics change, or we start breaking people's hearing or something.

---

### Post by spoons on 2010-08-14
I was just intrigued to whether it is possible to improve the codec any more and if anyone was working on it. Once I understand C to a good extent I might take a crack at it myself. :)

---

### Post by Bachstelze on 2010-08-14
> **spoons said:**
> I was just intrigued to whether it is possible to improve the codec any more and if anyone was working on it. Once I understand C to a good extent I might take a crack at it myself. :)

Merely "understanding C" won't get you anywhere.  Audio compression involves very advanced math.

---

### Post by spoons on 2010-08-14
> **Bachstelze said:**
> Merely "understanding C" won't get you anywhere.  Audio compression involves very advanced math.

I'm hopefully taking Further Mathematics at A-level (after high school, depends on grades) and it's a direction I'd like my career to go down. (in science)

I will do what is required. ;)

---

### Post by phrostbyte on 2010-08-14
> **spoons said:**
> I'm hopefully taking Further Mathematics at A-level (after high school, depends on grades) and it's a direction I'd like my career to go down. (in science)

I will do what is required. ;)

Look up the discrete cosine transform. :)

---

### Post by spoons on 2010-08-14
> **phrostbyte said:**
> Look up the discrete cosine transform. :)

Thanks, it looks pretty interesting. :)

---

### Post by murderslastcrow on 2010-08-14
I don't quite understand the mechanics at work here, but I do know you shouldn't underestimate the complexity of sound. It wasn't so long ago that OGG couldn't get some sounds quite right in output, whereas mp3 could. So, while it was technically superior, in its primary use case it wasn't perfect.

Today, it definitely kicks mp3's butt. It can be used to run dialup radio stations, man- c'mon. Do you really need it MORE compressed?

Any dedicated open source developer will tell you in response to that question, "sure, why not?" Vorbis is all about quality and efficiency. I think the best way to get it more optimized is to spread its use! The more people who use it, the more incentive developers have to improve upon it.

Theora is pretty dang good, too, and the OnVideo codec people just kept making it better. I don't doubt that there's still a ways to go before we give up on optimizing it. Of course, we don't want this to be at the loss of quality, so it's important to keep the end product in mind as you develop.

I understand your sentiment, though. Technology, especially open source, has continually proven to optimize what we have and make it more efficient and usable. However, just as we're seeing in modern computing, many formats, programs, and libraries are reaching the end of life so far as optimization and features go. The beautiful thing about open source is that it can adapt to exactly what the user wants as the ages change, but many programs provide so much flexibility outright that they probably won't need a big change for another 10 years or so, when we have new uses to put it to.

So, while open source may be the future of high-end technology, we must also consider how web applications are reinventing the paradigm. I predict we will see tons of crappy projects online that could use some improvement, and that much of that improvement will be in HTML5 and later. This is the interest and usefulness of software development- to create new opportunities where they never existed before, and give normal people new, more convenient ways to do their work.

If you really want to get that deep, I encourage you to do so. Just don't quit your day job XD.

---

### Post by phrostbyte on 2010-08-14
Well if the goal is good quality audio output, for some waveforms a simple codec can be devised that provides near total lossy compression (100%). I believe an implementation of this codec may even be bundled with Ubuntu.

---

### Post by NightwishFan on 2010-08-14
Vorbis always impressed me. I heard about this:
[http://en.wikipedia.org/wiki/Vorbis#aoTuV](http://en.wikipedia.org/wiki/Vorbis#aoTuV)

---

### Post by spoons on 2010-08-15
> **murderslastcrow said:**
> 
If you really want to get that deep, I encourage you to do so. Just don't quit your day job XD.

Thanks for the write-up! And I don't have a day job yet, I'm trying though. ;)

---

