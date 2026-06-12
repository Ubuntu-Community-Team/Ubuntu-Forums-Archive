---
title: "How to login to my work environment anywhere in a lan?"
date: 2012-09-03
forum: Server Platforms
---

### Post by cnplane on 2012-09-03
hi there, I saw some guy can login to his work environment with his account anywhere in a Ubuntu lan, the point is he can back to his work environment including opened apps, browsers,etc.
someone could telll me how to do it? thanks much.

---

### Post by HermanAB on 2012-09-04
SSH
Screen
VNC

---

### Post by cnplane on 2012-09-04
Thanks to your response.
But I prefer thinkign its NFS, LAMP or NIS sth. Could someone give some more advices? Thanks.

---

### Post by SeijiSensei on 2012-09-04
NFS+NIS was the traditional method for this on *nix networks.  The users' home directories reside on a central server running NFS, and NIS is used for authentication.  LDAP might provide the authentication mechanism in some installations these days.

---

### Post by cnplane on 2012-09-04
> **SeijiSensei said:**
> NFS+NIS was the traditional method for this on *nix networks.  The users' home directories reside on a central server running NFS, and NIS is used for authentication.  LDAP might provide the authentication mechanism in some installations these days.

hi,thanks a lot.

---

