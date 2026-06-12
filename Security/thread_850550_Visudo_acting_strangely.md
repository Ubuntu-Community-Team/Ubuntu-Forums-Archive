---
title: "Visudo acting strangely"
date: 2008-07-05
forum: Security
---

### Post by Bunnykun on 2008-07-05
I am having difficulty editing my sudoers.

I enter sudo visudo, and I see the sudoers file as normal.  However, I can't edit it.  key presses don't respond normally, meaning sometimes it the text will appears but usually does not.  Backspace does not work, the only way I can delete text is by pressing "delete," and it seems only if I'm at the end of the line, not in the middle.

pressing ctrl+X does not prompt a syntax check and request to save or whatnot, as I understand it should do.  I can only get out of visudo if I use ctrl+C, then type ":quit!"  I believe that the last time I used visudo, I running Gutsy. I've since upgraded to Hardy.

Any idea what broke? or what I'm doing wrong?

---

### Post by Dr Small on 2008-07-05
Apparently visudo is opening in vi

---

### Post by Bunnykun on 2008-07-05
What does that mean, and how do I prevent it?

---

### Post by Fass on 2008-07-05
[http://ubuntuforums.org/showthread.php?t=850555](http://ubuntuforums.org/showthread.php?t=850555)

Changing which editor visudo uses was just discussed in that thread and tinivole posted a nice guide.

---

