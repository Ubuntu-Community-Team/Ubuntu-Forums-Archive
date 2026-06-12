---
title: "Public/private key security"
date: 2009-10-19
forum: Security
---

### Post by gemmahenchmen on 2009-10-19
I have some data that I want to keep totally locked-down from the Internet. I have a couple of old machines lying around with enough storage to hold the files but not enough processing power to be useful. If I put my sensitive files on the old computer and lock down the wireless connection between this machine (Running Ubuntu and occasionally Vista for games) that is connected to the Internet and the old one with a public/private key connection (making the old one an open ssh server) so that it can't be cracked by anyone with a wireless computer.

My only concern about this is the chance of a hacker getting access to my new computer and being able to access the server because he/she has access to my private key. Even if I lock it down with a passphrase, a brute force attack could penetrate. I have a hardware firewall but don't have any crypto set up on my laptop above what comes straight away with Ubuntu. 

If you know any, it'd be great if someone pointed me to any sites on security against wireless or internet attacks and any opinions on my plan.

Thanks in advance

---

### Post by kevdog on 2009-10-20
Can you rephrase your question perhaps, because I'm not quite following you.

---

### Post by falconindy on 2009-10-20
Require a private key to login to the SSH server and disallow password logins. Don't lose your private key -- keep it in only certain locations (your /$HOME/.ssh and a flash drive). If you think your key has been compromised, just generate a new one. Make a habit of rotating the key every so often (a week? a month?) if you're still paranoid.

---

