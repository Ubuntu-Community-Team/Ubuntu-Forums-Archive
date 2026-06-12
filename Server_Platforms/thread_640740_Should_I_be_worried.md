---
title: "Should I be worried?"
date: 2007-12-14
forum: Server Platforms
---

### Post by christhemonkey on 2007-12-14
Looking through the auth.log on my home server (running ubuntu 7.04) today, i found these entries:

```
Dec 14 06:25:03 server su[23544]: Successful su for nobody by root
Dec 14 06:25:03 server su[23544]: + ??? root:nobody
Dec 14 06:25:03 server su[23544]: (pam_unix) session opened for user nobody by (uid=0)
Dec 14 06:25:03 server su[23544]: (pam_unix) session closed for user nobody
Dec 14 06:25:03 server su[23569]: Successful su for nobody by root
Dec 14 06:25:03 server su[23569]: + ??? root:nobody
Dec 14 06:25:03 server su[23569]: (pam_unix) session opened for user nobody by (uid=0)
Dec 14 06:25:03 server su[23569]: (pam_unix) session closed for user nobody
Dec 14 06:25:03 server su[23574]: Successful su for nobody by root
Dec 14 06:25:03 server su[23574]: + ??? root:nobody
Dec 14 06:25:03 server su[23574]: (pam_unix) session opened for user nobody by (uid=0)
Dec 14 06:25:03 server su[23574]: (pam_unix) session closed for user nobody
Dec 14 06:25:03 server su[23580]: Successful su for nobody by root
Dec 14 06:25:03 server su[23580]: + ??? root:nobody
Dec 14 06:25:03 server su[23580]: (pam_unix) session opened for user nobody by (uid=0)
Dec 14 06:25:03 server su[23580]: (pam_unix) session closed for user nobody
Dec 14 06:25:03 server su[23582]: Successful su for nobody by root
Dec 14 06:25:03 server su[23582]: + ??? root:nobody
Dec 14 06:25:03 server su[23578]: Successful su for nobody by root
Dec 14 06:25:03 server su[23578]: + ??? root:nobody
Dec 14 06:25:03 server su[23578]: (pam_unix) session opened for user nobody by (uid=0)
Dec 14 06:25:03 server su[23582]: (pam_unix) session opened for user nobody by (uid=0)
Dec 14 06:25:33 server su[23582]: (pam_unix) session closed for user nobody
Dec 14 06:25:33 server su[23578]: (pam_unix) session closed for user nobody

```


Nobody in my house was awake let alone using the server at 6:25 this morning.

Is this something to be worried about?

If any more information is needed please let me know.

EDIT: Upon further checking this appears to be a daily occurrence at 6:25.

---

### Post by Total_Biscuit on 2007-12-14
Probably nothing at all to be worried about because the nobody user is deliberately harmless, though don't be tempted to delete this user as it will quite likely break something.  There's a nice little explanation of nobody here: [http://books.google.com/books?id=wOGUuoHUyAEC&pg=PA69&dq=nobody+user&lr=&sig=-JD-mEIK3M5VSw6IGS8uYYVSxlY](http://books.google.com/books?id=wOGUuoHUyAEC&pg=PA69&dq=nobody+user&lr=&sig=-JD-mEIK3M5VSw6IGS8uYYVSxlY).    If you're curious aobut what's running at 06:25 each day then take a look at the scripts in /etc/cron.daily.

---

### Post by christhemonkey on 2007-12-14
Ok thankyou, that is reasurring.

---

