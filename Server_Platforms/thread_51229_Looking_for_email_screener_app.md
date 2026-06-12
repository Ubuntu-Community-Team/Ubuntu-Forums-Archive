---
title: "Looking for email screener app"
date: 2005-07-23
forum: Server Platforms
---

### Post by grofaz on 2005-07-23
Anyone know of a good app utility that can screen email on the server before downloading onto your PC?? Thanks!

---

### Post by spanishwasabi on 2005-07-27
What for?

Maybe procmail...

G

---

### Post by grofaz on 2005-07-27
So I don't have to download my email only to discover 18 advertisements for penis enlargement pills! That's what for.

---

### Post by spanishwasabi on 2005-07-29
The maybe spamassasin is more suited for you, if you have access to the server of course.

I just tried an amavis-clamav-spamassasin solution for spam and antivirus filtering in my server, and it seems to work pretty well.

If you are not root on the server, then you may think of asking your mail admin to install it, or else try a .procmail with a local installation of spamassassin if you have an account o the server.

Good luck,

G

---

### Post by LordHunter317 on 2005-07-29
Use Mailscanner, which I prefer over amavis.  It does roughly the same things.

---

