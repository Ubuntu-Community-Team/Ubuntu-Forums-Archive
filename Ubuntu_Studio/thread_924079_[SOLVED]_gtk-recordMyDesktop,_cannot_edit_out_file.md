---
title: "[SOLVED] gtk-recordMyDesktop, cannot edit out file"
date: 2008-09-19
forum: Ubuntu Studio
---

### Post by WinterWeaver on 2008-09-19
Not really sure if this post belongs here, but here goes.

I'm recording screencasts in Ubuntu. After recording my actions, I want to edit all of these together and add audio instructions and explanations to them.

Problem, none of the video editing apps that comes with ubuntu seems to open the output .ogg file from gtk-recordMyDesktop. So I'm unable to edit the files at all.

How can I get the output.ogg from gtk-recordMyDesktop to be compatable with the video editing apps?

Thanks,

PS: I'm not using Ubuntu Studio, just standard Ubuntu Hardy

WW

---

### Post by roqwez on 2008-09-19
> **WinterWeaver said:**
> Not really sure if this post belongs here, but here goes.

I'm recording screencasts in Ubuntu. After recording my actions, I want to edit all of these together and add audio instructions and explanations to them.

Problem, none of the video editing apps that comes with ubuntu seems to open the output .ogg file from gtk-recordMyDesktop. So I'm unable to edit the files at all.

How can I get the output.ogg from gtk-recordMyDesktop to be compatable with the video editing apps?

Thanks,

PS: I'm not using Ubuntu Studio, just standard Ubuntu Hardy

WW

I do agree with you winterweaver, it seems there's no apps can edit ogg theora out there . . .can anyone helps us?! im not a geek but i want to show to some of my friend my ubuntu dekstop on video . . .howcool and hows easy to use:)

---

### Post by eye208 on 2008-09-19
> **WinterWeaver said:**
> Problem, none of the video editing apps that comes with ubuntu seems to open the output .ogg file from gtk-recordMyDesktop.
Blender does.

If you want to use another video editor, this is how to prepare the file for import:
```
mencoder out.ogg -ovc xvid -oac pcm -xvidencopts fixed_quant=2 -o out.avi
```

---

### Post by WinterWeaver on 2008-09-19
You use blender as a video editor? How do you do that? Is it good as a video editor?

Thanks for the menconder tip, will give that a go as soon as I have a chance.

EDIT: btw. how would I do the above with ffmpeg?

---

### Post by eye208 on 2008-09-20
> **WinterWeaver said:**
> You use blender as a video editor? How do you do that? Is it good as a video editor?
It's the most stable video editor for Linux I have seen so far. All the editing of ["Big Buck Bunny"](http://www.bigbuckbunny.org/) was done in Blender. I am familiar with Blender's interface, so it's quite natural for me to use its video editor as well.

> btw. how would I do the above with ffmpeg?
Ubuntu's ffmpeg is crippled on the encoding side, so you probably have to resort to external repositories or compile it yourself. I haven't done either because mencoder is pretty much the same thing. Actually I find its command line options less confusing because they are grouped by codec, so its very easy to find out from the man page which codec supports which options.

---

