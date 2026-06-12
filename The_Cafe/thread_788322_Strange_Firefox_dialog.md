---
title: "Strange Firefox dialog"
date: 2008-05-09
forum: The Cafe
---

### Post by carlosm7 on 2008-05-09
Hi.

Isn't there something wrong with the buttons on Firefox?

---

### Post by SunnyRabbiera on 2008-05-09
no, that error sometimes comes up with loading certain sites.
What site do you see this issue with?

---

### Post by carlosm7 on 2008-05-09
Hi. Thank you for your response.

In this link:

[http://ejohn.org/blog/processingjs/](http://ejohn.org/blog/processingjs/)

Which apparently forwards you to:

[http://dev.jquery.com/~john/processing.js/](http://dev.jquery.com/~john/processing.js/)

Then I clicked on various demos, and got that error several times.

But note that my confusion is not really the error, but the button with the red stop sign being labeled "Continue", and the one with the green arrow being labeled "Stop script".

---

### Post by illu45 on 2008-05-09
> **SunnyRabbiera said:**
> no, that error sometimes comes up with loading certain sites.
What site do you see this issue with?

I think he's talking about the fact that the 'Continue' button has a red 'X' while the 'Stop Script' button has a green arrow. I've gotten the error before, but never paid attention to the icons on the buttons. I can't seem to replicate it on the site you mention, so I'm not sure if it was just a one-time thing or an actual bug. If you get the same issue again (or are able to replicate it), I would suggest submitting it to [Bugzilla]("https://bugzilla.mozilla.org/")

---

### Post by DoktorSeven on 2008-05-09
Design decision based on the fact that Firefox wants you to stop the script vs. letting it go and continuing to freeze Firefox?

Sure, it's not intuitive, but that's the only explanation I can come up with to justify that.  Maybe it does just have the wrong labels.

---

### Post by FuturePilot on 2008-05-09
> **DoktorSeven said:**
> Design decision based on the fact that Firefox wants you to stop the script vs. letting it go and continuing to freeze Firefox?That's what I was thinking.

---

### Post by swoll1980 on 2008-05-09
Green good Red bad me like it that way, me no like change

---

### Post by macogw on 2008-05-09
> **FuturePilot said:**
> That's what I was thinking.

me too

---

### Post by carlosm7 on 2008-05-10
Hi. Thank you for your responses.

It looks like not all of the demos will produce the error. Here are two that do, in my particular machine:

[Koch Fractal]("http://ejohn.org/apps/processing.js/examples/topics/koch.html") 
[Artistic water-color style drawing](http://ejohn.org/apps/processing.js/examples/custom/substrate.html)

---

### Post by warbread on 2008-05-11
> **DoktorSeven said:**
> Design decision based on the fact that Firefox wants you to stop the script vs. letting it go and continuing to freeze Firefox?

Sure, it's not intuitive, but that's the only explanation I can come up with to justify that.  Maybe it does just have the wrong labels.

This is the way I considered it.  They use the same color as traffic lights.  It's arguably easier to understand that way as all industrialized nations (at least) use those colors, and the concept is learned by children early on.

---

