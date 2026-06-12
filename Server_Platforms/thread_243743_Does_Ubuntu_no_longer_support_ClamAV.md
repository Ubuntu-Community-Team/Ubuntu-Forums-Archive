---
title: "Does Ubuntu no longer support ClamAV?"
date: 2006-08-25
forum: Server Platforms
---

### Post by jimwillsher on 2006-08-25
Hi,

I'm running Dapper, and every day in my logs I see:

ClamAV update process started at Fri Aug 25 18:29:09 2006
WARNING: Your ClamAV installation is OUTDATED!
WARNING: Local version: 0.88.2 Recommended version: 0.88.4

I'm used to being one version behind (e.g. 0.88.3) but now we're TWO versions behind. Will there continue to be updates for ClamAv in the apt repositories? Or is it time to move on to something else?

(I run a mailserver, no GUI installed)

Many thanks,



Jim

---

### Post by lotusleaf on 2006-08-27
Right now, if you want the latest version of [ClamAV](http://www.clamav.net), you can download the source ([clamav-0.88.4.tar.gz](http://prdownloads.sourceforge.net/clamav/clamav-0.88.4.tar.gz?download) and compile it yourself (it's easy), get it from someone else who has a .deb of it, or request it in backports.

I build the latest version of ClamAV with each new release but I don't have a .deb handy at the moment.

---

### Post by jimwillsher on 2006-08-27
Many thanks for the tips.

Seems strange that a security-related application, available in the official repositories, isn't kept up to date.



Jim

---

### Post by socceroos on 2008-01-17
I couldn't agree more.

---

