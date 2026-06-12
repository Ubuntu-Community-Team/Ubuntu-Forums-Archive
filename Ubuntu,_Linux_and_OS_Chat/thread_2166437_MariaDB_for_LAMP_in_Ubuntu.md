---
title: "MariaDB for LAMP in Ubuntu"
date: 2013-08-09
forum: Ubuntu, Linux and OS Chat
---

### Post by bksouder on 2013-08-09
I have been looking around for a thread discussing when Ubuntu will adopt MariaDB as the standard SQL in the LAMP install now that Red Hat and Fedora have moved over.  It seems to be a no brainer at this point.  I probably just missed a post here.  Most of the other MariaDB threads I was finding were pretty old at this point.  It seems like most people have been having positive experiences, and it includes some more advanced features.

---

### Post by monkeybrain20122 on 2013-08-09
Because Debian hasn't switched? I read somewhere that is because business users tend to be conservative when it comes to changes.

---

### Post by The Cog on 2013-08-09
> I read somewhere that is because business users tend to be conservative when it comes to changes.They do. MariaDB - what's that??? I'm meeting that reaction at work.
MariaDB provide .deb packages for Debian and Ubuntu on their web site.

---

### Post by lykwydchykyn on 2013-08-09
The vast majority of the time, if you're asking why $PACKAGE is not in Debian, it's not because of politics, emotions, feuds, conspiracies, ignorance, or stupidity on the part  of developers; it's rather because nobody has stepped forward to do the work.

Take a look at this post from a thread on the debian-mysql mailing list:
[http://lists.debian.org/debian-devel/2013/05/msg00197.html](http://lists.debian.org/debian-devel/2013/05/msg00197.html)

That's a good example of the kind of post I eventually find when I start researching why a package isn't in Debian; someone has filed the ITP, posted a package, and done the legwork; they just don't have the manpower to really test things and properly support the package in Debian.

---

### Post by CharlesA on 2013-08-09
> **The Cog said:**
> They do. MariaDB - what's that??? I'm meeting that reaction at work.
MariaDB provide .deb packages for Debian and Ubuntu on their web site.

Heh.

That is probably what I would run into if I tried switching the MySQL servers over the MariaDB even though it is a drop-in replacement.

I just added their repo to my sources.list and installed it from there.

---

### Post by SeijiSensei on 2013-08-11
I, as a Postgres user, have watched the dramas over MySQL play out over the years and smiled.  Back in the days of RedHat 4, MySQL was still owned by MySQL AB and was not available under an open source license.  I started using PostgreSQL at that point, since it was the only SQL database system I could legally redistribute to clients without charging a royalty.  
Then MySQL was opened, then sold to Sun, then bought by Oracle.  :popcorn:

For those of you wanting to migrate clients, you might mention that [RedHat Enterprise Linux will replace MySQL with MariaDB]("http://www.theregister.co.uk/2013/06/15/red_hat_to_ditch_mysql_for_mariadb_in_rhel_7/") in its upcoming version 7.  Gee, I wonder why RedHat is not a fan of [Oracle]("http://en.wikipedia.org/wiki/Oracle_Linux")?

---

