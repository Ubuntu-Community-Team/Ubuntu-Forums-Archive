---
title: "Change Proxy server"
date: 2010-03-29
forum: Server Platforms
---

### Post by popsZA1 on 2010-03-29
In the 9.1 server install you can specify a proxy server for updates. 
How do you change the proxy after the install?
There must be a config file somewhere but where?

Thanks

---

### Post by Ryan Dwyer on 2010-03-29
Edit the entries in /etc/apt/sources.list.

---

### Post by popsZA1 on 2010-03-29
Thanks for the reply Ryan but there is no reference to my old proxy server in this file.

Paul

---

### Post by Twinnie on 2012-01-10
I just spent a while working on this so let me leave this here.

When you enter the proxy settings during the install you aren't entering system wide proxy settings, you're just entering settings for apt-get. You can change the settings in /etc/apt/apt.conf and if you're anything like me you need to prepend your proxy config with http://.

FYI, to get into it type:

cd /etc/apt
sudo nano apt.conf

If you need to enter system wide proxy settings you can find plenty of instructions knocking around, start by looking at bash.bashrc.

---

