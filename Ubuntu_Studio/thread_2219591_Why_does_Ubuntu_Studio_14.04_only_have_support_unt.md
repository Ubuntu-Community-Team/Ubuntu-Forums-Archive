---
title: "Why does Ubuntu Studio 14.04 only have support until 2017?"
date: 2014-04-24
forum: Ubuntu Studio
---

### Post by osterchrisi on 2014-04-24
Ubuntu Studio 12.04 LTS has 5 years support until 2017. According to the official Ubuntu Studio homepage Ubuntu Studio 14.04 LTS also has support until 2017 while Ubuntu 14.04 LTS is supported for five years again. Why is that?

I just made my Ubuntu Studio 12.04 usable next to my Ubuntu Studio 10.04 so I will switch very soon. Is there a reason for me now to set up the newer Ubuntu Studio 14.04 when the support will end at the same time?

Thanks for your answers.

edit: Oh, I should probably add that I didn't use the Ubuntu Studio 12.04 yet apart from installing a few programs and getting gnome shell and my graphics card running. I have a pretty old machine with an old-ish graphics card (Dell Studio 1558 w/ ATI Mobility Radeon HD 4500).

---

### Post by jejeman on 2014-04-24
Core of the system is supported for 5 years. Don't know about lowlatency kernel, but I guess its for 5 years.
XFCE is supported for 3 years.
So thats why, like Xubuntu, Ubuntu Studio is supported for 3 years (for the whole system).

And no, 12.04 is also 3 years.

---

### Post by osterchrisi on 2014-04-24
> **jejeman said:**
> And no, 12.04 is also 3 years.

Well, not according to this page [http://ubuntustudio.org/download/]("http://ubuntustudio.org/download/")... otherwise I wouldn't be wondering.

---

### Post by jejeman on 2014-04-24
Ubuntu Studio is more a variant of Xubuntu, you should read their release notes
[http://xubuntu.org/news/12-04-release/](http://xubuntu.org/news/12-04-release/)

For both versions repository will be active for 5 years, and that's what counts. Security fixes are available for the whole that period on any Ubuntu variant, and that can be important. Rest is not important. All the bug fixes are made within a year if any. And no software will be updated to the upstream versions.

---

### Post by osterchrisi on 2014-04-24
Thanks, jejeman, for your input. So what's the difference then, I don't understand. Only the number in the name (in the case of Ubuntu Studio 12.04/14.04 I mean)?

---

### Post by su:bhatta on 2014-04-25
Studio 14.04 actually has newer versions of most applications than 12.04 as default and some new applications have been added.
Also, a newer kernel, 3.13.
Actually, not anything that you cannot install on the 12.04, .

Looking at your Graphics card, are you using proprietory drivers? Then it is better for you to stick with the 12.04 for longer.
Since last year AMD has stopped development of drivers for 2xxx-4xxx cards.

With 14.04 your only resource is the open-source drivers.
Though, Kernel 3.13 is more AMD graphics friendly, as many have reported.

---

### Post by osterchrisi on 2014-04-25
Okay, so 14.04 is more of a "pre-updated" 12.04 with a newer kernel running in the bottom? Yes, I actually run the proprietory drivers downloaded directly from the AMD website, hey worked out of the box for me (as opposed to fglrx which didn't work at all) and my fans don't go crazy. I'll probably stick with 12.04 for now then unless someone would point out a fact that we have overlooked until now.

---

