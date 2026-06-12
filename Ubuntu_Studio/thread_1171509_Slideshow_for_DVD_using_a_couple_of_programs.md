---
title: "Slideshow for DVD using a couple of programs"
date: 2009-05-27
forum: Ubuntu Studio
---

### Post by reiki on 2009-05-27
Well in my quest to make a DVD slideshow for my father-in-law's wake...

The EASIEST way I've found to do this requires the use of a couple of programs. Part of my dilemma was that I wanted to mix photos and some video clips from old home movies we had transferred to a DVD a couple years ago. 

I installed [JSlideshow]("http://jslideshow.sourceforge.net/") which was really quite easy. It handles individual images quite nicely and has several kinds of transitions, control over timing, and even has the ability to add a soundtrack.  For a simple, photos-only kind of slideshow, this might be all you need. It saves as both AVI and VOB at the same time. 

I also installed a program called [Imagination]("http://ubuntuforums.org/showthread.php?t=1047150") and I am VERY impressed with where this new app appears to be going. Very polished appearance. LOTS of transitions between slides. I can't add video clips to it or add a sound track (yet), but this is a very new app and I have great hopes for its continued development. When I installed it, I used checkinstall to create a deb only to later find out that the deb was already created by someone else (in that thread linked above). This will take a slide show and export it as a VOB or FLV.

I also installed dvdrip (in the repos) to get the video clips off that dvd we had created years earlier.

Also install Open Movie Editor (found in Add/Remove in Jaunty).

Quite a collection of apps. :)

So I have a directory of photos, a directory of videos and several apps. It took a little planning and playing around, but...

Used Imagination to create a slide show. Actually several slideshows eventually. I created and saved one big "master" slide show of photos. 

THEN I decided where I wanted to insert video. I then deleted all slides AFTER that first video location and saved the first group of slides as photos1. Reload the master file, decide placement of NEXT video segment, kept only the files between the 2 video segments, saved as photos2, etc. Basically used teh locations of where I wanted to insert video to decide where to create slideshow segments.

Now I used Open Movie Editor to assemble the DVD by bringing in each video segment. The photo slideshow segments were exported as VOB files, bring in a slideshow segment, bring in a video clip, another slideshow segment, another video clip... and so on until done.

The transitions in Imagination are at the beginning of each slide. So.... how it transitions IN.. there is no way to transition OUT. This looked a bit choppy when transitioning from a slideshow segment to a video segment and I couldn't find a way to transition between video segments in Open Movie Editor. So I created a blank image with a black background (depending on what you're doing a different background color might work better) and I TRANSITIONED to a black screen and only held the slide for 1 second at the END of a slideshow segment. 

So... I got it done using linux apps and not windows apps. This is the kind of stuff that needs to be easier in linux. This is what people want to do to be creative. I think Imagination has great potential as the building block upon which to add features. 

By comparison, my wife has Vista Ultimate on her laptop. She can open DVD Maker (part of standard install) and drag groups of photos to it, rearrange teh order easily, insert videos, preview it... and hit a button that says, "Burn".   How much easier can it get?  We need that kind of functionality in linux. :)  It can't just be good.... we know it's a better OS... it has to also be fun. :)

Anyways... just one person's way of skinning a cat. Hope it helps someone trying to accomplish something similar.

---

### Post by cotcot on 2009-05-27
Have you tried SMILE (it is the successor of mandvd) ?

---

### Post by reiki on 2009-05-27
I looked at SMILE, but it was all in French and I can't read French. I didn't install it as it appears to be a KDE app and I wasn't sure I could compile it in Gnome without adding a ton of extra libs. If there is a deb for it, I would certainly try it.

---

### Post by LostInBrittany on 2009-06-01
> **reiki said:**
> I looked at SMILE, but it was all in French and I can't read French. I didn't install it as it appears to be a KDE app and I wasn't sure I could compile it in Gnome without adding a ton of extra libs. If there is a deb for it, I would certainly try it.

There is a .deb for it, in its official site :
[http://smile.tuxfamily.org/?q=node/2](http://smile.tuxfamily.org/?q=node/2)

I would suggest you to try it, it's a good piece of software. I've found it very useful (even if it's in French ;) )

---

### Post by reiki on 2009-06-01
> **LostInBrittany said:**
> There is a .deb for it, in its official site :
[http://smile.tuxfamily.org/?q=node/2](http://smile.tuxfamily.org/?q=node/2)

I would suggest you to try it, it's a good piece of software. I've found it very useful (even if it's in French ;) )

Cool!  I didn't find the .deb before. I will definitely give this a look.  Thanks!:D

---

### Post by reiki on 2009-06-02
OK I tried SMILE. I wish there was more English documentation as it looks like it could be a nice program. I ran into a couple of issues:
1.) Opened "Documentation" and it was blank. AND it had no way to CLOSE the window that opened.
2.) There's only 1 transition.... crossfade. How do I get more transitions?
3.) Tried to add a video as a slide and the program hung. Looks like it only imports AVI files which is OK if tehy actually work.

---

