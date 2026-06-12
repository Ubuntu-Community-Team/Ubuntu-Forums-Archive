---
title: "Picture slideshow for DVD software?"
date: 2008-06-14
forum: Ubuntu Studio
---

### Post by KingTermite on 2008-06-14
Are there any good software tools that one can create slideshows of pictures and/or video (with background sound)? 

Preferably one that will put it on DVD format so it will just automatically come up when put in a DVD player (not just some video format so it comes up with a filesystem to select video).


I saw a few tools listed for creating slideshows, but I was having trouble getting details about the features without installing and trying each and every one of them.




Edit: Ooops, sorry I didn't search first. I found a thread about DVD Slideshow. Looking at website now. Any thoughts on this software or others?

---

### Post by cotcot on 2008-06-15
kdenlive can do this

---

### Post by TenPlus1 on 2008-06-15
ManSlide is a good slideshow creator with 3D effects:

[http://www.getdeb.net/app/ManSlide](http://www.getdeb.net/app/ManSlide)

---

### Post by WrathofthePenguin on 2008-06-15
I was just about to start searching on this exact subject and found your post right at the top. I'd love to hear about what you've found so far and what you think. I'm going to put together some kind of presentation today for guests to play at a wedding reception. I'd like to have both pictures and video. I'm leaning towards a DVD, but decided to look and see what's out there.




> **KingTermite said:**
> Are there any good software tools that one can create slideshows of pictures and/or video (with background sound)? 

Preferably one that will put it on DVD format so it will just automatically come up when put in a DVD player (not just some video format so it comes up with a filesystem to select video).


I saw a few tools listed for creating slideshows, but I was having trouble getting details about the features without installing and trying each and every one of them.




Edit: Ooops, sorry I didn't search first. I found a thread about DVD Slideshow. Looking at website now. Any thoughts on this software or others?

---

### Post by KingTermite on 2008-06-18
> **WrathofthePenguin said:**
> I was just about to start searching on this exact subject and found your post right at the top. I'd love to hear about what you've found so far and what you think. I'm going to put together some kind of presentation today for guests to play at a wedding reception. I'd like to have both pictures and video. I'm leaning towards a DVD, but decided to look and see what's out there.

I haven't actually tried any yet, but appreciate the suggestions. I'll be looking in to them.

---

### Post by WrathofthePenguin on 2008-06-21
Well, I figured I'd post my experiences so far.

I tried Manslide, which looked great, but unfortunately was less than useable. I could do everything except actually export the video. Nothing was produced and when it asked me if I wanted to see the results, the "results" would flash and then disappear without actually showing me anything. In trying to fix it, I found a review of it where the reviewer was having the same problem. In the comments the developer who made Manslide defended the product and said it was likely a dependency problem and to check the page at kde-apps. Well, the page no longer exists.

I also tried Jslide. After some dependency work (see the README that comes with it) and a copy of the bin directory from the regular to the bytencode version, I was able to make it work. It seemed to work great until I actually reviewed the slideshow. On a short slideshow of 24 pictures it dropped the last two pictures. On longer slideshows it could drop dozens.

Thankfully I found a post which pointed to Open Movie Editor to make slideshows. It's in the add/remove section (didn't check the repositories). I installed it and tried it - while it's a little tricky to work with (no zoom on the timeline, so working with pictures can be challenging) the end result was a great slideshow. Another difficulty is that pictures can only be added one at a time by dragging. VERY time-consuming if you have a couple hundred pictures. Otherwise, it's the only thing I found that would actually produce a complete slideshow.

---

### Post by cotcot on 2008-06-21
> **WrathofthePenguin said:**
> Well, I figured I'd post my experiences so far.

I tried Manslide, which looked great, but unfortunately was less than useable. I could do everything except actually export the video. Nothing was produced and when it asked me if I wanted to see the results, the "results" would flash and then disappear without actually showing me anything.
After having seen manslide in this thread i tried is to see what it does. I can confirm the experience except when i export as DV. With DV i get a decent slideshow video.

---

### Post by piponline on 2008-06-23
I have been using dvdslideshow for over a year now and I am quite happy with it.
Altough I use the command line I believe there's a GUI for it too.

