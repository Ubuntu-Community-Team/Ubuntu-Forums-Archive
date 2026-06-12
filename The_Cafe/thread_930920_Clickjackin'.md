---
title: "Clickjackin'"
date: 2008-09-26
forum: The Cafe
---

### Post by zmjjmz on 2008-09-26
[The problem](http://blogs.zdnet.com/security/?p=1972)
[The (Firefox only) solution](http://blogs.zdnet.com/security/?p=1973)

Sounds pretty scary, but I applied the NoScript preference.

---

### Post by init1 on 2008-09-26
Looks like the best way to prevent it is just to use Links or Lynx :D
> The problem affects all of the different browsers except something like lynx.

---

### Post by zmjjmz on 2008-09-26
> **init1 said:**
> Looks like the best way to prevent it is just to use Links or Lynx :D

Anything that doesn't parse iframes should do.

---

### Post by kernelhaxor on 2008-09-26
That article was linked from slashdot too yesterday.  The article just says there exists an exploit but doesnt tell what it is.  I still don't get how this 'clickjackin' works! They probably haven't disclosed it for security reasons but how do I protect myself if I dont know wht the trick is?

---

### Post by tom66 on 2008-09-26
It uses a hidden iframe to trick you into continuously clicking on a link of some kind. If an attacker can predict where you will click, then he can probably get you to click there. Sounds a bit like an early Firefox bug where if an attacker could predict or create a download or addons box they could install it by getting the user to click somewhere repeatedly. 

I can only see disabling hidden iframes as an option. Seriously, what is the advantage. I mean, hidden links in a hidden iframe. I cannot see that being useful to anyone but an attacker.

---

### Post by zmjjmz on 2008-09-26
> **tom66 said:**
> 
I can only see disabling hidden iframes as an option. Seriously, what is the advantage. I mean, hidden links in a hidden iframe. I cannot see that being useful to anyone but an attacker.

I forbid iframes in general w/NoScript.
This way I can allow them if I trust the site.

---

