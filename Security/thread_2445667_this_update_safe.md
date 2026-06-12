---
title: "this update safe?"
date: 2020-06-18
forum: Security
---

### Post by T6&amp;sfpER35% on 2020-06-18
got a software update today and looked at the description...that sounds dodgy

would it be safe to install it?
sorry if i'm paranoid

[ATTACH=CONFIG]286247[/ATTACH]

---

### Post by guiverc on 2020-06-18
If you're worried, I'd just check your sources to ensure it's coming from an official source (eg. `apt-cache policy <package>`). 

 (I assume it's the `accountservice` package possibly including a few library files that also showed when I searched for that string using `apt-cache search`)

*Sorry if you'd prefer a GUI method of looking up this info, you'll have to wait for another user as I find terminal quicker*

---

