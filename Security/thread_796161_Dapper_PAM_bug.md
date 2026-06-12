---
title: "Dapper PAM bug?"
date: 2008-05-16
forum: Security
---

### Post by masmad on 2008-05-16
I have one machine running 6.06 and I just tried to tighten the password policy. I noticed that even though the obscure-option is passed to PAM in /etc/pam.d/common-password, I can use "weak" passwords.

Of course, I'm not sure which passwords PAM should consider "weak", but I created a testuser and as that user running passwd allowed me to change the password to 11111 and aaaaa.

Can someone confirm this? Or tell me that I'm just doing something wrong ;)

Oh and I know about cracklib, but I'd like to know if I can live without it.

---

