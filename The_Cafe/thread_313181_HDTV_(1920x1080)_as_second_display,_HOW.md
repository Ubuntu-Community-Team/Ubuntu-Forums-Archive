---
title: "HDTV (1920x1080) as second display, HOW?"
date: 2006-12-05
forum: The Cafe
---

### Post by isync on 2006-12-05
I'd like to add another display to my system - in this case a HDTV display in the resolution of 1920x1080 pixels (for HD video editing).

Now, how do I do it and what is the best way to do it?
Can I add another screen via the second connector of my graphics card (I've got an GeForce 6150) or will I have to add another card just to feed the HDTV?) Will I just use an DVI to HDMI adaptor cable or should I option for something else?

How will my workspace be organized? Will one screen start where the other one ends or can I switch with the workspace-selector on the panel?

Any ideas, advises etc. welcome!

---

### Post by RandomJoe on 2006-12-05
I can't address the specifics of hooking up the TV, I don't have any HD stuff yet.  But I run dual screens all the time, including one machine that runs a regular flat panel and a 720x480 projector for watching movies.

You can set the screens up just about any way you want.  Using Xinerama or nVidia's TwinView (think that's it) you can make the two effectively one continuous desktop (you can move windows between them, or even split across them) but I had trouble with some apps that ran fullscreen starting spanned completely across both.  I recently found an option to add to fix that though, but haven't tried it yet.

Or you can set each screen up as an independent desktop (what I usually do) - you'll get a menubar across each screen, which can then be customized to each screen (they don't have to be identical) and whichever screen you start an app on, that's the one it runs on.

The screens can be set (via xorg.conf statements) to be left-of, right-of, above or below each other.  So you can hang the TV on the wall over your other monitor! :)

---

### Post by isync on 2006-12-06
Thanks for the hints!

Still the question:
will I need another graphics card or will my DVI+VGA output nVidia do it, even if one screen runs in 1024x78@75Hz and the HDTV will (probably) run in 1920x1080@50Hz... Where are the technical limits? Buying another card is no problem, I just need to know...

---

### Post by Aetherius on 2006-12-06
don't think you'd need a new card, I set up my (nonHD)TV as a second screen very simply, but that was using the s-video out my geforce. Seperate X sessions on each screen seem to cause the least hassle in my experience

---

### Post by RandomJoe on 2006-12-06
I think the only issue you will have is whether your card has enough memory to handle the resolutions.  I have several computers I've run dual-head off a "single" video card, using the two outputs as you describe.  There may be a few (cheaper) cards around that can't handle that, but all the nVidia cards I've bought have said they would.

One other nuisance may be modelines.  My projector evidently doesn't report its capabilities properly / correctly (or maybe it's just that X doesn't know about that resolution?) - by default X comes up with some wierd resolutions to try to drive it.  I had to search around to find some modelines someone else had come up with to get it working correctly.

---

### Post by icemanblues on 2007-08-31
Apologies on cross-posting, but I think this is the better thread.
[http://ubuntuforums.org/showthread.php?t=539165](http://ubuntuforums.org/showthread.php?t=539165)

So I just bought a HDTV that's 1080p (1920x1080). However, I'm having difficulty getting ubuntu to recognize it as a second display.

I'm running Ubuntu 7.04 on a dell laptop with the integrated Intel graphics display. My xorg.conf uses the i810 device.

When I configured the two heads of the video card to clone one screen to the other, the HDTV says Mode Not Supported. This disappoints me because I want to use this tv as a big screen for movies.

I've also used Xinerama for the dual screen approach, but the resolution on the HDTV looks like something a bobo would use. Its way too small, can't even fit a full terminal window on it.

I guess what I am looking for is to have all of ubuntu running on the HDTV. The laptop doesn't have to be on. Maybe I can give the HDTV its own instance of ubuntu, with panels, etc?

Tell me more about how I can set up distinct X sessions on each monitor, and how to configure the modelines (ugh).

I'm sure I'm not the first to have these difficulties, but I was unable to find any helpful links via google. If you know of any, please reply. And if it helps, I can post the relevant snippets from the xorg.conf file.

---

