---
title: "PAM won't let users login, but root is OK [have workaround]"
date: 2012-04-17
forum: Security
---

### Post by Skaperen on 2012-04-17
I don't know whether this is the result of installing Xubuntu desktop edition, instead of server edition I normally use ... or because I'm using 12.04 Beta2 to get prepared for 12.04 LTS when it is released.  I can login just fine as user root.  This fails for non-root users and PAM is logging as the cause:
```
Apr 17 14:07:41 feynman sshd[2235]: Accepted publickey for root from fe80::225:90ff:fe14:c458%eth0 port 54068 ssh2
Apr 17 14:07:41 feynman sshd[2235]: pam_unix(sshd:session): session opened for user root by (uid=0)
Apr 17 14:11:14 feynman sshd[2619]: fatal: Access denied for user phil by PAM account configuration [preauth]
```I can't find any mention of "preauth" in the PAM configs.  So I don't know what that means.  Aside from PAM entries for a few new packages, the configuration is the same as on servers I have in which users can login OK.

The logins are via ssh using keys.  The authorized_keys files have the same keys.  Permissions are the same (755 for / /home /home/phil /home/phil/.ssh and 600 for /home/phil/.ssh/authorized_keys) on this new system that does not work and the old systems that work.

Basically I'm looking for an explanation of why PAM made the unexpected (wrong) decision on this new machine.  The logs are vague.  Logs should not be vague (user messages should be vague for security reasons, but not logs).

I can just change "UsePAM yes" to "UsePAM no" in the sshd config to make it work (tested it).  But I haven't had to do that before.  I'd like to find out what's wrong with the PAM config before disabling it "permanently".

---

### Post by AnojiRox on 2012-04-17
wow, you have a serious problem...  what's your workaround???

---

### Post by Skaperen on 2012-04-17
> **AnojiRox said:**
> wow, you have a serious problem...  what's your workaround???
"UsePAM no" in /etc/ssh/sshd_config.

The thing I think is so funny is that it has been letting root login all along.  If something changed in PAM in this latest version to make things "more secure", why lockout non-root users but let root login?  I would have thought a more secure default would have been the other way around.  I think it's just something goofed somewhere.  I just don't know if I did it or someone else.  This is different in that we are putting a desktop edition on a server, plus moving up to 12.04 (just getting ready with the Beta2, but final deployment is to be shortly after the LTS release).

---

