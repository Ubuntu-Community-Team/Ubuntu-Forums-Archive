---
title: "dillo is fast"
date: 2006-01-27
forum: The Cafe
---

### Post by towsonu2003 on 2006-01-27
except the text based browsers, I have never seen such a fast web browser! it's like I have broadband, but I'm on dial up. :mrgreen: just wanted to share this with others who might not know about it. 

PS. won't render pages except basic html. also, need to play around with ~/.dillo/cookiesrc to be able to get cookies. but sooooo fast, couldn't care less!

---

### Post by aysiu on 2006-01-27
It is fast, but speed isn't everything.

While I was impressed with Dillo's speed, its inability to handle frames, use tabbed browsing, or even set a new homepage (as far as I was able to find) put me off to it.

I'm Firefox all the way, despite its relative sluggishness. Tabbed browsing and extensions up the wazoo keep me from switching to other browsers (and, yes, I've tried Epiphany, Konqueror, Opera, and all the rest of the major browsers).

---

### Post by GeneralZod on 2006-01-27
[QUOTE=aysiu]
While I was impressed with Dillo's speed, its inability to handle frames, use tabbed browsing, or even set a new homepage (as far as I was able to find) put me off to it.
[/QUOTE]

Yeah, it's very feature-limited, but quite cool - especially for low-end systems.  Fun fact - the stock Dillo that comes with Gentoo actually *does* have tabs, which is neat! :)

---

### Post by towsonu2003 on 2006-01-27
[QUOTE=aysiu]While I was impressed with Dillo's speed, its inability to handle frames, use tabbed browsing, or even set a new homepage (as far as I was able to find) put me off to it.
[/QUOTE]
you may be able to change the homepage using ~/dillo/dillorc (or a similar name). The website mentions a sample dillo configuration file, but I couldn't find it in my system. to be honest, it renders the default homepage (about:splash) faster than firefox does with about:blank, which is very weird eheh. for dial up, the speed is very amazing. 
It seems tabbed browsing needs patching the source code and recompiling from source. maybe it will be there in the 1.0 release (which seems too far away after 5 years of development leading to 0.8.5 ;) )

---

### Post by fuscia on 2006-01-27
dillo's great. i use it whenever i'm in an impatient mood (which is half the time).

---

### Post by dcast on 2006-01-27
oh wow... is it ever i read the post and installed it.

---

### Post by fuscia on 2006-01-28
links2 might be even faster. i'm trying it now with a graphical interface - *links2 -g*

---

### Post by dolson on 2006-01-28
Oh hey, thanks for the links2! I never realized there was another version of links. Never thought to check. And the -g is sweet!

---

### Post by aysiu on 2006-01-28
[QUOTE=towsonu2003]you may be able to change the homepage using ~/dillo/dillorc (or a similar name). The website mentions a sample dillo configuration file, but I couldn't find it in my system.[/QUOTE] Yeah, the only file I found in ~/.dillo was cookiesrc

---

### Post by GeneralZod on 2006-01-28
[QUOTE=aysiu]Yeah, the only file I found in ~/.dillo was cookiesrc[/QUOTE]

```

cp /etc/dillorc ~/.dillo

```

Then in ~/.dillo/dillorc, edit the entry called "Start page".  Mine's set to google.com! :cool:

---

### Post by towsonu2003 on 2006-01-28
[QUOTE=GeneralZod]```

cp /etc/dillorc ~/.dillo

```

Then in ~/.dillo/dillorc, edit the entry called "Start page".  Mine's set to google.com! :cool:[/QUOTE]
very helpful, thanks a lot!

---

### Post by fuscia on 2006-01-28
i have come to the conclusion, in my drunken stupor, that time saved by not using firefox, is used up navigating one's way through all the pages firefox skips, using dillo and links2. all hail the slug!

---

### Post by lotusleaf on 2006-01-29
Dillo is fast, and bundled by several of the tiny sized Linux distros for good reason.

---

