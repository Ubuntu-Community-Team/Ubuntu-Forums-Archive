---
title: "OpenSSH server questions"
date: 2006-09-26
forum: Server Platforms
---

### Post by Cyraxzz on 2006-09-26
By it's default settings how many login guesses does it give you? since it's man page doesn't state such info.

---

### Post by bernied on 2006-09-26
I don't think there is a limit, judging from my auth.log

keep trying heroes
(sorry, my little rant)

---

### Post by mannheim on 2006-09-26
"man sshd_config" gives you some information on this sort of thing.

For example, "MaxAuthTries" is 6 by default, according to that man page. This is the maximum number of authorization attempts per connection. 

Of course, an intruder trying to guess a password isn't limited to 6 guesses, because the intruder can connect repeatedly without limit, unless some additional mechanism is put in place.

---

