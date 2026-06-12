---
title: "Ubuntu Server Question"
date: 2006-10-17
forum: Server Platforms
---

### Post by mzracer360 on 2006-10-17
I just installed Ubuntu Server.  Edit: I figured out my first question.

#2 how do i edit files with the server.  Example being the sources.list?

---

### Post by az on 2006-10-17
sudo nano /etc/apt/sources.list

CTRL-O to save and CTRL-X to exit


You may also learn to use vi.  It is quite powerful once you fogure it out.

Leaning vi (or vim) is beyond the scope of this post....

---

### Post by RU-In? on 2006-10-18
quote:"sudo nano /etc/apt/sources.list

CTRL-O to save and CTRL-X to exit

[B]
You may also learn to use vi. It is quite powerful once you fogure it out.

Leaning vi (or vim) is beyond the scope of this post...[/B]"


I notice on furums a lot when metioning Vi (Vim), they all say "hard to learn, beyond scope" which is for the most part true. Most forget to mention typing in:

$ vimtutor <enter>

this will bring up a short tutorial for vim, built right into you box. Try it out when you have 30 min. or so to at least learn the basics of Vi.

---

