---
title: "[SOLVED] How do I install wine from the wine site"
date: 2008-04-25
forum: Virtualisation
---

### Post by Rytron on 2008-04-25
Hi,
I go to this page:
[http://www.winehq.org/site/download-deb]("http://www.winehq.org/site/download-deb")

I open the terminal and type in this
```
sudo wget http://wine.budgetdedicated.com/apt/sources.list.d/hardy.list -O /etc/apt/sources.list.d/winehq.list
```

I then get this response:

```
Error parsing proxy URL http://:8080/: Invalid host name.
```

What is wrong here?

:confused:

---

### Post by gtdaqua on 2008-04-26
why dont you simply:

```

sudo apt-get install wine

```

That ought to do it.

---

### Post by Rytron on 2008-04-26
> **gtdaqua said:**
> why dont you simply:

```

sudo apt-get install wine

```

That ought to do it.

But by getting wine directly from the winehq website - it should be more up to date than by getting via ubuntu.

---

### Post by Rytron on 2008-06-09
I just stick with the older Wine in add/remove.
It works perfectly.

---

