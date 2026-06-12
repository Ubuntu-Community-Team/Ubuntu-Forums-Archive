---
title: "DOS-like application in text mode, 80x25 resolution"
date: 2018-12-16
forum: Ubuntu Application Development
---

### Post by pawelsokolowski on 2018-12-16
Hi all, I am new to this forum, starting development for Linux.
I have a long history of programming starting from 8-bit computers, DOS, Windows all versions.

I have to port my old DOS app that is running on several hundreds of old PC to Linux.
Windows is not an option, because people using the app are train just for using this app, and it should stay just identical as in DOS.

I am thinking of using ncurses.
The system should work with text only, non-GUI.

Problem is it starts in much higher resolution, still in text mode.
Screen looks strange because the console occupies like 2/3 of the screen, the rest is unused.

I need to set the screen resolution to 80x25 characters, like in DOS.

So first question is : Can I set this up generally, for the system console and apps?
Or if not, can I change the screen mode programmaticaly from ncurses just after my app starts?

I would appreciate your ideas.

---

