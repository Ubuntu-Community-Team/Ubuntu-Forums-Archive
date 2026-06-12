---
title: "I think I've been hacked"
date: 2013-11-10
forum: Security
---

### Post by digitalmetis on 2013-11-10
I had my internet,phone, go down about three days ago. I recieved an error that broke apt-get upgrade. I found a fix for it, and upgaded. I haven't seen any upgrades available since. Then my Firefox browser started to freeze. I couldn't open tabs, and youtube would skip. I scanned with bitdefender and found no viruses. I checked with rootkit scan, and recieved a warning. Can someone read this and tell me if I've been comprimised. Thanks.

[http://pastebin.com/raw.php?i=QVhi6BVh](http://pastebin.com/raw.php?i=QVhi6BVh)

---

### Post by TheFu on 2013-11-10
Didn't see anything too alarming to me - that ruby script might be something ... perhaps if you posted it?

First, google for it ... to see what comes up .... [https://launchpad.net/unhide.rb](https://launchpad.net/unhide.rb)

---

### Post by digitalmetis on 2013-11-10
I tried unhide.rb and it didn't find any hidden processes. Sorry, now I know what to do. Here it is. I hope it's nothing to bad, since I actually ran it without you verifying it.
[http://pastebin.com/raw.php?i=yMWmLFDh](http://pastebin.com/raw.php?i=yMWmLFDh)

---

### Post by cariboo on 2013-11-11
unhide.b and unhide are recommended packages for rkhunter, see the dependency/recommends/suggests [here]("http://packages.ubuntu.com/saucy/rkhunter").

---

### Post by digitalmetis on 2013-11-11
I found the answer. It's normal after installing rkhunter. [http://milodovic.wordpress.com/2013/02/11/things-to-do-after-installing-ubuntu-12-04-3-lts-part-i/](http://milodovic.wordpress.com/2013/02/11/things-to-do-after-installing-ubuntu-12-04-3-lts-part-i/)

---

