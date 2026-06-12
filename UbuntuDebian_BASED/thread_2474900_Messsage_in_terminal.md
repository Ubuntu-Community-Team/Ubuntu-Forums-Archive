---
title: "Messsage in terminal"
date: 2022-05-11
forum: Ubuntu/Debian BASED
---

### Post by ray42 on 2022-05-11
What is this and how may I fix it?

Teamviewer was a download from Teamviewer's own site.

```

W: https://linux.teamviewer.com/deb/dists/stable/InRelease: Key is stored in legacy trusted.gpg keyring (/etc/apt/trusted.gpg), see the DEPRECATION section in apt-key(8) for details.

```

I believe it has been reporting since download.

---

### Post by vanadium on 2022-05-11
This way of handling keys is deprecated, because once that key is trusted, any repo could use that key, e.g. a malicious PPA that got hold of public and private key. In the new system, one key is attached to a specific repository.

You could (and probably should) leave that alone until this system does not anymore work and/or software providers changed the system. Otherwise, [here](https://askubuntu.com/questions/1398344/apt-key-deprecation-warning-when-updating-system/1398346#1398346) is how you could update the situation manually.

---

