---
title: "SSH Port (Weird Issue)"
date: 2010-01-29
forum: Server Platforms
---

### Post by squeeky on 2010-01-29
Im competent at using linux and ive just got a vps. I wanted to change the port and i have done in the ssh_config file. I reloaded ssh and now it listens on both !!! what on earth is going on ?

Squeeky

---

### Post by HermanAB on 2010-01-30
Howdy,

Comment out port 22 in sshd_config and restart sshd.

---

