---
title: "Ubuntu 11.04 Server guest doesn't have mouse support or copy/paste"
date: 2011-07-25
forum: Virtualisation
---

### Post by russianbandit on 2011-07-25
Hi,

I'm using Virtualbox on Windows 7 and installed Ubuntu 11.04 Server edition as a virtual machine. I've installed the Guest Additions as per instructions. When the server boots my screen is pretty small and also doesn't have any support for copy/paste between host and guest machines. There also seems to be no mouse cursor, so I can't scroll or select text using the mouse.

I want to use the guest server to develop on, and I plan on using Vim and command line tools, but I would like to be able to scroll through the output and copy and paste stuff using the keyboard and mouse. Is there some configuration I need to do? Do I need the X server? Should I be installing the Desktop edition?

---

### Post by CharlesA on 2011-07-26
The guest additions only work if you have a GUI installed.

If you just want to do CLI stuff, it would probably be easier to just use Putty and ssh in.

---

### Post by 2F4U on 2011-07-26
Is there a special reason why you choose the server edition. As its name says, its intended for servers. From your description I would say that you are better off with a desktop edition, for example the long term support 10.04.

---

### Post by russianbandit on 2011-07-26
I went with Server because I don't need to use the GUI, since I would be doing everything on command line.
Using Putty to ssh in is what I'm going to do.

---

