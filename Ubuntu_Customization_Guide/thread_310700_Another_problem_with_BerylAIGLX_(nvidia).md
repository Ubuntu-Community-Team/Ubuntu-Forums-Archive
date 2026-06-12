---
title: "Another problem with Beryl/AIGLX (nvidia)"
date: 2006-12-01
forum: Ubuntu Customization Guide
---

### Post by Feck on 2006-12-01
UPDATE: Currently ignoring my past two problems, as I have a much larger issue now.

After enabling the blur effects, my desktop now doubles itself in a blank black window in the center. I can't see anything I do on the actual desktop but whenever I open a menu or select something, it will not show up on my actual desktop, but flash briefly in the windowed desktop before glitching out and becoming a useless, blank black rectangle in the middle of my screen. I have tried uninstalling everything related to beryl, and reinstalling it all again, but for some reason it automatically defaults to the settings that made my desktop glitch out like this.

If anybody could help in the least with this, that would be phenomenal. I love Beryl, but I don't like it glitching out on me :(

Cheers folk,
Feck

---

### Post by Contrast on 2007-02-04
So I assume you've already disabled Blur effects in the Beryl Settings Manager and that didn't work? If that fixes it, try tinkering with the Blur settings and re-enabling it-- The problem might be that, for whatever reason, one of the parameters doesn't work well with your system. You should at least be able to have Blur enabled though. On every system I've run Beryl on, some of the video cards didn't support Blur, but this just caused Blur effects to not do anything. Leaving Blur enabled didn't cause any problems.

If all else fails, you might want to ask about this over at [http://forum.beryl-project.org](http://forum.beryl-project.org). Beryl has a very supportive community over there, and developers post there regularly as well.

---

### Post by _simon_ on 2007-02-04
Your settings are saved in ~/.beryl

All you need to do is delete that folder then open beryl-manager and it will re-create the folder with the beryl defaut settings, rather than the settings you last used.

EDIT: Just noticed that this is a post dug up from 1st December 06!

---

