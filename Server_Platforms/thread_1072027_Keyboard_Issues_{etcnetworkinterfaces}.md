---
title: "Keyboard Issues {/etc/network/interfaces}"
date: 2009-02-17
forum: Server Platforms
---

### Post by c.hobbes on 2009-02-17
Hello all, this is my 1st post. hooray.

i downloaded the latest version of Ubuntu Server (yesterday) and installed on my desktop. all is well, except when i try to assign a static ip address to it. 

when i type in /etc/network/interfaces, i get the interface i want, make my changes, but cannot save them.

If i hit CTRL + x, i'm either greeted with a system beep or a blue "^X" showing up where my cursor was.

This isn't limited to the CTRL + x command either, it also applies to every other command i try to give it, making this very counter-productive.

Also, i have issues with just simple navigation around this interface, sometimes my cursor doesn't feel like producing the letter i typed, it'd much rather greet me with another system beep. sometimes, when i press the "." key, it acts as a backspace and deletes what the cursor was on. the arrow keys never work, and they only seem to instigate this problem more often than not.

I am using a USB keyboard, but why would this problem only arise during the editing of /etc/network/interfaces? every other command i've used types out just fine.

Thanks for making it through my very long, 1st question. May the Schwartz be with you.

---

### Post by cariboo on 2009-02-17
What editor are you using to edit your config files?

Jim

---

### Post by c.hobbes on 2009-02-17
sudo vi /etc/network/interfaces

I tried replacing my USB keyboard with a conventional one plugged into the port on the back, yet i'm getting the same result

---

### Post by volkswagner on 2009-02-17
If you are not experienced with vi, you should learn the commands.  There are many hits on google to help with this.

Or you can use a nano, which will let you use ctrl+x and ctrl+o, etc.

If you want to copy and paste in nano use shift+ctrl+c or shift+ctrl+v respectively.

Good luck

---

### Post by ephmanjmm on 2009-02-17
For vi:

[http://www.lagmonster.org/docs/vi.html](http://www.lagmonster.org/docs/vi.html)

---

### Post by c.hobbes on 2009-02-17
> **ephmanjmm said:**
> For vi:

[http://www.lagmonster.org/docs/vi.html](http://www.lagmonster.org/docs/vi.html)

thank you guys, that worked

---

