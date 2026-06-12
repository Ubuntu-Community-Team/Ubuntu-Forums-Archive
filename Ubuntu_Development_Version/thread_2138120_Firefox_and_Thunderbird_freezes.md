---
title: "Firefox and Thunderbird freezes"
date: 2013-04-23
forum: Ubuntu Development Version
---

### Post by benvantende on 2013-04-23
Since the first beta of 13.04 I have freezes of Thunderbird and Firefox. They seems to freeze when not in focus. It is hard to identify exactly when the freeze happens. On average have 4 freezes a day. Any ideas how to solve this?

tHNx ben

---

### Post by Gavin77 on 2013-04-23
It's a bug in the gtk oxygen engines apparently. 

[https://bugs.launchpad.net/ubuntu/+source/thunderbird/+bug/963736](https://bugs.launchpad.net/ubuntu/+source/thunderbird/+bug/963736)
[https://bugs.launchpad.net/ubuntu/+source/emacs23/+bug/1142213](https://bugs.launchpad.net/ubuntu/+source/emacs23/+bug/1142213)

I doubt it will be fixed before Raring is released so this is going to impact a lot of Firefox users.

---

### Post by Roman0 on 2013-04-27
As suggested in the bug #1142213 comments, switching to Raliegh GTK2 theme seems to help, at least as a temporary workaround. Good to see it's an already known bug.

---

