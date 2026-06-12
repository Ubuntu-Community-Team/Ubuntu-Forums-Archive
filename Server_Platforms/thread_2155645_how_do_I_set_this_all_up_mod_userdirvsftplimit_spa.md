---
title: "how do I set this all up mod_userdir/vsftp/limit space on webpages?"
date: 2013-06-18
forum: Server Platforms
---

### Post by kustomjs on 2013-06-18
Hey Guys
I am looking for some help on setting all this up as mod_userdir/vstfp (locking user into there own home directory)/ limit user on how much MB he/she can have to upload for there personal website because I want to limit them to 50Mb of storage space?

---

### Post by TheFu on 2013-06-19
Don't know how to do it with apache. I'd use quotas.

---

### Post by chris56 on 2013-08-20
Hi, 

i wrote a tutorial about this

[http://infofreund.de/user_quotas_vsftpd_en/](http://infofreund.de/user_quotas_vsftpd_en/)

like TheFu said, you should use filesystem quotas, but for this, you have to mount the device with some options.

Regards
Chris

---