[http://dvd-slideshow.sourceforge.net/wiki/Main_Page]("http://dvd-slideshow.sourceforge.net/wiki/Main_Page")


[http://dvd-slideshow.sourceforge.net/wiki/Complete_Example]("http://dvd-slideshow.sourceforge.net/wiki/Complete_Example")

Bye.

---

### Post by sunnydayday on 2008-10-29
I recommend [**Wondershare DVD Slideshow Builder **]("http://www.photo-to-dvd.com/dvd-slideshow-builder.html#106")which is a professional software that can create DVD photo slideshows with 

photos, video clips and music and publish MPEG/AVI/WMV/MP4/3GP for YouTube or burn CD/DVDs. 

What it attract me is its plenty 2D/3D transitions and Ken-Burns effects.

CD or DVD created by DVD Slideshow Builder can actually play in the DVD player, you can enjoy your own movie on TV.

FlV file download from YouTube can be edit directly with Movie Story.You can not only burn flv to DVD but also edit it and create DVD menu.

Find more from its official website:
[http://www.photo-to-dvd.com/dvd-slideshow-builder.html]("http://www.photo-to-dvd.com/dvd-slideshow-builder.html#106")

---

### Post by jantra on 2008-10-29
Slide-Show Software Adds Life to Still Digital Images
Put your digital photos to good use and create a slide show for playback on TVs and PCs.

Tom Spring, PCWorld.com

---

### Post by mnrbig on 2008-10-29
> **sunnydayday said:**
> I recommend [**Wondershare DVD Slideshow Builder **]("http://www.photo-to-dvd.com/dvd-slideshow-builder.html#106")which is a professional software that can create DVD photo slideshows with 

photos, video clips and music and publish MPEG/AVI/WMV/MP4/3GP for YouTube or burn CD/DVDs. 

What it attract me is its plenty 2D/3D transitions and Ken-Burns effects.

CD or DVD created by DVD Slideshow Builder can actually play in the DVD player, you can enjoy your own movie on TV.

FlV file download from YouTube can be edit directly with Movie Story.You can not only burn flv to DVD but also edit it and create DVD menu.

Find more from its official website:
[http://www.photo-to-dvd.com/dvd-slideshow-builder.html]("http://www.photo-to-dvd.com/dvd-slideshow-builder.html#106")

This is windows software.Does it run flawlessly in wine?

---

### Post by celem on 2009-10-28
> **TenPlus1 said:**
> ManSlide is a good slideshow creator with 3D effects:

[http://www.getdeb.net/app/ManSlide](http://www.getdeb.net/app/ManSlide)

I loaded manslide and it was looking good until **crash**. Everytime that I attempt to load pictures, it:
```
ecomer@ubu-squirrel:/usr/bin$ ./manslide
**Segmentation fault**
ecomer@ubu-squirrel:/usr/bin$ 


```

---

### Post by WrathofthePenguin on 2010-06-10
> **WrathofthePenguin said:**
> Well, I figured I'd post my experiences so far.

I tried Manslide, which looked great, but unfortunately was less than useable. I could do everything except actually export the video. Nothing was produced and when it asked me if I wanted to see the results, the "results" would flash and then disappear without actually showing me anything. In trying to fix it, I found a review of it where the reviewer was having the same problem. In the comments the developer who made Manslide defended the product and said it was likely a dependency problem and to check the page at kde-apps. Well, the page no longer exists.

I also tried Jslide. After some dependency work (see the README that comes with it) and a copy of the bin directory from the regular to the bytencode version, I was able to make it work. It seemed to work great until I actually reviewed the slideshow. On a short slideshow of 24 pictures it dropped the last two pictures. On longer slideshows it could drop dozens.

Thankfully I found a post which pointed to Open Movie Editor to make slideshows. It's in the add/remove section (didn't check the repositories). I installed it and tried it - while it's a little tricky to work with (no zoom on the timeline, so working with pictures can be challenging) the end result was a great slideshow. Another difficulty is that pictures can only be added one at a time by dragging. VERY time-consuming if you have a couple hundred pictures. Otherwise, it's the only thing I found that would actually produce a complete slideshow.

How funny is this. I want to create another slideshow but couldn't remember what software I used last time. And here I find my own post that I don't even remember making...

---

### Post by brenti on 2010-08-26
anybody know where I can get a copy of manslide?  seems to have disappeared.

Thanks,
Brent

---

### Post by FYI on 2010-10-20
I've been using photo flash maker, it very easy to make a slideshow with music and get it burn on dvd.
[http://www.photo-flash-maker.com/make-a-slideshow-with-music.html](http://www.photo-flash-maker.com/make-a-slideshow-with-music.html)
 
Support adding photos & music
Provides numerous transitions & effects
Provides hundreds of amazing templates devided in 4 categories
Support adding hyperlink to photos 
Output standalone & XML-driven photo gallery
Burn auto-run CD/DVD
Upload photo gallery to Go2Album, social websites and your own website

---

### Post by celem on 2010-10-20
FYI - Given that Photo Flash Maker is a Windows only program, are you running it under WINE? If so, do all features work? Which version of Photo Flash Maker are you using - platinum, pro or free?

---

### Post by wkulecz on 2010-10-20
I've never been happy with still photos on DVD.  Image quality stinks when the photos are reduced to the 720x480 of DVD -- especially if viewed on a large screen.

Solution I like is a play list on one of those media player set top boxes like the Viewsonic VMP-70 (~$90) + the cost of a USB stick.  Will display video up to 1080p and on an HD set the photos automatically get resized to the HD display which look way better than any on a DVD.

The VMP-70 has Linux inside too!

---

### Post by LeoVince on 2010-10-20
I have been using dvdslideshow for over a year now and I am quite happy with it.

---

### Post by FYI on 2010-10-21
> **celem said:**
> FYI - Given that Photo Flash Maker is a Windows only program, are you running it under WINE? If so, do all features work? Which version of Photo Flash Maker are you using - platinum, pro or free?
 
 
Yes, I run Photo Flash Maker Platinum under WINE and it works fine so far on my linux. And just also make sure your latest version adobe flash player run in PC. 
 
:guitar:

---

### Post by qneill on 2013-01-15
> **WrathofthePenguin said:**
> How funny is this. I want to create another slideshow but couldn't remember what software I used last time. And here I find my own post that I don't even remember making...

Oh yee of little cache size.

(same with me).

---

