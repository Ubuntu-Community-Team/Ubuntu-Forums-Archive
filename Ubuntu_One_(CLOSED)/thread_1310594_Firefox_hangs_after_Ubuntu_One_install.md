---
title: "Firefox hangs after Ubuntu One install"
date: 2009-11-01
forum: Ubuntu One (CLOSED)
---

### Post by slugicide on 2009-11-01
Hey, I just set up Ubuntu One on my laptop and netbook, including the bookmarks sync and Tomboy notes. Now Firefox hangs every ten seconds. Like, literally every ten seconds. What is going on here?

---

### Post by Merovius on 2009-11-02
I have the same thing. See my post here,

[http://ubuntuforums.org/showthread.php?p=8213712#post8213712](http://ubuntuforums.org/showthread.php?p=8213712#post8213712)

I had to diable the Bindwood addon in Firefox to make it stop. No replies yet to my post.

---

### Post by alanjohnsmith on 2009-11-02
Yep. While it seems a good idea (and has a great name), I can't see that the advantages of Bindwood are worth the constant freezes. I'll be waiting for a proper fix.

---

### Post by joshuahoover on 2009-11-02
> **slugicide said:**
> Hey, I just set up Ubuntu One on my laptop and netbook, including the bookmarks sync and Tomboy notes. Now Firefox hangs every ten seconds. Like, literally every ten seconds. What is going on here?

Ubuntu One bookmarks will take a little while to sync initially and cause Firefox to become unresponsive, but constant behavior like this (every ten seconds) is not correct. Please make sure you have the latest update to Bindwood (sudo apt-get update && sudo apt-get upgrade) and if the problem persists, please file a bug here: [https://bugs.edge.launchpad.net/bindwood/+filebug](https://bugs.edge.launchpad.net/bindwood/+filebug)

---

### Post by slugicide on 2009-11-02
Uninstalling it fixed the hanging. I uninstalled it before doing an apt-get upgrade, but since I just installed it last night I'd think it was up to date.

---

