---
title: "vi editor: keyboard is screwed up"
date: 2006-12-01
forum: Server Platforms
---

### Post by Zentropic on 2006-12-01
Hi all,

Just installed Ubuntu server ( Edgy ) for the first time. Been using the desktop version for quite a while.

Problem here is the vi editor is not working properly. arrow keys produce A,B,C,D but not always! Backspace is completely non-functional, and any key in general stops responding, until I repeatedly hit i ( insert ), then it starts again. 

This problem occurs whether using a keyboard connected to the box or via ssh from another machine.

It's a fresh install, brand new. Keyboard was setup as US English, and is, of course, that type.

I've never seen this before. Anyone else? It's essentially useless like this, and I'll likely end up paving it and using Fedora 6 ( had fedora 4 on it, decided ot give Ubuntu server a go ) if it can't be fixed.

Thanks in advance.

---

### Post by IbeeX on 2006-12-01
Hi allegedly this is how vi should behave you can fix it if you install vim package it did it for me.

---

### Post by Zentropic on 2006-12-01
Hmmm. Perhaps I have become used to the way Fedora / Red Hat vi behaves, but not being able to type after going into insert mode is  not a default behavior I wouuld expect! And why would the arrow keys only give A,B,C, and D, rather than moving the cursor as they should? This too, is not consistent either. I'm no vi expert, but if this is some default version of it, it's bloody awful.

I'll give it a shot with vim, thx!

---

