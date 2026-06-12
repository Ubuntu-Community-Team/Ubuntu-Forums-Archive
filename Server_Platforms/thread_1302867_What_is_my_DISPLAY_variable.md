---
title: "What is my DISPLAY variable?"
date: 2009-10-27
forum: Server Platforms
---

### Post by leohart on 2009-10-27
I have a Ubuntu server with dual video card. I have some GLUT code that will only work if I have the variable DISPLAY set.

So if I ssh into this server, I don't have this variable set. How do I know my available options?

For example, if I set up this machine, then I know it has :0.0, :0.1, :1.0 and :1.1. But if someone is administering this machine and I am only a user, how do I know what are my available DISPLAYs and SCREENs?

---

### Post by Lars Noodén on 2009-10-28
Display doesn't usually get set unless you use X forwarding.
[INDENT][FONT="Courier New"]
ssh    -l user remotehost.example.org 'echo $DISPLAY'
ssh -X -l user remotehost.example.org 'echo $DISPLAY'[/FONT][/INDENT]

---

### Post by leohart on 2009-10-28
Certainly, but there are only a set amount of display/screen available per the settings of your Xorg. What I want to know is: what are they?

This is necessary because if I have four displays in separate X screens: :0.0, :0.1, :1.0, :1.1 . By setting the DISPLAY environment variable prior to launching my binary, I can choose to output to a certain display. This, consequently affects which video card in the system is used to render for my binary. I want to run 4 copies of my code if I have 4 separate X screens running.

---

