---
title: "print from shell server/"
date: 2013-04-02
forum: Server Platforms
---

### Post by conradin on 2013-04-02
Hi all, 
I have a shell server running and i would like to send print jobs to a network printer. Should I install cups? or is there something else?
Also, how would I print from the command line?

---

### Post by schragge on 2013-04-03
> **conradin said:**
> Hi all, 
I have a shell server running and i would like to send print jobs to a network printer. Should I install cups? or is there something else?
Also, 
CUPS is probably the easiest option. *Something else* would be [gnuspool](http://packages.ubuntu.com/precise/gnuspool) (or [LPRng](http://packages.ubuntu.com/lucid/lprng) on *Lucid*).
> **conradin said:**
> how would I print from the command line? See [lp(1)](http://www.cups.org/documentation.php/doc-1.6/man-lp.html), [lpr(1)](http://manpages.ubuntu.com/manpages/lucid/man1/lpr.1.html)

---

