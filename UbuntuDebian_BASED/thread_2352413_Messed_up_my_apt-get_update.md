---
title: "Messed up my apt-get update"
date: 2017-02-12
forum: Ubuntu/Debian BASED
---

### Post by dcpifhq on 2017-02-12
Hi, just to make this clear I'm not using ubuntu right now cuz this pc that I'm using will blow u from the animations on the ubuntu (even if I disable all of them xD)

So, I wanted to install flash playr to run flash games on Chromium, and now everytime I do sudo apt-get update all this pops up (here's how it looks like [http://imgur.com/rHEe8UX](http://imgur.com/rHEe8UX) ). Oh yeah I tried installing virtualbox 4 windows and now i decided ima dual boot them.


So can anyone tell me how can I get rid of these? Cuz, I think since those errors poped up...I don't think I'm able to upgrade and dist-upgrade cuz it keeps saying 0 upgrades 0 removed etc.

AND I tried to install unetbootin, and now this pops up when I try to install it... [http://imgur.com/LB52Ev1](http://imgur.com/LB52Ev1)

**PLEASE ANYONE** tell me how do I fix this...

---

### Post by howefield on 2017-02-12
So what operating system are you using, the references to lucid indicate an old unsupported release ?

Might help to see your repo sources, what's the output of ..

```
egrep -v '^#|^ *$' /etc/apt/sources.list /etc/apt/sources.list.d/*
```

PS. Terminal output is much better pasted back here between [noparse]```

```[/noparse] tags rather than linking to an image.

---

### Post by dcpifhq on 2017-02-12
Nevermind, had to get the latest sources.list Repositories form here: [http://docs.kali.org/general-use/kali-linux-sources-list-repositories](http://docs.kali.org/general-use/kali-linux-sources-list-repositories)
I had put unsupported repositories in there xD. And...yep! Everything is back to normal!

---

### Post by howefield on 2017-02-12
Moved to the "*Ubuntu/Debian BASED*" forum.

---

