---
title: "PPTP server with encrypted user passwords"
date: 2014-01-16
forum: Server Platforms
---

### Post by kevpatts2 on 2014-01-16
Hey all,

Is it possible to do this? The PPTP guide [here]("https://help.ubuntu.com/community/PPTPServer") implies that all PPTP user passwords will be in the clear, which isn't secure enough for my purposes.

Kevin

---

### Post by SeijiSensei on 2014-01-16
Must you use PPTP, which has known vulnerabilities?  I'd suggest [OpenVPN]("http://openvpn.net/") instead.  You can install it from the repositories.

Even if you're supporting Windows users, they can install the OpenVPN client for Windows.

---

