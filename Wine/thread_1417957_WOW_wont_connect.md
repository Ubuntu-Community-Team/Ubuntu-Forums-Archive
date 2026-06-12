---
title: "WOW wont connect"
date: 2010-02-28
forum: Wine
---

### Post by Arminius on 2010-02-28
ok, when I go to log into wow at the main login screen, where the big frost drake is.
I either get an instant "you have been disconnected from servor" with out it even trying to connect.
or connect comes up and only connected, I've left it for over an hour just to make sure it won't change, and it just hangs on connected

so any ideas?

---

### Post by Arminius on 2010-03-01
bump

---

### Post by Arminius on 2010-03-02
bump

---

### Post by Arminius on 2010-03-03
bump

---

### Post by Penguin Guy on 2010-03-03
Wine is far from perfection - you really don't stand much of a chance of fixing the problem unless you're like super-clever. I'd advise that you just dual-boot, or maybe someone more knowledgeable than me can help you.

Sorry.

---

### Post by Arminius on 2010-03-03
wine has run wow before on my box, somethings just gone wrong this install

---

### Post by hikaricore on 2010-03-04
You didn't install a firewall or something along the lines of moblock did you?
If you have any software or hardware that's blocking ports you'll need to properly configure it to allow the wow ports.

---

### Post by Arminius on 2010-03-04
yeah I did install moblock, does it have a gui?
so I can ajust it's settings
what port does wow need to connect?

---

### Post by hikaricore on 2010-03-04
You'll have to configure it manually for the most part, there is a cli setup interface but I don't remember how to access it.
The blizzard website has a list of every port wow uses if memory serves.

---

### Post by Soulcage on 2010-03-04
Heres a list of ports wow uses [http://us.blizzard.com/support/article.xml?locale=en_US&articleId=21015&pageNumber=1&searchQuery=ports]("http://us.blizzard.com/support/article.xml?locale=en_US&articleId=21015&pageNumber=1&searchQuery=ports")

---

### Post by jre on 2010-03-10
If moblock blocks WOW running under wine, then I guess you have to allow IPs or ports on the FORWARD chain (AFAIK your Linux box is like a router for the wine system, therefore FORWARD). Learn more about allowing traffic in moblock in the wiki: [https://help.ubuntu.com/community/MoBlock](https://help.ubuntu.com/community/MoBlock)

But as you said in your other thread, you were going to use the mobloquer GUI - if you whitelist the IPs there, you will automatically get the correct rules.

---

