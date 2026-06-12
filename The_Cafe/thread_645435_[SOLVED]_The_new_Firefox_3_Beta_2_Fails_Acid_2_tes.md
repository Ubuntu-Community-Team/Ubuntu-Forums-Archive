---
title: "[SOLVED] The new Firefox 3 Beta 2 Fails Acid 2 test!"
date: 2007-12-20
forum: The Cafe
---

### Post by Kosimo on 2007-12-20
Wow....
The first beta of Ffx 3.o did make the test prefectly... But this second beta is having troubles.   Here the link:

[http://www.webstandards.org/files/acid2/test.html](http://www.webstandards.org/files/acid2/test.html)


Hope this will be fixed on the final release.

---

### Post by ~LoKe on 2007-12-20
Neat.  Pretty close right now.

---

### Post by Kosimo on 2007-12-20
> **~LoKe said:**
> Neat.  Pretty close right now.

Yes, but there is a downgrade from Firefox 3 Beta 1.

---

### Post by Mathiasdm on 2007-12-20
It's actually the Acid2 test that's currently broken. Try in Opera, it'll fail too.

---

### Post by ~LoKe on 2007-12-20
> **Kosimo said:**
> Yes, but there is a downgrade from Firefox 3 Beta 1.

One I'm sure the devs are well aware of.  I hope they get it all resolved! (I'd probably cry; it's like a Rubik cube.)

---

### Post by yatt on 2007-12-20
Is it possible to get a screenshot of what it actually displays? Anyways, my Konqueror doesn't render it correctly either.

This is what I get with Konqi:
[[IMG]http://img211.imageshack.us/img211/7823/snapshot2rg5.th.png[/IMG]](http://img211.imageshack.us/my.php?image=snapshot2rg5.png)

---

### Post by vishzilla on 2007-12-20
on the other hand an internal build of IE8 passes the test

---

### Post by fedex1993 on 2007-12-20
ie8 didnt get anywhere close for me on my windows setup that i only use for gaming but with firefox 3 which they call minefield it works great passes 100%

---

### Post by Mathiasdm on 2007-12-20
What happened is that something changed on the server hosting the test, so when it can't find a page, it returns a 200 status message, instead of a 404.

For a correct Acid2 test: [http://www.hixie.ch/tests/evil/acid/002/](http://www.hixie.ch/tests/evil/acid/002/)

---

### Post by ~LoKe on 2007-12-20
> **Mathiasdm said:**
> What happened is that something changed on the server hosting the test, so when it can't find a page, it returns a 200 status message, instead of a 404.

For a correct Acid2 test: [http://www.hixie.ch/tests/evil/acid/002/](http://www.hixie.ch/tests/evil/acid/002/)

Perfect!

---

### Post by undine on 2007-12-20
Passes with flying colours for me.

---

### Post by Kosimo on 2007-12-20
My god...

I was really aware of this (serious) issue...  But looks like is an Acid 2 test problem.

Comfirmed that works on the last link.  Gonna change the status of this 3RD to Solved.

Thank you guys.

---

### Post by TheFulscht on 2008-01-23
Hey guess what?!! SWIFTFOX passed them both links!!! I was really suprised!! or really should I be?!!

---

### Post by Xbehave on 2008-01-23
i get a 1 row of pixles discrepancy with the original.

siftfox uses the same code so no!

---

