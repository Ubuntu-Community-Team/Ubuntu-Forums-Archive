---
title: "SSH login with key doesn't work."
date: 2024-02-13
forum: Server Platforms
---

### Post by WhiteTigerIT on 2024-02-13
I have a VPS partially pre-configured with Ubuntu Server 22.04, updated.
I would like via SSH to be accessible only with one key.
I configured the /root/.ssh/authorized_keys file with my key.
I copied this file to the /home/user/.ssh folder
I assigned rights 600 on the files and 700 on the .ssh folders.
I configured Putty with my private key.

Yet when I call the server, instead of requesting the password on the private key, the login request appears.
Then if I use root obviously it won't accept the password, but if I use the user I log in without using the key.

I don't understand why, I always use the same configuration.
The only difference is that I didn't use "ChallengeResponseAuthentication no" because it wasn't included in the default file and I read online that it's no longer used.

Furthermore, the writing appears before and after the banner
[B]Pre-authentication banner message from server:
[/B]MY BANNER
[B]End of banner message from server
[/B]which I don't like and would like to avoid.

This is my sshd_config.

Where am I wrong?

```
Port 22
LoginGraceTime 2m
PermitRootLogin no
PubkeyAuthentication no
AuthorizedKeysFile    .ssh/authorized_keys .ssh/authorized_keys2
PasswordAuthentication no
PermitEmptyPasswords no
# ChallengeResponseAuthentication no
KbdInteractiveAuthentication no
UsePAM yes
X11Forwarding yes
PrintMotd no
Banner /etc/ssh/banner-pre-login.txt
```


=== Solved ===
The error is PubkeyAuthentication no

---

### Post by TheFu on 2024-02-14
Create a ~/.hushlogin file.  Existing is enough.

---

