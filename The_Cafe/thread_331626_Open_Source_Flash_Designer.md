---
title: "Open Source Flash Designer?"
date: 2007-01-04
forum: The Cafe
---

### Post by Johnsie on 2007-01-04
Is there any program for Linux that ypu can use to make flash websites?

---

### Post by jpeddicord on 2007-01-04
[http://freshmeat.net/projects/f4l/](http://freshmeat.net/projects/f4l/) is one of the few I have found, although there hasn't been much progress on it since late 2005.

---

### Post by Johnsie on 2007-01-04
Thanks, I'll check that project out. I'm not a big fan of the whole closed idea of flash but when you work in web development sometimes you need it.  BTW, I bet you can't eat more than 4 jacobs cream crackers in a minute(with no drinks)! :-)

---

### Post by maniacmusician on 2007-01-04
> **Johnsie said:**
> Thanks, I'll check that project out. I'm not a big fan of the whole closed idea of flash but when you work in web development sometimes you need it.  BTW, I bet you can't eat more than 4 jacobs cream crackers in a minute(with no drinks)! :-)
Please don't make a flash website...they're the most horrid implementation of technology I've seen in a little while. There are better ways!

---

### Post by Johnsie on 2007-01-05
Tell me these better ways.... I need to make a professional, artistic looking website for a photographer that allows people to see a presentation of his work. Html/css dont really provide the special effects and eye/ear candy that flash can provide

---

### Post by 3rdalbum on 2007-01-05
HTML, Javascript, CSS, and SVG can, but I'll admit that there's no good Flash-like tool for doing that sort of stuff in open standards.

You probably won't find F4L to be satisfactory, at all, unfortunately.

At least make sure you make your movie Flash 7 compatible for the Gnash-folks :-)

---

### Post by Magnes on 2007-01-05
Use JavaScript.

---

### Post by Tomosaur on 2007-01-05
Flash websites are irritating not because they're flash, but because flash designers are often terrible. You may want to do some serious reading on the psychology of websites, it's very eye opening. People tend to not read websites, they just skim around for interesting words, unless the article in question is directly relevant to their interests. The problem with Flash technology is that it generally slows this process down through animations and such. A well designed Flash site can be a great piece of work and in portfolio websites, it can make all the difference. However - you need to remember that people don't care about how the website looks - they want to see the photographs. You should make every effort to present the photographs in an easy to access manner, in a way which makes them look good. Your problem is finding the best way to do this. Flash may be overkill - a good CSS design can be faster and also look great - it just may take you a bit more fiddling to get cross-browser support working properly. Your best bet is to make a number of different designs using different techniques: Flash, HTML/CSS, maybe even some cgi stuff, then ask the photographer which he/she thinks is the best.

---

### Post by %hMa@?b&lt;C on 2007-01-20
tell me if some of these are not "eye candy" enough. Believe me, use CSS, get good at CSS
[http://csszengarden.com/](http://csszengarden.com/)

---

### Post by Hex_Mandos on 2007-01-20
Flash is slow, heavy, closed (not just closed source, I also cannot look at the HTML source and see what it does, or copy/paste text from a flash applet) and is often used as a crutch by designers with poor skills. I tend to avoid Flash as much as possible, but I keep the Flash plugin installed to watch videos and stuff.

Flash HAS some good uses (as I said, I like watching videos on youtube/dailymotion/etc), but most designers use it poorly and in excess. IMO, it should be used only as a last resource, to avoid excessively blingy sites in terrible taste. Believe it or not, non-developers like me sometimes read the page source, and like to see everything in the open. 90% of the people who use Flash should first learn to code.

In the case of images, you should be careful: I'd rather be able to download a watermarked picture than having to load a heavy Flash site every time I want to see them or show them to someone else.

(For the record, I don't hate Flash as a technology... I love [LocoArts]("http://www.locoarts.com.ar"), which is both a great and a terrible implementation of Flash: it's the home to a GREAT animated series made in Flash, but the website design is terrible)

---

### Post by charasoverride on 2008-10-01
> **Hex_Mandos said:**
> Flash is slow, heavy, closed (not just closed source, I also cannot look at the HTML source and see what it does, or copy/paste text from a flash applet) and is often used as a crutch by designers with poor skills. I tend to avoid Flash as much as possible, but I keep the Flash plugin installed to watch videos and stuff.

In my opinion, flash is not really closed source.. there are tons of applications to decompile and they make a good job..
About the skills, i would not blame other's skills, its not them who will make my website.. actionscript is powerfull and does a good job on developing animations, it can make your site very light and atractive.. it depends on one's skill.. I like actionscript and trust me, i made good animations in flash which i could not think of with css.. of course, use it in combination with other technologies, PHP, javascript..

cheers

---

### Post by geoken on 2008-10-01
Any text editor + Open Source Flex compiler = Free, open source tool for Flash design.

If the site needs a lot of graphics you can throw inkscape into the mix (the flex compiler is able to embed svg objects and use them as graphical assets).

---

### Post by delfick on 2008-10-01
your not gonna get an ide in linux (unless you're willing to put up with the flash ide under wine (personally I'm not sure about cs3, but flash8 ide does work on wine, just rather slowly)

however, as mentioned above, a text editor + adobe flex works nicely for creating flash applications

though for the site itself, html, css, svg, etc :)


as for how to use flex in linux
[http://ubuntuforums.org/showthread.php?t=742981](http://ubuntuforums.org/showthread.php?t=742981)

and if you don't like gvim, you can use gedit with 
* [these lang files ](http://code.google.com/p/flashbsm/source/browse/testing/language-specs) in ~/.local/share/gtksourceview-2.0/language-specs
* [this plugin](http://code.launchpad.net/~delfick/vigedit/vigedit-additions) to make gedit become a modal text editor like vim (personally, I like the editing capability of a modal text editor, but gedit takes up way less memory than gvim and seems faster)
* and the filebrowser plugin that comes  by default with gedit.

:)

---

### Post by hessiess on 2008-10-01
personaly, eyecandy = avoid.

---

### Post by CamNZ on 2009-01-16
I want to create an online game as an illustration/simulator of how a complicated financial service operates. I was thinking a flash based game. What are my options wrt Ubuntu open source software to create said simulator?

---

### Post by SpyMasterMatt on 2009-02-24
I am a flash designer and agree that flash can be heavy in webpages and often poorly or over used by people keen to show off their abilities rather than acheive the website's aim. However, correctly used, flash can be incredibly effective and is an easy way of creating advanced animations very quickly. It is a shame about flash being closed source however. 

Could somebody create a GUI (with various animation and drawing tools) that uses javascript instead of actionscript to give flash designers the ease of use they are after, whilst remaining in the open-source domain? After all, anyone who uses javascript and actionscript can see that for the most part they are virtually identical.
Just a thought.

---

