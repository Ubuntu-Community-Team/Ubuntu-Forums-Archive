---
title: "Downloading updates offline"
date: 2005-04-08
forum: Repositories &amp; Backports
---

### Post by marbleheadman on 2005-04-08
I'm running Ubuntu on a relatively old i386 laptop (300 MHz) that I'm not connecting to the Internet.  I'd like to run KDE on it (or at least get libraries that will allow me to run KDE apps on it) for both usability and efficiency reasons.  I'm still using 4.10; which packages/libraries should I download from archive.ubuntu.com and copy onto the machine in order to run KDE?

---

### Post by mendicant on 2005-04-08
I think the KDE stuff is only available under hoary.  If you'd like to run it anyhow, go to a hoary machine, and download/use apt-rdepends to generate a list of the dependencies of kubuntu-desktop.  Something like:

% apt-rdepends kubuntu-desktop | cut -f 4 | sort | uniq

Note that apt-rdepends is in universe.

---

### Post by mendicant on 2005-04-08
Oh, I forgot to add: then use aptitude download to download everything.  I just ran it, and it actually looks like you want:

% apt-rdepends kubuntu-desktop | cut -d ' ' -f 4 | sort | uniq

---

