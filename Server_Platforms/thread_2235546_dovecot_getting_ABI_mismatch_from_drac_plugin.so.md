---
title: "dovecot getting ABI mismatch from drac_plugin.so"
date: 2014-07-21
forum: Server Platforms
---

### Post by Peter Howard on 2014-07-21
This appeared yesterday after doing a dist-upgrade on my 12.04 server.

Dovecot is now giving an ABI version error when trying to load drac_plugin.so in response to a mail client connecting.  From the log:

```
Jul 22 08:17:32 rhuiden dovecot: imap: Error: Module is for different ABI version 2.2.9 (we have 2.2.ABIv7(2.2.9)): /usr/lib/dovecot/modules//drac_plugin.so
Jul 22 08:17:32 rhuiden dovecot: imap: Fatal: Couldn't load required plugins
```

The installed packages:

```

pjh@rhuiden:~$ dpkg -l | grep dovecot
ii  dovecot-core                         1:2.2.9-1ubuntu2.1                          amd64        secure POP3/IMAP server - core files
ii  dovecot-imapd                        1:2.2.9-1ubuntu2.1                          amd64        secure POP3/IMAP server - IMAP daemon
ii  dovecot-pop3d                        1:2.2.9-1ubuntu2.1                          amd64        secure POP3/IMAP server - POP3 daemon
pjh@rhuiden:~$ 

```

I've done an apt-get purge and clean install of all three, to no effect.  Given drac_plugin.so is part of dovecot-core I'm not sure what I could have done wrong.  The same dovecot setup has been working fine for years.

All help appreciated, TIA.

---

### Post by Peter Howard on 2014-07-21
Actually, I'm no longer on 12.04 - I was resolving a dpg/apt problem, and it appears to have taken me from 12.04 to 14.04.  While I was planning to do that upgrade, I was waiting for the 14.04.1 point release.

Anyway, that should make the package versions make sense.  And apt-get upgrade shows nothing pending.  But the problem still occurs.

---

### Post by Peter Howard on 2014-07-22
Looks like it's a bug in the package meaning the drac plugin has the wrong version string.

Bug sumitted [https://bugs.launchpad.net/ubuntu/+source/dovecot/+bug/1346740](https://bugs.launchpad.net/ubuntu/+source/dovecot/+bug/1346740)

---

