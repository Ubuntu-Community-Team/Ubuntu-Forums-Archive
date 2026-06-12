---
title: "S/Key single-use passwords for OpenSSH"
date: 2006-04-06
forum: Server Platforms
---

### Post by sybren on 2006-04-06
Hi folks,

[INDENT]*[SIZE="1"]For those who don't know S/Key: it's a protocol that enables you to securely log in from an insecure box. It uses single-use passwords that you can generate in advance and take with you, or calculate when needed on a trusted PDA. This means that if there is a password sniffer on the box you use to log in, it only sniffs a password that's valid only once.[/SIZE]*
[/INDENT]

How can I use S/Key authentication with OpenSSH? Before I installed Ubuntu on my server, I used Gentoo, which required a recompile of OpenSSH to enable S/Key. Is there any package for Ubuntu that I can install to enable S/Key? Or do I have to rebuild OpenSSH in order to do that?

---

