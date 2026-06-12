---
title: "Webmin Passwords and Users"
date: 2006-06-28
forum: Server Platforms
---

### Post by tim.n9puz on 2006-06-28
I just installed Webmin using Synaptic on a Breezy system. It appears to have installed and is running because I can get to the login screen via <https://localhost:10000/>. During the installation I was never prompted to enter a password or a username for webmin. The Webmin references on their site seem to assume a Red Hat system.

Q1: What is the default password and/or how do I set a username and password for webmin?

Q2: After failed attempts from a second local machine that IP address is now blocked from Webmin. How do I unblock it?

Thanks...

---

### Post by Spudgun on 2006-06-28
```
sudo /usr/share/webmin/changepass.pl /etc/webmin root <your passwordhere>
```

---

