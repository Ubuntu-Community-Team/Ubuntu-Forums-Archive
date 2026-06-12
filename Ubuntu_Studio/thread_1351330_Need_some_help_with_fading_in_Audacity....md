---
title: "Need some help with fading in Audacity..."
date: 2009-12-10
forum: Ubuntu Studio
---

### Post by Inane_Asylum on 2009-12-10
I'm bought a karaoke track for Man of Constant Sorrow without realizing it was one with background vocals.  All I wanted was the instruments.  Not wanting to get another, I figured I could use Audacity to gloss over the background segments, and have done fairly well, with one exception.  There's a part at the very beginning when the background comes in pretty strong.  With the rest of it, I was able to copy the segment of song that was most similar to the part where they sing and replace the singing where needed.  The part I'm stuck on is during the intro, so it's quite a bit different than the rest of the song, and my previous method didn't work too well.  So I tried deleting it altogether, just skipping the singing part, but that was even worse.

What I need to know is, would there be a way to delete **most** of the singing part, then do a kind of fade from the beginning part into the end part to make a smoother transition?

Am I making any sense? 8-[

---

### Post by ajgreeny on 2009-12-10
Complete sense!  Load the file into audacity and just highlight the length of time you want the fadeout to take from the start of the offending vocals.  Go to Effects -> Fade out and the fade will appear on the file graphics.  Now do the same in reverse from the point in the file you want the fade in to occur, but work backwards and choose Fade in.  You will now have a file with a fade out, fade in and then a loud part still left in the middle, which you can highlight and delete.  Easy to do and very effective.

I have just thought, however, that the effects you need may be in either the **tap-plugins** or the **swh-plugins**, which you may need to install, but I think they are within audacity itself, so you may not need them for this.  Have a look at them, however, as there are some good reverb and echo and other more complicated effects you can get from them.  Both are in the repos along with other ladspa plugin packages.

Audacity is really top gear stuff, isn't it?  I use it a lot.

---

### Post by Inane_Asylum on 2009-12-10
Thanks a lot, aj, I'll check that out.  I got pretty good results from grabbing a chunk of the song that would work, putting it on a separate track, adjusting it to where it should go, then using envelope to fade out of the lyrics while fading in to the blank music, then back again afterwards.  It's not too bad, but I'll play around with those other settings to see if I can get better results.  This is my first time using Audacity, and I have to say it's a very admirable piece of software.  I wish I were using it on something other than a first-gen eee 900 :-/

---

