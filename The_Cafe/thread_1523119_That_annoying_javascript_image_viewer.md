---
title: "That annoying javascript image viewer"
date: 2010-07-03
forum: The Cafe
---

### Post by spupy on 2010-07-03
Ubuntu forums is one of the culprits. I'm talking about the annoying javascript (?) where I middle-click images to load them in a new tab while I keep browsing, but NOOOO, they need to open in the current tab, obscuring everything else I'm viewing.

Please, is there some greasymonkey/chromium script that disables this? My google-fu was ineffective.

/rant

---

### Post by robsoles on 2010-07-03
Hey spupy, would you please link to one of *those* images here on ubuntuforums.org?

I came across one in a thread somewhere but I'm not sure it had the behavior your speak of and I want to test stuff about it before I go saying what I think you can do about it.

---

### Post by Yarui on 2010-07-03
Well if what you are talking about is a link that uses javascript when you click on it instead of an http link, you can't really do anything to load those in a new tab.  Javascript runs on the current page, if you open it in a new tab, the new tab goes to a blank page and tries to run the javascript, which doesn't exist.  The only way to open it in a new tab is just to open a new tab with your current page and then click on it there.  I agree that javascript links that can't be opened in a new tab are really annoying.

---

### Post by BenAshton24 on 2010-07-03
Middle clicking opens the image in a new tab with Firefox.

---

### Post by spupy on 2010-07-03
> **Yarui said:**
> Well if what you are talking about is a link that uses javascript when you click on it instead of an http link, you can't really do anything to load those in a new tab.  Javascript runs on the current page, if you open it in a new tab, the new tab goes to a blank page and tries to run the javascript, which doesn't exist.  The only way to open it in a new tab is just to open a new tab with your current page and then click on it there.  I agree that javascript links that can't be opened in a new tab are really annoying.

The thing is that middle-click triggers the javascript, as if left-click was issued. "Context-menu -> open in new tab" works.

I just don't like websites messing with the controls.

And here is a link with lots of images:
[http://ubuntuforums.org/showthread.php?t=1520959](http://ubuntuforums.org/showthread.php?t=1520959)

Of course it's not just about ubuntuforums - I just gave this site as an example.

---

### Post by Yarui on 2010-07-03
I thought I was with you until you gave that link.  None of those pictures use javascript, they all open in a new tab just fine for me.

---

### Post by robsoles on 2010-07-03
> **BenAshton24 said:**
> Middle clicking opens the image in a new tab with Firefox.

Exactly what I was going to say straight after making sure I wasn't trippin' last time it seemed to work just fine for me!!!

---

### Post by CharlesA on 2010-07-03
You leftclick on them once to have them open in a window then either click on them again to have it open them in a new tab, or scroll to close them.

Middle click opens them in a new tab for me.

---

### Post by spupy on 2010-07-03
> **CharlesA said:**
> You leftclick on them once to have them open in a window then either click on them again to have it open them in a new tab, or scroll to close them.

Middle click opens them in a new tab for me.

Thanks, that seems to be the solution. Also, it seems this a chromium-related issue.

---

### Post by CharlesA on 2010-07-03
Ah. Using Firefox here and it works as above.

---

### Post by robsoles on 2010-07-03
> **spupy said:**
> Thanks, that seems to be the solution. Also, it seems this a chromium-related issue.

I've been finding that browser more and more annoying - I restored one of my user's files and settings from their original single drive onto their shiny new raid1 mirror setup and the only program that wouldn't restore *everything* they wanted: Chromium Browser!

---

