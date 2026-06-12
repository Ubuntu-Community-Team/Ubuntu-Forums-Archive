---
title: "SSH - forgotten passphrase"
date: 2008-10-23
forum: Security
---

### Post by jmidgley on 2008-10-23
Yes, yes, I know. Stupid.

I have a Ubuntu server, and Ubuntu desktop running on another machine. I use PuTTY on the desktop to administer the server.

A while ago, I had a brief try at getting PuTTY to log in automatically, by generating keys and all that stuff. It would always ask me for the password anyway, which defeated the object but that's a different question.

Now, I've added a second server, installed SSH and am connecting to it via PuTTY, as before. Except that now I'm getting a message saying something like 'An application wants to unlock id_dsa - enter the password'. Needless to say, I've forgotten the passphrase, since nothing has asked me for it for months. If I hit 'Deny', I get in anyway, because it asks for a password on server 2!

What must I delete, reinstall, alter to fix this mess?

Many thanks
John

---

### Post by hyper_ch on 2008-10-23
create new keys on that server without password this time.

---

