---
title: "Managing non-repo software using the staff group"
date: 2008-04-23
forum: Security
---

### Post by Patsoe on 2008-04-23
Hi all,

I want to start enforcing the policy that only software coming through APT can be installed in /usr or /bin, and everything compiled locally or downloaded from something other than a trusted repository can only be installed in /usr/local (at least, that is my understanding of what's usually done on Debian based systems).

So I thought it would make sense not to run such install procedures through sudo with root privileges, but rather through sudo as some other user that is a member of the staff group. This way, crufty scripts that write to /bin or so even though you specified another install path have less leeway to do damage.

Before I go ahead, I thought I'd post the idea here, hoping that you'll tell me if there's a better way or some convention about this that I don't know of. Thanks in advance for your feedback!

The plan in a bit more detail:
[LIST]
[*]something like "chown -R root:staff /usr/local"
[*]add a user who's a member of the staff group, say "local_admin"
[*]create an alias, say "staffdo", that really does "sudo -u local_admin"
[/LIST]

---

### Post by Patsoe on 2008-04-24
Ok, I went ahead and worked it out: [http://learninginlinux.wordpress.com/2008/04/24/staffdo-my-handicapped-version-of-sudo/](http://learninginlinux.wordpress.com/2008/04/24/staffdo-my-handicapped-version-of-sudo/)

---

