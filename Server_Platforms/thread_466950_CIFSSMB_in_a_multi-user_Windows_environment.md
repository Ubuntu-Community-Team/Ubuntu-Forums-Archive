---
title: "CIFS/SMB in a multi-user Windows environment"
date: 2007-06-07
forum: Server Platforms
---

### Post by telex4 on 2007-06-07
Hullo,

I'm trialling a Kubuntu machine in a Windows office. I've just got a test machine working with winbind and samba, so users can login and authenticate against our domain controller. Now I want to set-up the shares.

When users login in Windows they automatically find two mapped network drives: their personal folder (full control), and a shared drive with varied permissions throughout. I'd like something similar to happen on the Kubuntu machine but I can't work out how.

I've read through various bits of documentation for SMBFS and CIFS and I can see how to mount a drive permanently using one specific set of credentials (e.g. the administrator username and password). But that's no good - I want the machine to mount each user's shared folder and the public folder using that user's credentials when they login.

Is this possible? Can someone point me in the right direction?

---

### Post by telex4 on 2007-06-07
Incidentally, I get a nice list of available shares using "smbclient -L //biofile -k" but the kerberos option with smbmount only seems to work with samba servers and not with our Windows 2003 server (sigh), so that's not an option.

---

