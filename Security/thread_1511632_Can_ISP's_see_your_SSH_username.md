---
title: "Can ISP's see your SSH username?"
date: 2010-06-17
forum: Security
---

### Post by bedhead75 on 2010-06-17
I know that SSH is meant to be an encrypted protocol, but if you start an ssh session at the terminal with "ssh [email]username@yourfavorite.server.com[/email]", how much of that can your ISP see?  Can they see the username you're using and the name of the server you're ssh'ing into?  Does encryption occur only after you've logged in?

---

### Post by HermanAB on 2010-06-17
The ISP can only see the name and IP address of the server.

You can check with tcpdump, wireshark or ngrep.

---

### Post by anomie on 2010-06-17
Unless you're being subjected to a MITM attack*, only the remote host sees your ssh username.

---

* openssh has mechanisms in place to warn you about this, assuming you've already successfully connected to the remote host in the past.

---

