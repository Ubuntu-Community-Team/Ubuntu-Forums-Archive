---
title: "Video capture and editing on Linux"
date: 2010-05-31
forum: The Cafe
---

### Post by Rhapsody on 2010-05-31
This isn't a tech support thread, my webcam problems (which you may have seen) have been solved and my webcam now outputs excellent video and audio. My problem now is the software side.

For capture from the webcam, I'm using Cheese, which is simple and easy to use. But it only outputs video into Theora (which I'm not convinced is the best option, with 60 second 640x480 videos coming out at 50MB). I also gave VLC a go, but that seemed ridiculously esoteric and eventually failed to find its own H.264 encoder. What do people on Linux who make actual use of their webcam use? Is Cheese the best option or am I missing something?

Going outside that, it would also be nice to capture all or part of my desktop (mostly for video gaming demos using my 9001 assorted games) and maybe other purposes, but I'm not sure where to start there.

Then after all that is editing the videos, cutting stuff together and adding effects. I'm guessing this will be hard, with many YouTubers I watch using proprietary tools that I'd prefer to only go to as a last resort.

So. Camera capture, desktop capture, and editing. There must be other Linux users who do these things, and I'm hoping some are here. What are your suggestions? My first preference would be to things in the Debian repository (as I now use Debian testing), but I'm not averse to external repositories that can co-exist with Debian's (and Debian-Multimedia's), compiling software (as long as it's a sane process and actually tells me what dependencies it has), and I could even use Windows software in Wine or VirtualBox if there's really no other way.

I've got plenty of space, powerful hardware, and a pretty high quality webcam, but I need the software now. Suggestions, please?

---

### Post by quinnten83 on 2010-05-31
Asking about video editing in Linux is like cursing in church.
well, here goes
video capture: Istanbul, gtk-rrecord my desktop.I dunno how well they work with videogames thouhg.
Capture, I know that kino can do some video capture, but it does everything in DV format, so I dunno if it will work with you webcam.
good editors are IMHO openshot, very easy to use and understand and kdenlive, a bit more complex, a hell of a lot buggy, but lots of options. Cinelerra is almost professional grade, butt hard to setup and understand. Check the repos or google for video.
you can capture in one format and use a video converter to transfer into another format.

---

### Post by purelinuxuser on 2010-05-31
+1 for Kdenlive.  Best Linux video editing software in my experience.  It has a reputation for being buggy but has actually become quite stable in recent versions.  It has editing and recording from webcam built right in! :)

Only downside is you'll have to install a bunch of KDE libs if you don't have Kubuntu.  There will be some apps installed too but I've found you're able to remove some of them. ;)

---

### Post by madjr on 2010-06-01
good video

[http://www.youtube.com/watch?v=2ohKkEK280w&feature=related](http://www.youtube.com/watch?v=2ohKkEK280w&feature=related)

---

### Post by LeifAndersen on 2010-06-01
I also am having this issue.  I would like to capture video from my webcam (or dv based camcorder), and my desktop at the same time, I would also like to change the layout of that on demand (aka, when there is nothing interesting on my desktop, go to a full shot of me, and vice versa), I would also like to livestream it, but that's not necessary.

I know webcam studio for GNU/Linux does most of that, but it falls short when I want to change the whole layout of the windows on the fly (aka, have several set up in advanced, and switch to them with the click of a button), also, it may just be my hardware, but it seems more choppy than other video recording solutions.

Editing isn't a big problem, I generally use FFMpeg and blender.  Maybe, I should make a new thread for this?

---

### Post by SunnyRabbiera on 2010-06-01
Kdenlive, openshot and pitivi might bee good options

---

### Post by Linuxforall on 2010-06-01
For video editing, Open shot is the best around in Linux world and comes quite close to Premiere.

---

### Post by madjr on 2010-06-01
> **LeifAndersen said:**
> I also am having this issue.  I would like to capture video from my webcam (or dv based camcorder), and my desktop at the same time, I would also like to change the layout of that on demand (aka, when there is nothing interesting on my desktop, go to a full shot of me, and vice versa), I would also like to livestream it, but that's not necessary.

I know webcam studio for GNU/Linux does most of that, but it falls short when I want to change the whole layout of the windows on the fly (aka, have several set up in advanced, and switch to them with the click of a button), also, it may just be my hardware, but it seems more choppy than other video recording solutions.

Editing isn't a big problem, I generally use FFMpeg and blender.  Maybe, I should make a new thread for this?

you mean like this:

[http://www.youtube.com/watch?v=yLx4LiMtM4Y](http://www.youtube.com/watch?v=yLx4LiMtM4Y)

[http://www.youtube.com/watch?v=7QDEJ-9X4Ws](http://www.youtube.com/watch?v=7QDEJ-9X4Ws)

---

### Post by LeifAndersen on 2010-06-01
Almost.  That just popped up a new view with every window, and he just zoomed in on a window with compiz.  Imagine that I had 4 views pre-built before the video started, associated with the keys 1,2,3,4 (well, maybe not those keys, but ones I wouldn't use), when I hit 1, the picture changed to just my webcam, when I hit 2, it showed a zommed in picture of my desktop, when I hit 3, it showed my full desktop, and when I hit 4, it would show a split screen of me with my desktop.  Eventually, I would like to add a 5th option to capture two webcams, but I don't need that now.

(Also, I would like the windows to tile, but that's not too big of a deal, as I can set that up before hand).

---

