---
title: "Home directory encryption and remote access questions"
date: 2015-11-16
forum: Security
---

### Post by ColinBrough on 2015-11-16
I have a number of machines running various flavours of Ubuntu. I've just installed xubuntu 15.10 on a netbook. As I take the machine out and about and there is sensitive work data on it, I want encryption. As the machine is also used by another user who I don't want to have access to the encryption key I've selected home directory encryption rather than full drive encryption.

To facilitate backups, remote logins, etc, I have ssh setup on the netbook and my main desktop, with ssh keys on both machines to allow unprompted file copy and login between desktop and netbook when they are both on the home LAN.

This is all working fine.... except that when the netbook is first turned on, if I haven't logged in, ssh or scp remote access asks for a password on first connection. On second and subsequent connections it doesn't ask. I'm presuming this is because on first connection ~/.ssh/ is encrypted and not yet accessible. Once a login has happened the ~/.ssh is available for subsequent authorisation checks.

First question - is what I've deduced above what is actually happening?

Second question - how does that then affect automatic backups to a server? My work are insisting on sensitive data being encrypted, so at next OS upgrade I'll want to have desktop and server use some encryption scheme - but in such a way that backups can be made without prompting for a password...

Thanks

Colin

---

### Post by TheFu on 2015-11-16
Whole disk encryption supports 8 decryption slots.  No need to share a single key.  Mine is setup for a ridiculously long passphrase and for a pin+crypto-key password.
**cryptsetup** is the tool.

> First question - is what I've deduced above what is actually happening?
I don't believe that is what is happening.  It didn't behave that way when I was using HOME directory encryption. Yes, a login is necessary to decrypt the userid $HOME, which was the primary reason I stopped using that.  In a multi-user environment, that was unacceptable.

BTW, I don't use passwords for network logins.  That is what ssh-keys are about.  For backups¸ use a "pull" methodology with a key.  For system-level backups, we need a higher-privileged userid anyway, not some end-user account.

A solid understanding of Unix userids is necessary. It is very elegant as a solution, while not risking security because the backup account will only run from cron. It doesn't get a password and no remote*access through it is allowed. It connects to other systems over ssh but only runs backups, nothing else. There are ways to lock it down further, if necessary.  Allow 1 sudo cmd and nothing else.

---

