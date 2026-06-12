---
title: "[SOLVED] GNU screen font issues"
date: 2007-10-23
forum: Server Platforms
---

### Post by SDraconis on 2007-10-23
Just installed GNU screen on my new Ubuntu server installation, and I've noticed some font oddities.  The big one is that instead of getting lines drawn on the screen, I get the character 'â'.  This makes using any console app that draws lines (aptitude, for example) really annoying.  The issue does not show up outside of a screen session.  I tried using the -U option for UTF-8 support, but that didn't help.

---

### Post by SDraconis on 2007-10-28
After testing over SSH from another Linux box, I realized the problem was with my SSH client (PuTTY in Windows).  The solution lies with line-drawing and UTF-8 characters.  More info can be found here: [http://wp.sieker.info/ascii-line-drawing-in-putty](http://wp.sieker.info/ascii-line-drawing-in-putty)

---

