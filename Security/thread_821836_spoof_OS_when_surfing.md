---
title: "spoof OS when surfing?"
date: 2008-06-07
forum: Security
---

### Post by schlesinger on 2008-06-07
I'm not sure this is the right place to post this, but here it is... 

My banking website has a screen that occurs right after I log in, that says: "We have detected that you are not running an appropriate operating system and setup." I then have to scroll down two pages and press continue to be able to get into my normal page. 

I've written scripts that have spoofed a user agent before. Is there any way I can spoof my operating system and pretend to be running Windows? I use Firefox, and have checked about:config. Should I edit some useragent string?

Thanks lots.

---

### Post by Monicker on 2008-06-07
You could get the User Agent Switcher extension.

[https://addons.mozilla.org/en-US/firefox/addon/59](https://addons.mozilla.org/en-US/firefox/addon/59)

---

### Post by schlesinger on 2008-06-07
That did it, thanks.

---

### Post by Dr Small on 2008-06-07
I was going to suggest that earlier, but I couldn't remember the name of it! :D

---

### Post by todb on 2008-06-09
I'm curious which bank relies on such weak OS detection? User-agent spoofing is pretty trivial...

---

### Post by stmurray on 2008-06-09
My guess is that the bank is creating their website tailored to a specific browser (or are using Web Site development tools that to that).  Makes development of the site much easier if you only have to test using one browser......

---

### Post by Dr Small on 2008-06-09
> **stmurray said:**
> My guess is that the bank is creating their website tailored to a specific browser (or are using Web Site development tools that to that).  Makes development of the site much easier if you only have to test using one browser......
Which is utterly ridiculous considering there are alot of Linux users who use Firefox / Opera, etc.

---

### Post by stmurray on 2008-06-09
Sometimes money trumps user satisfaction

---

### Post by noerrorsfound on 2008-06-09
> **stmurray said:**
> [COLOR="Red"]Sometimes[/COLOR] money trumps user satisfaction
Correction: *Usually*

---

### Post by rudihawk on 2008-06-10
> **noerrorsfound said:**
> Correction: *Usually*

Correction: Almost always! :)

---

