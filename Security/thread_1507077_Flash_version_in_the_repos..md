---
title: "Flash version in the repos."
date: 2010-06-11
forum: Security
---

### Post by lovinglinux on 2010-06-11
Today I read [a thread](http://ubuntuforums.org/showpost.php?p=9443767&postcount=1) in which the user says all versions of flash on the repositories are 10.1.53.64, but mine are still 10.0.45.2. I have already updated the software sources and the mirror server is up to date.

I also checked the package at [packages.ubuntu.com](http://packages.ubuntu.com/search?searchon=names&keywords=flashplugin) and it is still 10.0.45.2.

So what's wrong?

---

### Post by squaregoldfish on 2010-06-11
I don't think anything is wrong. The 64-bit version of the flash player is still at the alpha stage, and therefore isn't kept in step with the official releases.

Steve.

---

### Post by lovinglinux on 2010-06-11
> **squaregoldfish said:**
> I don't think anything is wrong. The 64-bit version of the flash player is still at the alpha stage, and therefore isn't kept in step with the official releases.

Steve.

Actually, Adobe dropped support for 64bit entirely. They say they will provide support int the future tho. Nevertheless, the repositories do not install the 64bit, but the 32bit with the nspluginwrapper, so it should be the latest version.

---

### Post by squaregoldfish on 2010-06-11
When did that happen? It must have been recent, as the last 64-bit alpha is dated Feb 2010.

---

### Post by howefield on 2010-06-11
> **squaregoldfish said:**
> When did that happen?

In the last few hours, maybe yesterday.

[http://labs.adobe.com/technologies/flashplayer10/64bit.html](http://labs.adobe.com/technologies/flashplayer10/64bit.html)

---

### Post by lovinglinux on 2010-06-11
> **squaregoldfish said:**
> When did that happen? It must have been recent, as the last 64-bit alpha is dated Feb 2010.

Yes it is. You can still download it if you have the direct link, but it is no longer available at Adobe's page. Instead you receive [a message that the beta is closed](http://labs.adobe.com/technologies/flashplayer10/64bit.html).

---

