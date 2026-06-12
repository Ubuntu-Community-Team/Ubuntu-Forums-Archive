---
title: "I want to make a NICE slideshow with kdenlive, but am having technical problems"
date: 2009-05-09
forum: Ubuntu Studio
---

### Post by diablo75 on 2009-05-09
I've been playing around with kdenlive lately and I used it recently to make a slide show.  I did this by filling a folder with photos and renaming them so they would be sorted by alphabetical order into the order I wanted them to appear in the slideshow.  Then in kdenlive, I would add a "Slideshow Clip", select the folder, set my duration for all slides, tell it to add a transition, and that was pretty much it.

But when I rendered it, I ran into some trouble:

For starts, the transitions (a fade with no luma selected) only seemed to be applied between a small handful of slides, out of over a hundred.  In other words, most transitions were *snap* instant and not a fade of any sort.  And the ones that did fade did not respect the transition duration I had selected (about 2 seconds).  Finally, some slides would be brought into the slide show out of order.  I had to split the source image folder into three separate folders, then import each one as separate slideshow clips and put them all together on the time line.  Another reason I had to do this was on the very first render, only about half the pictures were rendered, and the last half of the video was solid black with the background music playing for 8 minutes or so.  After splitting the images up into separate folders and rendering again, the very last slide that was suppose to show up didn't, and instead it looked like the next to last slide just moved up slightly to reveal the previous slide under it which looked like a glitch to me.

What I'm wondering is if anyone might know why the transitions didn't hold for most of the slide show and if there is a way to fix that.

---

### Post by suda on 2009-05-10
I don't have an answer to your question, but I too am using Kdenlive with the new Jaunty/64 bit. Kdenlive is the only video editor I've found that can do the work I want, but I'm having a problem understanding how Slide Show works. There is no user manual. My next step is to join one of the Kdenlive forums. I understand from what you wrote that you set up a folder with your .jpg images, but how did you get Slide Show to work with this folder? I don't see any way to "select" or "open" in order to create a slide show.

---

### Post by diablo75 on 2009-05-11
After fiddling with kdenlive, I've actually discovered through a little practice that it is VERY easy to make a much more manageable slideshow via just adding the pictures as clips into a folder, and adding them to the time line one at a time.  I know, that sounds very tedious, but you know what?  Compared to the trouble I've had (and I mean this sincerely, not "seriously") it's more my flavor.  I mean, there are parts of the slide show that you actually want to have more flexibility over; not have every single one on the same duration and same length of transition.  It's fun to shake it up if you can.  And in just about an hour and a half I completed a slideshow last night with about 130 slides.  I had no idea it was so easy to add transitions...

Drag picture to line one.
Drag next picture to line two and overlap where you want the transition.
Click on that "Insert Transition" button.

THAT was IT!  (If I didn't want a custom luma, and in most cases, I don't; a plane fade is perfect for most pictures).

Then you add a third picture back on line 1, overlapping with the pic on line 2 for another transition, and click on the add transition button on line one *(again, and it usually doesn't actually "appear" on the screen, you have to watch your cursor to turn into that "pointing finger" cursor so you know your on the right spot before clicking*).  And that was all you needed to add another transition.

I was literally laying down one picture every 10 seconds at one point.  I'm much happier with the way thing went the second time around.  I tried the slideshow clip thing the first time around because I was in a hurry and though I'd save time.  Boy was I wrong.
:guitar:

Edit:  I just wanted to also mention the "Spacer Tool" (button on the bottom bar) was a huge helper (it's the only way I know how to insert a space in the middle of a whole composition and have it move all elements on the time line for you; transitions included).

---

### Post by suda on 2009-05-17
Diablo, thank you so much! Ironically, what you do is what I ended up doing, sort of. I put each pix on a separate line, never going back up to line 1, then back down to line 2, and up again as you do. I'll try that. Also, I don't know much about that Spacer Tool. I don't quite understand its function. I'll play with that too. I wish Kdenlive had its manual put together. :-)

---

### Post by cotcot on 2009-05-17
If you do not get out with kdenlive you could have a look at [[COLOR="Blue"]smile[/COLOR]]("http://linux.softpedia.com/get/Multimedia/Graphics/SMILE-38844.shtml") .

---

