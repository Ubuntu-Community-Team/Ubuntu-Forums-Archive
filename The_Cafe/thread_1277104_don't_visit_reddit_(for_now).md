---
title: "don't visit reddit (for now)"
date: 2009-09-27
forum: The Cafe
---

### Post by Xbehave on 2009-09-27
Reddit is under attack via a JS attack, if you mouse over the attacker text (in any browser) and allow javascript from reddit.com you will trigger it. Please [SIZE="5"][COLOR="Red"]don't visit[/COLOR][/SIZE] while logged in (e.g use private browsing as that way you will not be able to post)

---

### Post by pwnst*r on 2009-09-27
[http://mashable.com/2009/09/27/reddit-attack/](http://mashable.com/2009/09/27/reddit-attack/)

lol, that's some ownage right there.

---

### Post by purgatori on 2009-09-27
I can't imagine what would compel me to visit the site in the first place.

---

### Post by Xbehave on 2009-09-27
> **pwnst*r said:**
> [http://mashable.com/2009/09/27/reddit-attack/](http://mashable.com/2009/09/27/reddit-attack/)

lol, that's some ownage right there.
Can somebody explain how its XSS (claimed in the link), it seams like all the code is run from reddit so its not cross site at all, hence why noscript is failing!

---

### Post by hessiess on 2009-09-28
> **Xbehave said:**
> Can somebody explain how its XSS (claimed in the link), it seams like all the code is run from reddit so its not cross site at all, hence why noscript is failing!

Look up how cross site scripting works, one of the variants exploits incorrect invalidation of user input to get script stored in the sites DB, from which it is displayed on all pages that read that perticular DB record.

---

