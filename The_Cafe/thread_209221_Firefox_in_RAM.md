---
title: "Firefox in RAM"
date: 2006-07-04
forum: The Cafe
---

### Post by compwiz18 on 2006-07-04
Today I was bored, so I made a ext2 partition and mounted it in RAM, and then I proceeded to install Firefox on it, hoping for a dramatic speed boost :D in loading times, so that when I click the icon on the panel, it would be there.  Didn't help that.  However, my surfing seems to have gotten faster... although I didn't time it.  I guess I'll keep it, simply cause it seems snappier.  And that's what matters, right?  Not sure why that would be though... If someone is interested, and wants to try this, I can post instructions on how to do this...EDIT: Did that, it's close to the bottom of the page.

I'm just curious if anyone else has tried anything similar to this or has any comments about it.

---

### Post by 23meg on 2006-07-04
I tried the same back when I was using Warty and things were very slow for me. I had just about the same experience as you.

---

### Post by K.Mandla on 2006-07-04
Would you mind explaining how this is done, step-by-step (or perhaps a link)? I have an older machine that might benefit from this.

---

### Post by compwiz18 on 2006-07-04
Sure.  So I basically used [this site]("http://www.vanemery.com/Linux/Ramdisk/ramdisk.html"), except where it asked the size.  You should put 32000 instead of 16000 in there.  After you have created and mounted the disk (it should show up in the file manager, Nautilus), I took the Firefox (or in my case, Swiftfox) installation folder (I can't tell you where the Firefox one is, the Swiftfox one is in /opt/swiftfox) and copied the entire thing onto the disk.  If you want to do this at every boot (the RAM is deleted every time you turn the computer off), write a script to copy the installation folder to the ram disk on boot (in my link is instructions on how to do it at boot - follow these, they seem to work well).  I checked, and it *appears* that the Firefox profile/history/stuff is kept on in your home folder, so you will save your settings even though the RAM is deleted.  Don't know this for sure, but that was my analysis.  Anyway, if you are having trouble copying the Firefox folder, I would highly recommend Swiftfox.  ([http://www.getswiftfox.org](http://www.getswiftfox.org), I believe - if not, Google swiftfox)  It is a bit faster :D

Hope that helps.  If you have questions, post away :D

---

### Post by K.Mandla on 2006-07-04
Thanks, I'll try it when I get home. Cheers.

---

### Post by compwiz18 on 2006-07-05
Tell me how it works out :D

---

### Post by K.Mandla on 2006-07-05
Well, I'm a bit surprised. I think I got the same results you describe -- still slow to load, but quicker while in action. I expected different, and to be honest, I'm not sure it's worth the trouble setting it up. Even on an old machine, Swiftfox still has that Firefox-esque lag at start, but snappy performance otherwise.

It was a good learning experience, though. That's definitely something I can come back and use in the future. Thanks for the tips.

---

### Post by compwiz18 on 2006-07-05
That's pretty much how I felt - not sure it was worth setting up, but since I did, might as well keep it.

---

### Post by UbuWu on 2006-07-06
You might be interested in the preload package from the repositories, it might give better results. I haven't tried it myself yet though.

---

### Post by K.Mandla on 2006-07-06
I *think* I had preload installed, but I'm not sure (I've since rebuilt that machine). That probably would have helped with the startup lag. I might try it again, just out of curiosity.

---

