---
title: "What is the begin PGP signature ?"
date: 2010-03-05
forum: Security
---

### Post by jase21 on 2010-03-05
I see that some mails send by people contains the

-----BEGIN PGP SIGNATURE-----
Version: GnuPG v1.4.10 (GNU/Linux)
--
--
--
-----END PGP SIGNATURE-----

At the bottom the message. Is it a digital signature. 
I have made an OpenPGP Key in the process of signing the Ubuntu Code of Conduct. So how can I use my key to produce such PGP signature seen at the end of the mail?

---

### Post by psusi on 2010-03-05
I use the enigmail plugin for thunderbird.  What mail client do you use?

---

### Post by rookcifer on 2010-03-05
You will have to use a e-mail client that supports GPG.  On Gnome, use Thunderbird.  If on KDE, I like to use Kmail.

There are official Ubuntu wiki pages that explain how to setup GPG on various e-mail clients.  Just google it.

And in order to have "---Begin PGP Message---" appear inside your emails, you will have to use the "inline" delivery method.  Otherwise the signature gets put as an attachment to the email.  In fact, an attachment is really the way most people prefer it as "inline" is now deprecated.

---

