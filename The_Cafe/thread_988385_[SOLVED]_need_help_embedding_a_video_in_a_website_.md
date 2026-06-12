---
title: "[SOLVED] need help embedding a video in a website - making .swf"
date: 2008-11-20
forum: The Cafe
---

### Post by daverich on 2008-11-20
so I've got the mp4 file,- which I've also converted to a .flv

I need to embed it into a website without the media player controls - so ideally a .swf would work.

now,- KINO says it exports to .swf but it never seems to actually make the .swf file,- it's 0bytes big.

I've tried turning it into a gif even (the resulting file is huge), but the resulting .gif wont open in any of the tools that could convert it into a .swf.


I'm getting a sneaking suspicion that my ffmpeg installation does not in fact have the .swf codec in it - does anyone know how one might check?

Kind regards

Dave Rich

---

### Post by Vadi on 2008-11-20
I would use a site like [http://blip.tv/](http://blip.tv/) to upload the file to and them embed it into your website.

---

### Post by daverich on 2008-11-20
> **Vadi said:**
> I would use a site like [http://blip.tv/](http://blip.tv/) to upload the file to and them embed it into your website.

the problem is it needs to autoplay too.

it's just a video of a dancer in the background,- it's just decoration - not exactly a movie as such - just a posh .gif anim as it were.

Kind regards

Dave Rich

---

### Post by daverich on 2008-11-20
I should also say I've been trying to use the swftools package, but this wont open the gif I've made.

The other wierd thing is I have actually succeeded in making an .swf but it only plays in Totem, Firefox just sits there with a blank screen.

I can't actually remember how i made the .swf now as I've been trying all sorts all afternoon to get this to work... :(

Kind regards

Dave Rich

---

### Post by daverich on 2008-11-21
ok folks I did it!

I finally go it working!!!!!

YAY!!!!

ok.

enough excitement.

I used a program called Flowplayer,- but v2 not the newer v3 which is much more complicated to figure out.

Simply a matter of putting 

autoPlay: true,
hideControls: true

in the javascript bit and it works like a charm.

I'm very very happy I got this sorted.

Seems like a huuge amount of hoop jumping just to get an .flv to show up in a website,- I hope some lovely people are making some simple .swf authoring tools :)

Kind regards

Dave Rich

---

### Post by Vadi on 2008-11-21
Glad got got it working. Now click on 'Thread Tools' and 'Mark Thread as Solved' ;)

---

### Post by daverich on 2008-11-21
> **Vadi said:**
> Glad got got it working. Now click on 'Thread Tools' and 'Mark Thread as Solved' ;)

done :)

Kind regards

Dave Rich

---

