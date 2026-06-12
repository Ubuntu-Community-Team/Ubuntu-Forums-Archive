---
title: "Installing Wine ?"
date: 2009-02-08
forum: Wine
---

### Post by Leo Dragonheart on 2009-02-08
Can I install Wine by itself on a seperate HD to run windows apps?

---

### Post by overlord.gaurav on 2009-02-08
Install wine by itself..?
I didn't really get your question. Could you explain a bit more, please!?

---

### Post by Leo Dragonheart on 2009-02-08
I have ubuntu on my main HD, but I have a second smaller HD that has nothing on it and was wondering if I could install it on that drive so it will not interfere with my other HD with ubuntu on it. The reason I wonder this is cause I have heard that you can get viruses while running wine and I don't want it to effect the drive I have ubuntu on.

If this sounds like gibberish or completely insane please keep in mind that I am very new to this Linux stuff, only about a month old now so I can't even crawl yet.....:)

---

### Post by hikaricore on 2009-02-08
You can **not** get viruses through WINE.

All of the programs you install under WINE are placed in your home directory under *.wine* and unless you give WINE access it is pretty much limited to this area of your hard drive.

Let me know if I can make this any clearer. ^_^

---

### Post by cogadh on 2009-02-08
Where you install it really won't matter, since how you use it is how a virus would get into it. If you install or run executables from untrusted sources that may contain a virus, then regardless of where you have Wine set up, it could potentially cause problems. 

That being said, the odds that Wine will actually screw something up via a virus are very slim. As long as you are as conscious about what you run in Wine as you should be with what you run in Windows, it won't ever be a problem.

---

### Post by Dizzle7677 on 2009-02-10
> **Leo Dragonheart said:**
> Can I install Wine by itself on a seperate HD to run windows apps?

Technically you can if you build it from source and change the --prefix= & --exec-prefix= switches to the other hard drive path. Course you'd have to move .wine too.[ http://wiki.winehq.org/WineOn64bit]("http://wiki.winehq.org/WineOn64bit")
Not getting into the why's.... :)

---

