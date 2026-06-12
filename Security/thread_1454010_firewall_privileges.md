---
title: "firewall privileges"
date: 2010-04-14
forum: Security
---

### Post by get2gether2010 on 2010-04-14
Hello everyone,

From user account i added for auto start-up at boot the firewall (firestarter), though upon login to desktop found a message stating the obvious. So would anyone here be kind enough to give me some time and explain how i go about this? I don't mind having to give my password to make policy changes, etc, but would like to be able to have the firewall up and running upon login to my user account.

Thanks, Steve. :)

---

### Post by OpSecShellshock on 2010-04-14
Firestarter (which is no longer supported, btw) is not the firewall itself, but is actually a configuration tool for the real firewall (iptables). That's always running, with or without Firestarter.

---

### Post by cdenley on 2010-04-14
Since the firestarter interface requires root privileges, and is no longer maintained, running it at boot or login is a horrible idea.

---

### Post by bodhi.zazen on 2010-04-14
> **cdenley said:**
> Since the firestarter interface requires root privileges, and is no longer maintained, running it at boot or login is a horrible idea.

+1

You are by far better off running the following commands:

```
sudo apt-get purge firestarter
sudo ufw enable
```

A better question is why do you feel you need a firewall ? What is it you are trying to accomplish.

A default installation of Ubuntu has no significant open ports , so a firewall adds little to your over all security.

If you are wanting to monitor your network traffic there are better tools then firestarter.

---

