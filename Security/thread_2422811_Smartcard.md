---
title: "Smartcard"
date: 2019-07-13
forum: Security
---

### Post by Wolfsbane on 2019-07-13
Can someone point me to an updated tutorial on using smartcards with Ubuntu (or Linux in general).
It should cover setup of the card, and all configurations.

//Martin S

---

### Post by cruzer001 on 2019-07-13
I always thought of a smartcard as a credit card with built in processor.

Is this what you refer to?

---

### Post by Wolfsbane on 2019-07-13
Kind of - it's configurable so used for logins.

---

### Post by cruzer001 on 2019-07-13
I see.  This is something I am not familiar with, but am willing to investigate from a linux standpoint.

Could you provide a reference (link) to this smartcard?

---

### Post by uRock on 2019-07-13
Are you talking about CAC cards? [https://help.ubuntu.com/community/CommonAccessCard](https://help.ubuntu.com/community/CommonAccessCard)

---

### Post by Wolfsbane on 2019-07-13
Like that yes, but it doesn't use PKCS#11 it's a OpenPGP card.
Maybe I can use parts of that doc.

This is 5 years old and doesn't correspond to what i get when trying to do this: [https://anthon.home.xs4all.nl/rants/2014/setting_up_an_openpgp_smartcard_with_gnupg/](https://anthon.home.xs4all.nl/rants/2014/setting_up_an_openpgp_smartcard_with_gnupg/)

---

### Post by uRock on 2019-07-13
One of these may be more helpful for what you're doing. I have no experience with these cards, so can't offer much more insight.
[https://github.com/OpenSC/OpenSC/wiki/OpenPGP-card](https://github.com/OpenSC/OpenSC/wiki/OpenPGP-card)
[https://wiki.debian.org/Smartcards/OpenPGP](https://wiki.debian.org/Smartcards/OpenPGP)

---

### Post by Wolfsbane on 2019-07-14
Ah yeah thanks.
I worked with the cards several years ago, and have a stash at home - thought I'd use them for something.

---

### Post by sevendogs1337 on 2019-07-14
I have used smart cards on Linux, alas not for login, just for secure web sites. OpenSC, pcscd and ccid are all you need. Chromium will work but the instructions are a bit convoluted. Firefox is dead simple to set up so it uses the card. You can also set Linux up to login this way but again, I have not done it.

---

### Post by catman2 on 2019-07-28
> **Wolfsbane said:**
> Can someone point me to an updated tutorial on using smartcards with Ubuntu (or Linux in general).
It should cover setup of the card, and all configurations.

+1

---

### Post by uRock on 2019-07-29
> **catman2 said:**
> +1

Have you looked through the links I've posted? If you have and are having issues, then feel free to start a thread with what you're running into.

---

