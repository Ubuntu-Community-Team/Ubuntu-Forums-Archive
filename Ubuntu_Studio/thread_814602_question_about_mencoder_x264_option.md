---
title: "question about mencoder x264 option"
date: 2008-05-31
forum: Ubuntu Studio
---

### Post by digitalcat on 2008-05-31
I have some 1080i HD clips from camcorder and need to transcode them to x264 and rescale to 720p. I see there is an option in mencoder's x264encopt for **(no)interlaced**. The man page wasn't clear about the use of this option: do I need to select interlaced, because the source file is interlaced; or do I need to use nointerlaced, because I want the target file to be progressive scan? Any insight would be greatly appreciated.

---

### Post by digitalcat on 2008-06-01
Anyone? Or am I asking this question in the wrong forum?

---

### Post by finite9 on 2008-06-01
i would recommend the "-vf kerndeint" option as this has given me the best results in my opinion.  It de-interlaces interlaced source material.  I use it on all my home videos.  I had tried several deinterlacers when Fiesty Fawn was released and thought that most of the others were visible poorer quality than kerndeint.

---

### Post by finite9 on 2008-06-01
I have not looked into upscaling to 720p.  If you know how to do this with standard definition material, please do reply and tell me how.

---

### Post by digitalcat on 2008-06-01
Awesome! Thanks a lot.

---

### Post by digitalcat on 2008-06-01
Me either. I was just looking to deinerlace 1080i materials to 720p, which I think is not the same as upscaling from SD videos...
> **finite9 said:**
> I have not looked into upscaling to 720p.  If you know how to do this with standard definition material, please do reply and tell me how.

---

### Post by aeiah on 2008-06-01
> **finite9 said:**
> I have not looked into upscaling to 720p.  If you know how to do this with standard definition material, please do reply and tell me how.

just output to a resolution with a width of 1280, surely?

you'll want to deinterlace if its interlaced of course, and probably want a cubic scaler, but there isnt anything particularly special in upscaling to 720p as there is with any other size. just remember that for it to be classed as 720p then the resolution needs to be either 1280 wide OR 720 high with progressive frames.

---

### Post by finite9 on 2008-06-02
yeah, problem is that if I use -vf scale=1280:720 (dont know if syntax is correct there), then this will scale it to right proportions, but then I will have problems when I burn it to disc and play it on my DVD player.

Problem is when creating xvids that standalone dvd players require basic xvid specs to be used.  If I specify anything other than "-vf scale" or do not use scaling at all, then the clip will not play on my standalone player.

I dont know how this will work in a Bluray player.  Maybe if I upscale clips to 720 they will play ok in Bluray (when i encode to x264/aac/mp4box container using QT compatible settings with Mencoder), but I have not tested.

---

### Post by aeiah on 2008-06-02
[QUOTE=finite9;5098467]yeah, problem is that if I use -vf scale=1280:720 (dont know if syntax is correct there), then this will scale it to right proportions, but then I will have problems when I burn it to disc and play it on my DVD player.

Problem is when creating xvids that standalone dvd players require basic xvid specs to be used.  If I specify anything other than "-vf scale" or do not use scaling at all, then the clip will not play on my standalone player.
[QUOTE]

its a limitation of your standalone xvid player (and almost all others) in that they dont display HD video. unless yours reportedly does display HD video, in which case there's something else at fault. chances are, normal dvd players with xvid capabilities will not display anything that is of a higher resolution than dvds are.

---

### Post by JEDIDIAH on 2008-06-03
> **digitalcat said:**
> I have some 1080i HD clips from camcorder and need to transcode them to x264 and rescale to 720p. I see there is an option in mencoder's x264encopt for **(no)interlaced**. The man page wasn't clear about the use of this option: do I need to select interlaced, because the source file is interlaced; or do I need to use nointerlaced, because I want the target file to be progressive scan? Any insight would be greatly appreciated.

Why bother? If you have a destination that can do another flavor of HD, I would expect that your display equipment would be able to adjust as the output is being displayed (TV, DVD player).

---

### Post by digitalcat on 2008-06-04
> **JEDIDIAH said:**
> Why bother? If you have a destination that can do another flavor of HD, I would expect that your display equipment would be able to adjust as the output is being displayed (TV, DVD player).

My lowly dell 700m lappy with 1.8GHZ centrino CPU cannot handle 1080i videos, but fortunately 720p plays just fine. I eventually ended up with one pass divx4 encoding since it's faster and provides reasonable quality.

---

