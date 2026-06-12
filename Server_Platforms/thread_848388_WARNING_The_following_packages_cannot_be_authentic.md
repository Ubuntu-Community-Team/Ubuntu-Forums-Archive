---
title: "WARNING: The following packages cannot be authenticated! webmin"
date: 2008-07-03
forum: Server Platforms
---

### Post by trtech on 2008-07-03
I have a Ubuntu 8.04 box that I administer remotely via ssh and Webmin. It's configured to update every day using apt. Every day I get an email that says:

[INDENT]/etc/cron.daily/apt:
WARNING: The following packages cannot be authenticated!
  webmin[/INDENT]

How can I authenticate the webmin package or stop the warning some other way?

Thanks!

---

### Post by trtech on 2008-07-08
I solved this by installing **debian-keyring** and **debian-archive-keyring**.

[http://packages.ubuntu.com/hardy/debian-keyring](http://packages.ubuntu.com/hardy/debian-keyring)
[http://packages.ubuntu.com/hardy/debian-archive-keyring](http://packages.ubuntu.com/hardy/debian-archive-keyring)

```
sudo apt-get install debian-keyring debian-archive-keyring
```

---

