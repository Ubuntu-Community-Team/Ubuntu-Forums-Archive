---
title: "Weird processes?"
date: 2012-03-23
forum: Server Platforms
---

### Post by d4m1r on 2012-03-23
Hey guys, I have a Ubuntu server from a hosting provider and I recently upgraded to Ubuntu 11.10 from 11.04 and now I have several new processes that I never had before...

smbd

nmbd

and

saslauthd


Can someone explain what those 3 are and what their services are actually called so I can service x stop them if they are not vital? Thanks in advance!

---

### Post by bubylou on 2012-03-23
smbd and nmbd are used by samba, which is used for windows networking. saslauth im not familiar with so i suggest googling it on your own unless someone ansers it.

---

### Post by 2F4U on 2012-03-23
The process saslauthd can handle authentication on behalf of other processes, e.g. postfix.

[http://linuxcommand.org/man_pages/saslauthd8.html](http://linuxcommand.org/man_pages/saslauthd8.html)

---

### Post by d4m1r on 2012-03-23
> **bubylou said:**
> smbd and nmbd are used by samba, which is used for windows networking. saslauth im not familiar with so i suggest googling it on your own unless someone ansers it.

Ok, thanks. Why would Samba come preinstalled on 11.10 but not on 11.04? I definitely don't need it so I'll be turning it off! Same goes for saslauth.

---

### Post by bubylou on 2012-03-23
im relatively sure neither of them come preinstalled with Ubuntu. I know samba has an option to install it when installing Ubuntu but doesn't autmotatically select it for you.

---

### Post by jerome1232 on 2012-03-23
> **bubylou said:**
> im relatively sure neither of them come preinstalled with Ubuntu. I know samba has an option to install it when installing Ubuntu but doesn't autmotatically select it for you.

This, or you may have installed some package that depended on them and pulled them in. Pay attention to what is being installed when you are installing things.

---

### Post by d4m1r on 2012-03-23
> **jerome1232 said:**
> This, or you may have installed some package that depended on them and pulled them in. Pay attention to what is being installed when you are installing things.


As I mentioned originally, I did not have any option in this. My host basically gave me the option to upgrade to 11.10 and I took it. For hosting providers, this is an automated install process.

Anyway, problem solved so thanks guys!

---

