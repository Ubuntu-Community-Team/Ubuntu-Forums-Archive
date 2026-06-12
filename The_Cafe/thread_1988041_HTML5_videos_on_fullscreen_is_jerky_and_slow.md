---
title: "HTML5 videos on fullscreen is jerky and slow"
date: 2012-05-26
forum: The Cafe
---

### Post by pt123 on 2012-05-26
I was trying out HTML5 videos from youtube on fullscreen and it's was awful, the videos made the whole system unresponsive, and the video was jerky. But when there are not in fullscreen they perform better than Flash. But flash smashes it in full screen. 
I am using 12.04 with the binary nvidia drivers, using Firefox. 

Anyone else experiencing this, is this a common 'feature' of HTML5 video?

---

### Post by Primefalcon on 2012-05-26
> **pt123 said:**
> I was trying out HTML5 videos from youtube on fullscreen and it's was awful, the videos made the whole system unresponsive, and the video was jerky. But when there are not in fullscreen they perform better than Flash. But flash smashes it in full screen. 
I am using 12.04 with the binary nvidia drivers, using Firefox. 

Anyone else experiencing this, is this a common 'feature' of HTML5 video?
I have issues with html5 video as well at least on youtube, not sure whether its html5, webm or google at fault though... but yeah flash in better for me atm as well

what I typically do these days to watch youtube content is to install minitube, its a good youtube watching program and in the repo's it even allows me to watch vids in 720p!

---

### Post by Shadius on 2012-05-26
Video for me on my Ubuntu is choppy, makes my system laggy. :( I don't know why.

---

### Post by BLewis on 2012-05-26
Ok, which Nvidia drivers exactly are you using - which version etc. 

Unity/Gnome 3/KDE which environment?

Have you tried other drivers?

Have you tried other flash plugins?

Have you tried other browsers?

---

### Post by pt123 on 2012-05-26
> **BLewis said:**
> Ok, which Nvidia drivers exactly are you using - which version etc. 

Unity/Gnome 3/KDE which environment?

Have you tried other drivers?

Have you tried other flash plugins?

Have you tried other browsers?

I mentioned 12.04 as I am using the binary drivers that come with it and obviously Unity as it is default setup. 

As you have missed the point, this thread was whether other people on Ubuntu were experiencing similar problem, this not a bug report. 

HTML5 video when it came was promised to provide better handling of video as the browser can use the OS video codec libraries to handle the video.

---

### Post by mips on 2012-05-27
> **pt123 said:**
> 
Anyone else experiencing this, is this a common 'feature' of HTML5 video?

Please provide a link to a video we can use for test referencing so we are all on the same page.

---

### Post by pt123 on 2012-05-27
> **mips said:**
> Please provide a link to a video we can use for test referencing so we are all on the same page.
it happens on all youtube videos

---

### Post by mips on 2012-05-27
> **pt123 said:**
> it happens on all youtube videos

Well provide a short clip as an example anyway.

---

### Post by pt123 on 2012-05-27
[http://www.youtube.com/watch?v=60GJ0dJ1xmE&feature=youtu.be](http://www.youtube.com/watch?v=60GJ0dJ1xmE&feature=youtu.be)

---

### Post by mips on 2012-05-27
Works fine in fullscreen for me in both FF & Chromium.

Ubuntu 12.04 base + XFCE 4.10, nvidia-current 295.40, chromium 18.0.1025.151, FF 12.0

---

### Post by pt123 on 2012-05-27
> **mips said:**
>  flashplugin-installer 11.2.202.233
We are talking about HTML5, Flash is fine for me too.

---

### Post by Erik1984 on 2012-05-27
11.10 Nvidia binary drivers and the video plays fine for the most part. Although CPU usage is high when fullscreen. Only problem I have with html5 vids is a little 'stutter' at the beginning of each video.

---

### Post by mips on 2012-05-27
> **pt123 said:**
> We are talking about HTML5, Flash is fine for me too.

Sorry dunno why I added that as I was using html5, just habit.

---

### Post by ikt on 2012-06-11
+1 for laggy full screen html5 video... how is this even possible? I thought it was directly playing mp4's.

---

### Post by Dax0r on 2012-06-11
> **ikt said:**
> +1 for laggy full screen html5 video... how is this even possible? I thought it was directly playing mp4's.

Same here.
I experienced very laggy video even when not full screen. Direct rendering enabled. Cpu (firefox PID) at 100% occurred...

---

### Post by pt123 on 2012-06-11
There is actually a fix for this, you need to enable 
**layers.acceleration.force.enabled** in **about:config**
this should show "**GPU Accelerated Windows**" in **about:support** as being capable. After doing this fullscreen HTML5 videos did not lag and stutter. 
But the **downside** it affects the rest of your web browsing and it became slower and the scrolling was not smooth. So I decided to stick with Flash, and turn it off.

---

### Post by Erik1984 on 2012-06-17
Just one for reference: [http://www.youtube.com/watch?v=MShbP3OpASA](http://www.youtube.com/watch?v=MShbP3OpASA) This video (html5) started very choppy on Firefox 13 (also slowing down scrolling on another tab). Started normally on Chromium. Strange thing is when I pasted the same URL in Firefox again it played without stuttering.

---

### Post by darrenn on 2012-06-17
Here is a timely video of why some people are having problems and others not. Also, I have always had a problem with tearing but im happy it just works at all. 

> During the Q&A, a person asks why NVIDIA does not play well with Linux. Torvalds explained shortly that NVIDIA has been one of the worst companies to work with Linux project &#8212; which makes it even worse that NVIDIA ships a high number of chips for Android devices (which use Linux inside). Torvalds even summarized that ('Nvidia, f*** you!') in a playful manner. What has been your experience on NVIDIA drivers with Linux?"

[http://www.youtube.com/watch?v=MShbP3OpASA&feature=youtu.be&hd=1&t=48m9s](http://www.youtube.com/watch?v=MShbP3OpASA&feature=youtu.be&hd=1&t=48m9s)

---

### Post by MisterGaribaldi on 2012-06-17
Just tried it in Safari on Lion, and yeah, it is a bit jerky in full-screen mode here as well, so this may not necessarily strictly be a "Linux" thing.

---

### Post by alexfish on 2012-06-18
Just wondering,

I used Gtk webkit as standalone , with direct link to videos only

found no problems , on certain file types , nvidia graphics

what has changed.

Regards

alexfish

---

