---
title: "Is there a backporting &quot;cookbook&quot;?"
date: 2005-12-10
forum: Ubuntu Backports
---

### Post by HippoMan on 2005-12-10
There are a couple packages from Debian/sid that are much more up to date than their current Ubuntu counterparts.  I have already submitted a backports request for them here (they are runit-1.3.1 and runit-run-0.6.0), but I see that you folks are busy and that there's a backlog.  I'd like to use these new versions as soon as possible, and I'm thinking that I should probably just try to backport them myself while I'm waiting.

Is there a document that describes how to change a proper Debian *.deb package into one that will correctly install under Ubuntu?  I'm guessing that this probably doesn't involve much more than some possible directory name changes, given that the current Ubuntu packages and their Debian/sid counterparts have the same names.

Can someone point me to some sort of backporting "cookbook" that describes things like this, if such a document exists?

Thanks in advance.

---

### Post by Seth on 2005-12-10
[QUOTE=HippoMan]There are a couple packages from Debian/sid that are much more up to date than their current Ubuntu counterparts.  I have already submitted a backports request for them here (they are runit-1.3.1 and runit-run-0.6.0), but I see that you folks are busy and that there's a backlog.  I'd like to use these new versions as soon as possible, and I'm thinking that I should probably just try to backport them myself while I'm waiting.

Is there a document that describes how to change a proper Debian *.deb package into one that will correctly install under Ubuntu?  I'm guessing that this probably doesn't involve much more than some possible directory name changes, given that the current Ubuntu packages and their Debian/sid counterparts have the same names.

Can someone point me to some sort of backporting "cookbook" that describes things like this, if such a document exists?

Thanks in advance.[/QUOTE]
If you ever come on IRC (irc.freenode.net), look me up in #kubuntu or #kubuntu-devel (username seth_k) and I'd be happy to show you how to get started :)

But here are those packages for you:

[http://sethkinast.com/ubuntu/breezy/backports/](http://sethkinast.com/ubuntu/breezy/backports/)

---

### Post by HippoMan on 2005-12-10
[quote=Seth]If you ever come on IRC (irc.freenode.net), look me up in #kubuntu or #kubuntu-devel (username seth_k) and I'd be happy to show you how to get started :)

But here are those packages for you:

[http://sethkinast.com/ubuntu/breezy/backports/]("http://sethkinast.com/ubuntu/breezy/backports/")[/quote]
Thank you!

This honestly was not an attempt to get someone else to do this for me.  I really want to learn it, myself.

I haven't been in irc for years, but when I get some time, I'll stop by and take you up on your kind offer.

With much appreciation ...

---

### Post by Seth on 2005-12-10
[QUOTE=HippoMan]Thank you!

This honestly was not an attempt to get someone else to do this for me.  I really want to learn it, myself.

I haven't been in irc for years, but when I get some time, I'll stop by and take you up on your kind offer.

With much appreciation ...[/QUOTE]
Oh, I know, I just happened to stop in at the right time :) and those packages were very easy to backport, so no big deal ;)

---

