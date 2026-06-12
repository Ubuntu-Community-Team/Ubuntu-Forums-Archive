---
title: "Elinks not using the system locale, even with language-pack-**-base installed"
date: 2009-06-01
forum: Server Platforms
---

### Post by m-p{3} on 2009-06-01
Hello,

I'm currently working on building a small personnal shell account server based on Ubuntu Server 9.04, and I've installed several applications like irssi, elinks, etc on it. I've set the system language to french by default, but it seems elinks doesn't use the locale files even if [language-pack-fr-base](http://packages.ubuntu.com/fr/jaunty/language-pack-fr-base) is installed. I ve figured out that the elinks.mo file from /usr/share/locale-langpack/fr/LC_MESSAGES/ requires to be located in /usr/share/locale/fr/LC_MESSAGES/, otherwise elinks doesn't seems to use it.

Maybe I'm skipping a step, but could someone guide me in a cleaner solution to fix this little annoyance?

Thanks a lot!

m-p{3}

---

### Post by m-p{3} on 2009-06-10
Ok, I guess nobody knows..

---

