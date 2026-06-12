---
title: "Microsoft front end guys complain about Firefox :D"
date: 2008-10-28
forum: The Cafe
---

### Post by Nano on 2008-10-28
I was just reading some MS javascript when I found this:

```

		// Firefox counts white space as nodes (wondeful), so we can't count on the position of the firstChild cross browser.
		// It's either the first or second, so check before we change

```

I kinda love these things :)

File is:
[http://www.microsoft.com/azure/scripts/nav.js](http://www.microsoft.com/azure/scripts/nav.js)
lines 79 and 80

---

### Post by BackwardsDown on 2008-10-28
Haha, if I did that everytime with IE6 or IE6 I would have more comments than code:lolflag:

---

### Post by EnGorDiaz on 2008-10-28
> **BackwardsDown said:**
> Haha, if I did that everytime with IE6 or IE6 I would have more comments than code:lolflag:

lmao!

---

### Post by saulgoode on 2008-10-28
> // Firefox counts white space as nodes (wondeful), ...

... because that's what the W3C DOM specification recommends. :rolleyes:

---

### Post by EnGorDiaz on 2008-10-28
> **saulgoode said:**
> ... because that's what the W3C DOM specification recommends. :rolleyes:

lol they spelt wonderful wrong shows you how great the prgrammers are and how devoted they get

---

### Post by LaRoza on 2008-10-28
> **EnGorDiaz said:**
> lol they spelt wonderful wrong shows you how great the prgrammers are and how devoted they get

Microsoft hires good programmers. Examination of their code when it is leaked shows this.

However, the development model sort of mitigates this. 

Typo's in comments are nothing.

---

### Post by snova on 2008-10-28
Amusing.

> **LaRoza said:**
> Microsoft hires good programmers. Examination of their code when it is leaked shows this.

Or the occasional open source project.

> **LaRoza said:**
> However, the development model sort of mitigates this.

What would that be? Closed source?

---

### Post by MaxIBoy on 2008-10-28
I know this-- a friend of mine recently spent a few months as an intern at Microsoft, and turned down a job offer. His explanation was that, first of all, it was boring-- the programmers basically slacked around most of the time, and there was nothing to do. And when there *was* programming work to do, this friend described it as, "take all this legacy code and make it new."

---

### Post by Barrucadu on 2008-10-28
I should start putting comments in my code complaining about IE. I wrote a nice AJAX interface to a site, worked great in Opera and FF, and then I had to rewrite every line of JavaScript because it didn't work at all in IE 7.

---

### Post by LaRoza on 2008-10-28
> **snova said:**
> 
What would that be? Closed source?

That is very broad, so no. They have communication issues internally with all the developers leading to wasted time and mistakes.

---

### Post by macogw on 2008-10-28
"*grumble* what's firefox doing being all stupid and conforming to standards? why would anyone go and do that! *grumble*"

---

### Post by yabbadabbadont on 2008-10-28
> **LaRoza said:**
> Typo's in comments are nothing.

For that matter, typo's in code are nothing... as long as it isn't in a keyword and you are consistent.  ;)

A former co-worker and close friend is dyslexic.  There were a couple of times I had to make modifications to his code in the middle of the night (do to unannounced third party interface changes) and ended up continuing to "misspell" variables because it was quicker than trying to search and replace through multiple source files.  Besides, I have a tendency to use the British spelling of some words myself.  If you really want to mess someone up, use colour instead of color in your code...  :twisted:

---

