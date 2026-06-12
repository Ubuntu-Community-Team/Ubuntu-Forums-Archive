---
title: "Mouse on Server - how to get it working.."
date: 2012-04-29
forum: Server Platforms
---

### Post by ve1drg on 2012-04-29
I just installed the latest 1204lts server solfware and while things seem pretty good,  I have no mouse.
How do I install or get the mouse to work.  Is there a utility commad  that will get things going for me??

---

### Post by CharlesA on 2012-04-29
Ubuntu server is command-line only. You shouldn't need to use a mouse with it.

If you want to manage things with a GUI, you might be better off installing Ubuntu desktop.

---

### Post by HermanAB on 2012-04-30
Xorg controls the mouse.

If you want a server with a GUI, install regular desktop Ubuntu.

---

### Post by ve1drg on 2012-04-30
> **HermanAB said:**
> Xorg controls the mouse.

If you want a server with a GUI, install regular desktop Ubuntu.

Thanks for the input guys.  But I have been using a terminal with a mouse for 15 years.  I use it to capture things and paste them over to other terminals.  A mouse is very useful in terminal mode and much quicker than using it with a GUI.

Now can someone please give me  a tip or two on how to start up the mouse commands to have the system install my mouse??

---

### Post by CharlesA on 2012-04-30
Use ssh from another terminal. I do it all the time with Putty and/or xterm.

---

### Post by ve1drg on 2012-05-01
> **CharlesA said:**
> Use ssh from another terminal. I do it all the time with Putty and/or xterm.

Yes.!!  That is the answer.  I suddenly realized that this is the way to do it.  And I put that plan into action and away things went.  I forgot about using SSH.  But this is the solution.

Thanks guys..

---

### Post by AleTib on 2012-12-06
simply install the package named gpm and you will have the mouse activated in all the TTYs and you'll be able to use to copy/paste, click in Midnight Commander

enjoy! ):P

---

