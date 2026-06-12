---
title: "exim redirect local mail to user's email address"
date: 2007-05-12
forum: Server Platforms
---

### Post by rmjb on 2007-05-12
Hello I have exim4 installed and I have the replacement of the sender address working fine, i.e. if my local user sends an email to a public address, then exim will replace the local user's name in From:, Sender: and Reply-To: with the matching email address from /etc/email-addresses.

I'm trying to set up exim now to forward or redirect locally delivered mail to the users' email addresses. This is so that messeges from anacron that get sent to root (which is aliased to my username in /etc/aliases) will end up in my public email inbox. In essence I want to automatically replace to To: address, or something to that effect

Any idea how I do this?

- rmjb

---

### Post by elst on 2007-05-12
IIRC, you just need to specify a full email address as the target in /etc/aliases, rather than a username, and there isn't actually anything else required.

---

