---
title: "Yet another 12.04 problem: CUPS"
date: 2013-07-17
forum: Ubuntu, Linux and OS Chat
---

### Post by r_avital on 2013-07-17
After wrestling with 12.04 for better than a month now, well, that release, and the general direction in which Ubuntu is going, my opinion doesn't matter and I can't imagine anyone should be interested.  But facts do matter, or at least they should.

I installed the driver for my printer (Canon IP-4700) -- it was really nice to find a driver for it, instead of the procedure I had to experiment with back in Lucid (which ultimately was simple enough and worled).  So I installed it, and printed a test-page.

It was horrible enough that I went back to my old procedure -- installing two 32-bit-dependent packages from Canon, then getting the relevant PPD file from their source tarball, and installing the PPD file.  Then I printed a test-page of that.

Take a look at the two attached scans, and notice the difference in colors, as well as the clearly marked different driver names:

1. The CUPS-Gutenprint test-page: [https://www.dropbox.com/s/myim3zdc9p0bgi7/cups-gutenprint.png](https://www.dropbox.com/s/myim3zdc9p0bgi7/cups-gutenprint.png)
2. The old PPD test-page: [https://www.dropbox.com/s/rzwugh1issu16jt/old-ppd.png](https://www.dropbox.com/s/rzwugh1issu16jt/old-ppd.png)

Looking at the CUPS-driven page, a single look at the yellow would be enough to tell you something is really wrong, but all the colors are in fact incorrect.  Some developer must have done an easy copy/paste/spit job without giving a darn.

And please note:  This is NOT a matter of old/tired cartridges, because you can clearly see the time/date on both documents, they were printed on the same day, one hour apart.  I have since printed them both again just for grins, in the opposite order, the results are consistent.

Can anyone tell me who are the CUPS people/principals to whom this should be reported?

Other than that, will anything ever work right in Precise?  Aren't reliability and stability the whole point of LTS releases?

I didn't just wake up one morning and decide to spend a month trashing Precise -- I'm quite happy with Lucid, the only reason I'm experimenting with Precise, is that I know I will be forced to ditch Lucid eventually.  I love whisles and bells as much as the next fellow, but not at the expense of functionality, reliability, and stability.

I can only hope that 14.04 will be better, unless of course someone comes up with the notion that today's super-duper-coolnessburger unity launcher is old-school and invents something else by then.  I guess there's always good ol' Debian.  No frills, but it works.

---

### Post by Irihapeti on 2013-07-17
*Thread moved to **Ubuntu, Linux and OS Chat**.*

---

### Post by dino99 on 2013-07-17
you can review the changelogs here : [https://launchpad.net/ubuntu/+source/cups](https://launchpad.net/ubuntu/+source/cups)
and report bug : ubuntu-bug cups

on the other hand, i believe that raring is better in quality than precise.

---

### Post by r_avital on 2013-07-17
Thanks, Dino, I'll report.

Raring:  I tried it, found showstopper issues, but it's possible I've been able to resolve them on a separate test box, so I might try again.  Thanks for the tip.

---

### Post by r_avital on 2013-08-07
Found a workaround: 

1. In a terminal (or wherever in Unity you can enter a command-line), run system-config-printer, to get the old printer configuration interface, because the new one or current one won't let you do this.

2. Double-click on the printer, look at printer options, change "Color Model" from RGB (default) to CMYK.

This behavior was not the behavior of the same printer back in Lucid (with the appropriate Lucid driver).  Still reporting the bug.

---

