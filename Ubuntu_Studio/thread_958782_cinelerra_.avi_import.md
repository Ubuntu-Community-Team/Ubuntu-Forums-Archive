---
title: "cinelerra .avi import"
date: 2008-10-25
forum: Ubuntu Studio
---

### Post by bsharp on 2008-10-25
Technically I have two problems, I just need one solved in order to get finished:

1.Cinelerra cannot import .avi files, although .mpgs work fine. When I run it from a terminal, this seems to be important:

```

new_acodec: couldn't find codec for " "
new_vcodec: couldn't find codec for "FMP4"

```

2.Acidrip (my camera is one of those noob-friendly ones that writes directly to dvd *shudder*) rips to an .avi file just fine, but when ripping to .mpg, there is just a black screen that refuses to play in Totem while the .avi plays fine. Same problem when trying to convert the .avi to .mpg with ffmpeg.

So the problem. I have a clip that *very badly* needs to be edited, but I can't edit it because Cinelerra doesn't support .avi OR Acidrip/ffmpeg can't give me a working .mpg.

---

### Post by skullmunky on 2008-10-31
Maybe try using ffmpeg to convert it from AVI to MPG, then edit it in cinelerra?

---

