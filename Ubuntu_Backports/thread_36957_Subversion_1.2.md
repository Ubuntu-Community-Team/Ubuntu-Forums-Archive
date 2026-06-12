---
title: "Subversion 1.2"
date: 2005-05-25
forum: Ubuntu Backports
---

### Post by xmlblog on 2005-05-25
Humbly requesting Subversion 1.2 backport.
Thanks!

---

### Post by jdong on 2005-05-25
[http://packages.ubuntu.com/cgi-bin/search_packages.pl?searchon=names&version=all&exact=1&keywords=subversion](http://packages.ubuntu.com/cgi-bin/search_packages.pl?searchon=names&version=all&exact=1&keywords=subversion)

Not in Breezy

---

### Post by xmlblog on 2005-05-25
Sorry for my ignorance. Let me see if I understand now: you're backporting Breezy packages into Hoary, correct? So, if I wanted to suggest that Breezy update to 1.2.0 I assume I contact the package maintainer listed here: 

[http://packages.ubuntu.com/breezy/devel/subversion](http://packages.ubuntu.com/breezy/devel/subversion)

Am I right so far? And if/when once it makes it into Breezy then this request would be valid? 

I guess I'm still not sure who does what WRT the workflow between what the Debian maintainers / Ubuntu devs / Backports devs are doing.

Any enlightenment much appreciated, of course. There's nothing in the FAQ that makes this clear, but if someone would enlighten me, I'd be happy to contribute a formal write-up on this process.

---

### Post by jdong on 2005-05-25
I'm under quite a bit of pressure from the Ubuntu Developers about Backports progressing too quickly, causing problems with Ubuntu... ([http://www.ubuntulinux.org/wiki/UbuntuBackports](http://www.ubuntulinux.org/wiki/UbuntuBackports))

Something I certainly don't want to do is to go ahead of Breezy, because that causes potential upgrading issues in the future, much like we encountered from Warty to Hoary, which were resolved barely in time for the migration.

I want to see it in Breezy before I take any action.

---

### Post by xmlblog on 2005-05-25
JDong, 
Thanks that makes sense. So, just out of curiosity, who should I request the 1.2.0 from so they make it into Breezy?  The Ubuntu Devs? If so, could you be so kind as to let me point me at the right place to make this request? The svn version in Hoary 1.1.1 is pretty old now and there have been significant improvements and bugfixes. I'd hate to see Breezy maintain the status quo on the fastest growing SCM.

---

### Post by jdong on 2005-05-25
Talking to the maintainer of the package is going to be your best bet.

However, don't be surprised if he turns you down for stability reasons: with such a fast release cycle, Ubuntu can't afford to introduce in something so big it may take till the end of September to get working ;) lol

---

### Post by xmlblog on 2005-05-25
Lol. I'll probably just build from the sources but it's a shame that the community won't be able to apt-get the latest version in the meantime.

---

### Post by dvarnes on 2005-08-15
[QUOTE=jdong]I'm under quite a bit of pressure from the Ubuntu Developers about Backports progressing too quickly, causing problems with Ubuntu... ([http://www.ubuntulinux.org/wiki/UbuntuBackports](http://www.ubuntulinux.org/wiki/UbuntuBackports))

Something I certainly don't want to do is to go ahead of Breezy, because that causes potential upgrading issues in the future, much like we encountered from Warty to Hoary, which were resolved barely in time for the migration.

I want to see it in Breezy before I take any action.[/QUOTE]


It is in Breezy now !!  :)  

[http://packages.ubuntu.com/cgi-bin/search_packages.pl?searchon=names&version=all&exact=1&keywords=subversion](http://packages.ubuntu.com/cgi-bin/search_packages.pl?searchon=names&version=all&exact=1&keywords=subversion)

Is this still a valid request ?
thanks !
davidv

---

### Post by jdong on 2005-08-15
no, it's not valid -- swig is a C library, which is needed by SVN 1.2.x. Backporting libraries is a terrible idea.

---

