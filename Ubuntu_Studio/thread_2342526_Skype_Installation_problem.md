---
title: "Skype Installation problem"
date: 2016-11-07
forum: Ubuntu Studio
---

### Post by zetomtom on 2016-11-07
Can anybody help me to find a way to install Skype in my PC running only the last Ubuntu Studio 64 bit OS?
Thank You.
ZeTomTom

---

### Post by howefield on 2016-11-07
If you enable the Partner repository you should be able to apt-get install it.

Open the Software and Updates application and from the *Other Software* tab check off the Partner repository, close out and reload your software sources, then..

```
sudo apt-get install skype
```

That's probably the best method, there is also the Skype for Linux which is in Alpha, and as alpha software is likely to be short of some features that you might need.

---

