---
title: "Setup a proxy server to view web from work computer?"
date: 2010-08-02
forum: Server Platforms
---

### Post by tstack77 on 2010-08-02
I currently have my server setup with a web page and ssh. I am looking to find a way to access the internet from my work computer, but all proxies that I can find have been blacklisted...I can however access my home server webpage. Is it possible to create my own proxy so I can surf from my work laptop?

---

### Post by LightningCrash on 2010-08-03
You can SSH home and use the -D option to set up a local SOCKS proxy. Then just point your local browser to the SOCKS proxy localhost:1080

DNS requests will probably still be serviced locally, so don't be surprised when your sysadmins figure out what you're doing.

---

### Post by cariboo on 2010-08-03
We don't condone circumventing rules in the workplace. This thread is **Closed**.

---

