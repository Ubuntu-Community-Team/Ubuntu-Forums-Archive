---
title: "My Pangolin is not burning CD's with Gutsy"
date: 2008-03-20
forum: System76 Support
---

### Post by alexisbellido on 2008-03-20
Hello, I'm the proud owner of a Pangolin for almost a year. I love my laptop, really, but since I upgraded to Gutsy a few months ago my CD/DVD drive stopped burning.

I was able to burn CD's with Feisty, I have many discs here.

I've read many posts about the problem by the burner provided in Nautilus so I tried cdrecord, xcdroast and k3b in my Pangolin, as a regular user and as root in all cases and still can't burn any CD or DVD.

The laptop shows the dialog of writing (a text indication in the case of cdrecord) and takes a few minutes but then I get nothing written to the disc.

Any suggestions?

Thanks!

---

### Post by thomasaaron on 2008-03-20
Your problem is probably caused by a bug in Update Manager. In the upgrade from Feisty to Gutsy, it caused a lot of computers to loose sound and/or their CD drives.

It is a long post, but here is the page of it with the most useful information.
[http://ubuntuforums.org/showthread.php?t=584100&highlight=dvd&page=3](http://ubuntuforums.org/showthread.php?t=584100&highlight=dvd&page=3)

We could create a start-up script that would enable your cd drive, but probably the better bet would be to just re-image your system with a fresh coat of Gutsy 7.10 64-bit.

---

### Post by alexisbellido on 2008-04-13
64 bit? Does Pangolin support 64 bit? actually, are Core 2 Duo processors 64 bit? Sorry if it's a silly question, never had thought about it.

Would a fresh install of Gutsy 32 bit would help as well? I'm worried some application won't run in 64.

---

### Post by thomasaaron on 2008-04-14
If you have a core 2 duo, it should support 64-bit Ubuntu.

A fresh install of 32-bit would do the trick as well. You don't have to worry, though, about applications not running in 64-bit. At least not the ones in the repositories.

---

