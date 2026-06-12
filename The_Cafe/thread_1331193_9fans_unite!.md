---
title: "9fans unite!"
date: 2009-11-19
forum: The Cafe
---

### Post by MaxIBoy on 2009-11-19
How many 9fans are there in here? I've been running Plan 9 in Qemu the past few days and I'm only getting more and more impressed with it; my initial bad impressions are surprisingly easy to work around.

Take the lack of a "cat -n" for example. That's just 11 lines of RC script:
[http://mirtchovski.com/lanlp9/scripts/catn](http://mirtchovski.com/lanlp9/scripts/catn)

And when you think of how [one line of script spans ten thousand lines of C](http://catb.org/~esr/writings/unix-koans/ten-thousand.html), this is starting to look like a feature, not a bug.


Even the clunky UI is easy to improve. It took about an hour to write a desktop layout for Plan 9, almost all of which was me learning the RC lanugage and reading man pages. If I had to do it again now it would take at most 20 minutes.


(This one is slightly stretched, I was maximizing a 1024*768 Qemu window on a 1280*800 display.
[[IMG]http://img39.imageshack.us/img39/4189/de91label.th.png[/IMG]](http://img39.imageshack.us/i/de91label.png/)


[[IMG]http://img194.imageshack.us/img194/8170/de92.th.png[/IMG]](http://img194.imageshack.us/i/de92.png/)



Introducing window decorations with close and hide buttons would be as  simple as making each window an instance of rio with two subwindows,  plus hacking together a few lines of Plan9 C (better than UNIX C) to  provide the buttons. Contrast this with X, where the window decorator  alone is probably a couple hundred lines...

---

