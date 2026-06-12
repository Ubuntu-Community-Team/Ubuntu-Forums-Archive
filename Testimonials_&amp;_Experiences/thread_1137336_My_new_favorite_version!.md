---
title: "My new favorite version!"
date: 2009-04-25
forum: Testimonials &amp; Experiences
---

### Post by TheThinker on 2009-04-25
Ah, Linux, why do I love you so much? You're not perfect; after all you're made by human beings. But I know you better than I know Windows, and I've used windows for most of my life. There's just so much freedom in you, and I trust you more so than any other OS.

Ubuntu has been a great starting point for me, and continues to be my office OS of choice. Feisty was good, Hardy was interesting, Intrepid was fine. Each one, of course, had bugs of their own, but with a little sweat and determination I overcame them. And they STAYED fixed.

Jaunty, however, is perhaps the best version yet. I use an E-Machines 2.8 ghz celeron processor, 750mb of RAM, and an Nvidia Geforce4 MX4000, which is a combination as mediocre as rice and beans. But the bootup was much faster than before, video was slick and the system performance is quicker than ever, especially when it comes to program installations. 

Other programs, whose credit should probably go towards their developers as opposed to the Ubuntu teams, made out like kings. After getting my Hercules Classic Silver webcam working with v4l (yes, it can be done), the new Ekiga's frame rate was much better. The new firefox is also a pleaser, as I found my webpages loading sooner than expected. I have yet to try the other programs such as Open Office and GIMP, but I suspect they'll be at least as wonderful as before.

Some caveats however:

1) Since Intrepid, Compiz refused to work through the appearance settings and the same applies to Jaunty as well. Fortunately, this is a bug that can easily be overcome. Install the fusion-icon application through synaptic and use that to get compiz to work, if you're confidant your video card can handle it that is. Just remember to rightclick the icon as it appears on your tray and select indirect rendering and loose bindings.

2) The black screen post-installation problem was still apparent on Jaunty this time around, although it only affected my brother's newer computer. No biggie, since you can just add a line in the device section xorg.conf file to include the vesa driver. But why VESA wasn't automatically used in that case remains a mystery to me. I assume its the sort of problem that is less common now, but it's one that shouldn't exist anyway.

3) Synaptic is slightly buggy, in the sense that when you mark programs your program list jumbles a bit. A little inconvenient. That, and your simple-search option can sometimes yield no results. The same applies to the add/remove program of your application bar. Hopefully this will be fixed with an update.

Conclusion: 
A faster system is never a bad thing! Of course, bugs are inevitable, but I continue to be impressed by the level of support the Ubuntu maintainers give out to their users. You guys rock! The same applies to all the good souls out there volunteering their free time on the forums for us noobies.

---

### Post by wolfen69 on 2009-04-25
> **TheThinker said:**
> 
3) Synaptic is slightly buggy, in the sense that when you mark programs your program list jumbles a bit. A little inconvenient. That, and your simple-search option can sometimes yield no results. The same applies to the add/remove program of your application bar. Hopefully this will be fixed with an update.


i've never experienced any issues with synaptic. why not use the regular search function? anyway, glad to hear you like it.

---

### Post by ScottBurnham on 2009-04-25
Jaunty is my favourite so far, hats off to the Ubuntu staff for a great release and hoping that one day Linux will be a major contender in the desktop OS market.

---

### Post by 3rdalbum on 2009-04-25
The simple search bar will only search items in the right pane. If you've already got a filter selected, or you've done a "normal" search, then the simple search bar will only search those results.

That's caught me out a couple of times too.

---

### Post by TheThinker on 2009-04-26
Thanks 3rdalbum. I just figured that out recently. It's not a major hinderance of course. I guess I'm a stickler for details.

Putting aside the VESA issue, I think I understand why the Compiz problem remained. From my own investigation, Compiz seems to think that I am currently using my Intel graphics chip when in fact I use the Nvidia card, and many newer computers these days don't have more than one graphics chip anyway. Fusion-icon avoids this altogether. It's possible that a boot function of Compiz, this "blacklist" I'm reading about, is the culprit. Perhaps an update will fix this, so that more novice users than myself could avoid the confusion.

Other than that, I'm solid. :)

---

### Post by nimajiman on 2009-05-06
> 1) Since Intrepid, Compiz refused to work through the appearance settings and the same applies to Jaunty as well. Fortunately, this is a bug that can easily be overcome. Install the fusion-icon application through synaptic and use that to get compiz to work, if you're confidant your video card can handle it that is. Just remember to rightclick the icon as it appears on your tray and select indirect rendering and loose bindings.

Just a question for you - why do you suggest to tick indirect rendering and loose bindings? I'm just not sure what these terms mean. Compiz seems to work for me whether they are ticked or not. Is there an advantage to having these options selected?

Cheers

---

### Post by TheThinker on 2009-05-07
nimajiman:

Well, I recommend loose bindings and indirect rendering because they're safe-mode options for people unsure whether their graphics card will handle compiz at all and wish to avoid black windows or sluggish performance at the first onset. See here:

[http://wiki.opencompositing.org/Troubleshooting](http://wiki.opencompositing.org/Troubleshooting)

That wiki mentions indirect rendering and loose bindings in more detail.

---

### Post by nimajiman on 2009-05-09
Thanks!

---

