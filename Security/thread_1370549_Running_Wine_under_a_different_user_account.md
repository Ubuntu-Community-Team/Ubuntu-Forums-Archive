---
title: "Running Wine under a different user account"
date: 2010-01-02
forum: Security
---

### Post by Bobulous on 2010-01-02
Hello, all.

I've written an article on my site which lays out steps for installing Wine and running it under its own, separate user account, so that Windows applications cannot access personal files (particularly those in your home directory).
[INDENT]**[http://www.bobulous.org.uk/misc/Spotify-Linux-Wine.html](http://www.bobulous.org.uk/misc/Spotify-Linux-Wine.html)**
[/INDENT]I'm hoping that there are people on this forum who know Ubuntu inside-out, as I'd like to know how effective the described method is at trapping Windows applications so that they cannot read or write personal files or directories.

The way I understand it, once the process is running under user account wine, it's stuck with the access privileges of user wine. But are there ways in which a rogue application could break out of this prison and gain access to whatever it wishes?

I'm guessing that such behaviour would mean someone customising Windows software to recognise Linux, and that such a thing is very unlikely, but I'm still interested to hear what gurus of the Ubuntu internals think of this method.

---

### Post by Agent ME on 2010-01-02
This seems very interesting, and not just useful for running wine programs under another account, but any untrusted linux program too.


However, I think AppArmor could be used as a simpler alternative; It should be possible to use AppArmor to limit wine to only be able to access the ~/.wine folder. I don't know the specifics though.

---

### Post by Bobulous on 2010-01-03
I did try very hard to get AppArmor to work, but I have to admit that after a couple of hours I declared it bug-ridden and ineffective, and I gave up on it. That was a few months ago, and things may have improved since then.

So long as no one can see a way that Wine could break out of its prison, I'm happy to go to the trouble involved in my method. But I'd still like to hear from those deep-down developers who know the inner workings of Ubuntu and Linux.

---

