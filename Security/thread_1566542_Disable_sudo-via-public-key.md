---
title: "Disable sudo-via-public-key?"
date: 2010-09-02
forum: Security
---

### Post by Prendi on 2010-09-02
Hi, I just set up my server to allow logins over ssh via public key (which is what I want). However, now sudo is also working without prompting for a password (which is entirely not what I want).

So how do I disable sudo-via-public-key without disabling ssh-via-public-key?

My point is not so much to gain additional security against attackers stealing a private key, but to make sudo'ing users (including myself) aware of the fact that they are about to gain root rights and every one of their actions may have severe consequences.

---

### Post by Bachstelze on 2010-09-02
sudo always asks for a user's password (unless you messed with PAM). If it doesn't, something is very wrong. Did you for example assign a blank password to the user?

---

### Post by Prendi on 2010-09-02
Seems you're right. What got me confused is that ubuntu doesn't **re**ask for the root password on ssh-sessions, even if I close one ssh session and open another one.

So if I open a ssh-session via public-key authentication, and then sudo, I have to enter my password. However, when I close the ssh connect and establish a new ssh connection from the same machine shortly after, I don't need to enter my password for sudo that time. Feels insecure, but I guess it should be safe.

Anyway, thanks for your clarification.

---

### Post by FuturePilot on 2010-09-02
> **Prendi said:**
> Seems you're right. What got me confused is that ubuntu doesn't **re**ask for the root password on ssh-sessions, even if I close one ssh session and open another one.

So if I open a ssh-session via public-key authentication, and then sudo, I have to enter my password. However, when I close the ssh connect and establish a new ssh connection from the same machine shortly after, I don't need to enter my password for sudo that time. Feels insecure, but I guess it should be safe.

Anyway, thanks for your clarification.

That would be the sudo timeout. See [here]("https://help.ubuntu.com/community/RootSudoTimeout")

---

