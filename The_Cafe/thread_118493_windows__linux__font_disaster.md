---
title: "windows / linux / font disaster"
date: 2006-01-17
forum: The Cafe
---

### Post by borisattva on 2006-01-17
about 7 years ago i was trying storm linux and mandrake, i succesfully installed them, and was intrigued by browsing this new medium, untill i went on the web and could not read anything because fonts were displayed microscopically.

there was no solution at the time so i just removed it without a second thought

installing ubuntu i was happy to see that all web pages are readable,
i was a little surprised taht everything looks slightly different than on a windows or mac browser, but it was readable and did not screw up the page lay out.

i just installed xp core fonts onto ubuntu and surprised to find out that

firstly, they dont look in linux as they do in windows - why?

secondly, typing anywhere that is bound to be viewed across differnet platfroms
(like an away message in AIM) the sizing is AGAIN screwed up.

typing in seemingly regular size Arial font in Gaim, all my windows-borne friends see fone dispalyed about 2 times as big.

and if i downsize mine to appear normal on their screens, its practically unreadable on my side.

How could have this sizing mess could have come to be ?
as it obvisouly had its roots in earliest forms of linux.

Why isnt there something being done to standardize things to look uniform across platforms?

---

### Post by tkjacobsen on 2006-01-17
you should install msttcorefonts. This can be done from with apt-get

---

### Post by 23meg on 2006-01-17
> firstly, they dont look in linux as they do in windows - why?Because they're rendered by a different font rendering engine, namely [Freetype 2]("http://www.freetype.org/freetype2/index.html").
> typing in seemingly regular size Arial font in Gaim, all my windows-borne friends see fone dispalyed about 2 times as big.This sounds like a problem with the protocol you're using, or its implementation, rather than a font rendering problem; does it only happen with AIM? Has anyone else experienced this?

---

### Post by borisattva on 2006-01-17
tgk: i did. but i installed them via the HOW to walkthrough in the tips and tricks section which consisted of copyingFonts fodler from my XP install into /msttcorefonts (which i had to manually create)

[QUOTE=23meg]Because they're rendered by a different font rendering engine, namely [Freetype 2]("http://www.freetype.org/freetype2/index.html").
This sounds like a problem with the protocol you're using, or its implementation, rather than a font rendering problem; does it only happen with AIM? Has anyone else experienced this?[/QUOTE]
i can only test it via aim as other methods like gmail seem to automatically adjust to their defaults.

i just did an apt-get of the fonts and reloaded gaim to refresh its font awareness this is what i get still
text sent as(through linux):[IMG]http://www.borisattva.com/freq/sentas.png[/IMG]
received as(in windows):[IMG]http://www.borisattva.com/freq/receivedas.bmp[/IMG]

Is there any (legal?) reason that FreeType cant render core fonts to display as their designers intended them?

---

### Post by 23meg on 2006-01-17
I'm puzzled about your IM problem; maybe it's about the way relative font sizes are set in the apps you're using, but definitely doesn't look like a Freetype problem.
> 
Is there any (legal?) reason that FreeType cant render core fonts to display as their designers intended them?Not that I know of; the autohinter module is licensed by Apple, but using non-licensed hinting with it removes that restriction. Try giving it a go by doing ```
sudo dpkg-reconfigure fontconfig
```

---

### Post by prizrak on 2006-01-17
That gotta be the weirdest problem ever, I never had that happen. ::confused::

---

### Post by Vlammetje on 2006-01-17
I can't say I've had that happen on any IM engines so far.... but I must admit I have not used AIM in a very, very long time.

I am curious though, is it only AIM?? being AOL and all.... :rolleyes:

---

### Post by prizrak on 2006-01-17
23meg, awesome command, I been looking for something like that since for some reason I couldn't get the fonts to render as I wanted them (they looked fine but I'm real picky)

---

### Post by borisattva on 2006-01-17
heres an update. thansk for that command 23megs, it seems to have made things slightly better in the beginign but when i tried to adjust it in Gaim, the proeblm came back. 
its possible that its rooted from the fact taht Gaim doenst have a reset to default sizes buttong like in regular Aim.
but i also noted that all regular webpages like google are affected by the new fonts.. it appears that characters themselves are ok. but they are bucnhed together closer, squeeshed.

pages with specific fonts like ubuntuforums are fine, but others taht are meant to rely on defaults are all affected and look bad.

i'm surprised that i'm the only one having this problem as it followed me through a number of distros on a number of computers, with no fancy tweaking on my parts. just out of the box this would be the problem.

also in reconfiging of the font i used a default NO for bitmapsed fonts.. i read the epxlanation but am not certain i understand it in the context. if someone could explain the benefit/downside of bitmap fonts in the config portion id appreciate it.

---

