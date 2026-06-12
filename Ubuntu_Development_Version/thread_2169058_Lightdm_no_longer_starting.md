---
title: "Lightdm no longer starting"
date: 2013-08-20
forum: Ubuntu Development Version
---

### Post by bela83 on 2013-08-20
Hello everybody,

I played a bit with my 13.10 installation and managed to break Lightdm :/

I had Lubuntu/Xubuntu/Ubuntu installed and tried to remove Ubuntu following [http://www.psychocats.net/ubuntu/purelubuntu]("http://www.psychocats.net/ubuntu/purelubuntu")

Now I can't get to my desktop. At boot I have the following items failing :
Starting load fallback graphics devices
Starting Lightdm Display Manager
Starting Send an event to indicate plymouth is up

Thank you for the help.

---

### Post by ibjsb4 on 2013-08-20
Did you notice that link does not cover 13.10?

---

### Post by bela83 on 2013-08-21
> **ibjsb4 said:**
> Did you notice that link does not cover 13.10?

Yes sure, that's what I call playing. I'm not saying that's smart !

---

### Post by xc3RnbFO8P on 2013-08-21
Did you try [Recovery Mode]("https://wiki.ubuntu.com/RecoveryMode"), repair broken packages

---

### Post by bela83 on 2013-08-21
> **Ringi said:**
> Did you try [Recovery Mode]("https://wiki.ubuntu.com/RecoveryMode"), repair broken packages

Hello Ringi ! Yes I did and it didn't resolve the issue.

---

### Post by xc3RnbFO8P on 2013-08-21
in recovery try root and type **unity**

---

### Post by philinux on 2013-08-21
From recovery root prompt.

```
apt-get install --reinstall lubuntu-desktop
```

If no joy reinstall saucy.

---

### Post by bela83 on 2013-08-27
Hi,

I've been away from the computer for a few days. After today's upgrades, works like a charm again. Can't say what did the trick though.

---

