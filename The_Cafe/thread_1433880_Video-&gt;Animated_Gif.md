---
title: "Video-&gt;Animated Gif?"
date: 2010-03-19
forum: The Cafe
---

### Post by AJHunter on 2010-03-19
Question: Is there any software out there for ubuntu that converts video into animated gifs?

---

### Post by HappinessNow on 2010-03-19
> **ajhunter said:**
> question: Is there any software out there for ubuntu that converts video into animated gifs?
gimp

---

### Post by AJHunter on 2010-03-19
Automatically?

---

### Post by Psumi on 2010-03-19
> **AJHunter said:**
> Automatically?

Flash.

Oh wait, you wanted linux.

Oh wait, you wanted automatically.

---

### Post by hessiess on 2010-03-19
Why would you want to, GIF is awful, it only supports 256 colours, and produces much larger files. Codecs like h264, or even Theora produce much better quality with a much smaller file size.

If its for the web, use a flash video player like Flowplayer, at least until HTML5 is standardised.

---

### Post by Psumi on 2010-03-19
> **hessiess said:**
> Why would you want to, GIF is awful, it only supports 256 colours, and produces much larger files. Codecs like h264, or even Theora produce much better quality with a much smaller file size.

If its for the web, use a flash video player like Flowplayer, at least until HTML5 is standardised.

Animated Avatar?

---

### Post by hessiess on 2010-03-19
> **Psumi said:**
> Animated Avatar?

Maby, but in that case doing it manually with GIMP wouldn't be too difficult.

video -> ffmpeg convert to image sequence -> GIMP -> animated GIF.

---

### Post by AJHunter on 2010-03-19
> **Psumi said:**
> Animated Avatar?
EXACTLY! That, and just to have an animated gif of what I want.

---

### Post by fromthehill on 2010-03-19
softwares can't crawl into your brain to figure out exactly what you want, so this is as automated as it's going to get

cut out the frames you want with avidemux
open the frames as layers in gimp

resize, crop, whatever you want (put '(XXXms)' into the layer title to change how long a frame will be displayed) 

you can view the animation in gimp with filters>animation>playback
if you're finished, optimize the image with filters>animation>Optimize(for gif)

save the optimized file as gif. gimp will ask if you want to save it as a flat file or animation
[IMG]http://img291.imageshack.us/img291/5537/screenshot22.png[/IMG]

---

### Post by Psumi on 2010-03-19
> **AJHunter said:**
> EXACTLY! That, and just to have an animated gif of what I want.

Too bad you can't have animated avatars on this forum unless you're staff.

---

