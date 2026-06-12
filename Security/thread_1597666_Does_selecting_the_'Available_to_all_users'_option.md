---
title: "Does selecting the 'Available to all users' option in Network Mgr mess with security?"
date: 2010-10-15
forum: Security
---

### Post by wah fun on 2010-10-15
To avoid having to input a password for the keyring each time I connect to the net via wireless, I enabled the 'Available to all users' option in Network Manager. Now, my question is this. Are the 'users' it refers to just those created on this machine? Would a drive-by be able to use my network without entering the password?

thx

---

### Post by The Cog on 2010-10-15
What the available to all users setting does is to change where the login information is stored. Instead of being stored in your personal settings, it is stored in /etc/NetworkManager/system-connections. These settings are then available to all users of the computer, not just you, so if you log out and a different user logs in, they too will have access to the wireless network. In fact, the wireless network will connect even before anyone is logged in. These configuration files are only readable by root, but they are not encrypted.

---

### Post by bodhi.zazen on 2010-10-15
> **wah fun said:**
> To avoid having to input a password for the keyring each time I connect to the net via wireless, I enabled the 'Available to all users' option in Network Manager. Now, my question is this. Are the 'users' it refers to just those created on this machine? Would a drive-by be able to use my network without entering the password?

thx

In this case, users means anyone logged into your machine.

IMO this is no a significant security risk. If they can log in, they already have access.

Access to your wireless network by others is governed on your router.

---

### Post by The Cog on 2010-10-16
Actually, it seems odd to me that anyone might ever have thought of making the network connectivity a per-user setting. I have always thought of network connectivity as part of the computer infrastructure, as with cabled connection. So I always make my settings "available to all users".

---

