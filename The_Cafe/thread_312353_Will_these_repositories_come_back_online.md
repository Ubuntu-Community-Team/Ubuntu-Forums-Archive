---
title: "Will these repositories come back online?"
date: 2006-12-04
forum: The Cafe
---

### Post by djsroknrol on 2006-12-04
I pooched my Beryl and decided to do a clean install, but I'm getting a 404 on these two:

deb [http://xgl.compiz.info/](http://xgl.compiz.info/) dapper main
deb-src [http://xgl.compiz.info/](http://xgl.compiz.info/) dapper main

I'm sure it's because of the crash, but does anyone have any info on if they'll be back online?

---

### Post by PriceChild on 2006-12-04
Hey there, guessing you installed from my HOWTO....

Repositories have changed... They WILL stay as this:

```
deb http://ubuntu.beryl-project.org edgy main
```
btw, the other mirror doesn't have as much traffic allowance as me, and so you can choose to use me specifically to help out at:
```
deb http://beryl-mirror.pricechild.co.uk edgy main
```

The first mirror basically round robins you to either me or lupine completely randomly, sharing the load.

If/When me or him take our mirrors down, and others provide mirrors then that initial repo will stay the same and you won't notice the difference :)

---

### Post by djsroknrol on 2006-12-04
Thanks Pricy for that...but I'm running Dapper still. Can I get away with changing Edgy with Dapper? will I still get what I need?

Everyone is saying that Dapper isn't supported, but I didn't have any problems with Beryl till lately, and Edgy doesn't like my compy...

---

### Post by PriceChild on 2006-12-04
> **djsroknrol said:**
> Thanks Pricy for that...but I'm running Dapper still. Can I get away with changing Edgy with Dapper? will I still get what I need?

Everyone is saying that Dapper isn't supported, but I didn't have any problems with Beryl till lately, and Edgy doesn't like my compy...Dapper Isn't supported anymore no, and you won't receive any updates.

You can change edgy to dapper and have working repos though.

On my server: [http://beryl-mirror.pricechild.co.uk/dists/dapper/main/](http://beryl-mirror.pricechild.co.uk/dists/dapper/main/) you can see everything at 0.1.1

---

### Post by BLTicklemonster on 2006-12-04
Yeah, I reinstalled using repos, and still have the "no titlebar on any windows" problem. Is there any certain guaranteed way to specifically absolutely for sure resolve this issue at all?

---

### Post by earobinson on 2006-12-04
Im pretty sure a server died and will be back up soon!

---

### Post by PriceChild on 2006-12-04
> **BLTicklemonster said:**
> Yeah, I reinstalled using repos, and still have the "no titlebar on any windows" problem. Is there any certain guaranteed way to specifically absolutely for sure resolve this issue at all?It could be any number of many things...

Make sure you've got the "window decorations" plugin enabled in beryl settings manager. type ```
emerald
``` To ensure its on.

> **earobinson said:**
> Im pretty sure a server died and will be back up soon!Nope, check out my explanation above.

---

### Post by earobinson on 2006-12-04
nm then

---

