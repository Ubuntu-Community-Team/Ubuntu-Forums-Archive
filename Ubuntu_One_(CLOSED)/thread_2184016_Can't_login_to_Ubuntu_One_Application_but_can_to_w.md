---
title: "Can't login to Ubuntu One Application but can to website ok"
date: 2013-10-27
forum: Ubuntu One (CLOSED)
---

### Post by jdpitt on 2013-10-27
HI I am trying to upload files to Ubuntu One but the application fails authentication with the correct credentials. If I visit the one website website the same credentials work fine. I am using 13.10 so I guess this might be a bug possibly? Any ideas anybody please?

---

### Post by Irihapeti on 2013-10-27
It sounds as though there's a mismatch between the credentials on the website and the credentials or token on your machine. You need to remove both and start again.

[LIST=1]
[*]Remove the reference to your machine at [https://one.ubuntu.com/account/machines/](https://one.ubuntu.com/account/machines/) (you need to be logged into the website)
[*]Remove any Ubuntu One tokens/keys on your computer using Passwords and Encryption Keys (or equivalent program).
[*]Either restart syncdaemon, or take the easy way out and reboot.
[/LIST]

---

### Post by jdpitt on 2013-10-27
Thanks alot that sorted it out for me.

---

### Post by Irihapeti on 2013-10-28
Good to know it's working!

Could you please mark the thread "solved". Thanks.

---

