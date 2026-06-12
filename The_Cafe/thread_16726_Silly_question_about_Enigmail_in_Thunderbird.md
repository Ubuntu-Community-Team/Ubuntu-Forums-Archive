---
title: "Silly question about Enigmail in Thunderbird"
date: 2005-02-23
forum: The Cafe
---

### Post by Sam on 2005-02-23
Ok, this one is pretty useless... I would like to know how to remove the comment (*Comment: Using GnuPG with Thunderbird - [http://enigmail.mozdev.org](http://enigmail.mozdev.org)*) in the PGP signature in Thunderbird.

```
-----BEGIN PGP SIGNATURE-----
> Version: GnuPG v1.2.5 (GNU/Linux)
> Comment: Using GnuPG with Thunderbird - http://enigmail.mozdev.org
>
> [snip]
```
Thank you...

---

### Post by Zundfolge on 2005-02-23
Go to your account settings (go to "Tools" menu, should be second from the bottom) and see if there is a signature attached.  It should be in the account settings dialog  box when you click on the account name ... you can just uncheck the box by "Attach this signature:"


If its not checked then the PGP program is putting it in and I have no idea how to get rid of it  :-s

---

### Post by Sam on 2005-02-23
Thank you for your reply. It was not that, but I found the answer.

I looked into OpenPGP Security in the Account Settings, then in the Advanced window there is the option "Do not add Enigmail comment in OpenPGP signature" in the Advanced tab...

Next time I will look twice before asking... :|

---

