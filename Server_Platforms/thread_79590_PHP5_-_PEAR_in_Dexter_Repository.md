---
title: "PHP5 - PEAR in Dexter Repository?"
date: 2005-10-20
forum: Server Platforms
---

### Post by parf on 2005-10-20
Does anyone how you get pear using the [http://people.debian.org/~dexter](http://people.debian.org/~dexter) repositories? I've installed php5, but pear is missing.

I can't use the breezy's php5 because it's missing mcrypt. I've been using [http://www.heydon.com.au/debian](http://www.heydon.com.au/debian) for hoary, but he doesn't have a breezy version available yet. The dexter stuff seems complete, except for pear. I can't believe pear isn't there, the packages even suggest php-pear, but it doesn't exist anywhere I can find.

Any help is much appreciated.

Thanks - Dave

---

### Post by aouie on 2006-02-01
Consider using dotdeb instead of dexter. Dotdeb finally got all the things I wanted for PHP5 and Apache 1.3. They recently got the pdo support going. They also have pear, mysql, pgsql, ....
deb [http://packages.dotdeb.org/](http://packages.dotdeb.org/) stable all
deb-src [http://packages.dotdeb.org/](http://packages.dotdeb.org/) stable all
Sincerely,
Aouie

---

### Post by parf on 2006-02-01
I'm using the dotdeb packages on my Debian stable server, I agree, they work very well.

But dotdeb doesn't have a breezy repository, and it's supposed to be kind of dangerous to mix-and-match repositories from different distributions. Ubuntu is based on Debian, but it's sid, not stable. I guess if it works, though... I'll give it a try.

Thanks - Dave

---

