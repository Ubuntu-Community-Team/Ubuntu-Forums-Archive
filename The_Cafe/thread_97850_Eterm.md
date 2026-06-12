---
title: "Eterm"
date: 2005-12-01
forum: The Cafe
---

### Post by jrincon87 on 2005-12-01
Hey, is there a way to paste something in Eterm? Ctrl+V doesn't work, Ctrl+Shift+V doesn't work either.
Thanks.

---

### Post by invalid on 2005-12-01
shift insert

Cb

---

### Post by erikpiper on 2005-12-01
highlight
middle click where it goes (Press down scroller)

That is standard linux copy/paste

---

### Post by jrincon87 on 2006-01-23
Another question. How do I change the Eterm codification so that it recognizes caracters like á,ü, etc (spanish)?
Thanks.

---

### Post by jpkotta on 2006-01-23
Another way to cut/paste from a terminal is to *kill* text and *yank* it back (from the dead, presumably).  Here are some standard shortcuts:
[LIST]
[*]ctrl-a : go to beginning of line
[*]ctrl-e : go to end of line
[*]ctrl-k : kill to end of line
[*]ctrl-y : yank from kill buffer
[/LIST]

Read the section of the man page for bash ```
man bash
``` that talks about key bindings.  To get to it quickly, type "/Readline Command Names" (the slash initiates an inline search, just like on firefox).

---

### Post by carl13 on 2006-01-23
[QUOTE=erikpiper]highlight
middle click where it goes (Press down scroller)

That is standard linux copy/paste[/QUOTE]

I never knew that. This will change my life forever. No more ctrl x,c, or v!

---

### Post by arghh2d2 on 2007-11-01
Funny, i never thought a linux standard would involve a mouse click.

---

### Post by init1 on 2007-11-01
> **arghh2d2 said:**
> Funny, i never thought a linux standard would involve a mouse click.
Well, it was modeled after GPM functionality, so at least that's a terminal app ;D
Edit:
I wonder why my smiley isn't being parsed

---

### Post by macogw on 2007-11-01
> **init1 said:**
> Well, it was modeled after GPM functionality, so at least that's a terminal app ;D
Edit:
I wonder why my smiley isn't being parsed

because you used a semi-colon instead of a colon

---

### Post by kevdog on 2008-12-22
eterm 

How do I cut and paste multiple lines from eterm to some application like gedit?  The above solutions were only good for one line!

---

