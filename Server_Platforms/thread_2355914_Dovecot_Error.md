---
title: "Dovecot Error"
date: 2017-03-18
forum: Server Platforms
---

### Post by nightfrost123 on 2017-03-18
Hi guys, I tried installing dovecot and it went well but when i started it, it shows an error about dovecot.socket and see systemctl stuff. But when i use sudo service dovecot restart, it doesn't show any error.

Is it okay to ignore that? I was going on with the squirrelmail installation and wonder will something bad happened? Thx in advance!

---

### Post by SeijiSensei on 2017-03-18
If this is 16.04 or later, you need to use the systemd utilities.

```
sudo systemctl restart dovecot.service
```

---

