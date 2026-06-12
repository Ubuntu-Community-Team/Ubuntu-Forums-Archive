---
title: "Access control"
date: 2015-11-23
forum: Security
---

### Post by jeffjohn2 on 2015-11-23
Hi! I am seeking advice on limiting access to my LUbuntu PC to my remote home network.  I'm looking for firewall advice to block incoming access except from one fixed IP address.  Would this have any 'unforeseen consequences' in normal operation?  Thanks to all, Jeff

---

### Post by TheFu on 2015-11-23
Never use unencrypted, non-key-based, authentication, over the internet if you care about security.

That means using openvpn or ssh-based connections. These are secure enough to be left open to most of the world, unless only passwords are used for authentication. Keys are 1,000,000,000,000,000,000x more secure AND more convenient, so using a password really isn't good.

Use ssh/scp/sftp and fail2ban. Call it done.

With this setup, only 1 port needs to be open. Sure you can only allow inbound connections from 1 IP or 1 small subnet to further reduce the risks. With fail2ban I don't feel that is necessary. Different people have different levels of security requirements.

---

### Post by CharlesA on 2015-11-25
> **TheFu said:**
> Never use unencrypted, non-key-based, authentication, over the internet if you care about security.

That means using openvpn or ssh-based connections. These are secure enough to be left open to most of the world, unless only passwords are used for authentication. Keys are 1,000,000,000,000,000,000x more secure AND more convenient, so using a password really isn't good.

Use ssh/scp/sftp and fail2ban. Call it done.

With this setup, only 1 port needs to be open. Sure you can only allow inbound connections from 1 IP or 1 small subnet to further reduce the risks. With fail2ban I don't feel that is necessary. Different people have different levels of security requirements.

Just vouching for this. I ran a setup like that a long time ago. The only real reason I changed from having SSH open to the entire Internet to only allowing a few IPs was to reduce the log noise. The security is the same since I am using keys instead of passwords.

---

### Post by jeffjohn2 on 2015-11-25
Thanks for those wise comments; I concur and use ftps and IPSec vpn, but would still request coding for IP exclusion, please.

---

### Post by TheFu on 2015-11-25
Use ufw or gufw.  They are really easy.

---

