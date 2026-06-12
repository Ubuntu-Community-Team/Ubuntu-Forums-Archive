---
title: "GPG key (authentification)"
date: 2005-06-02
forum: Ubuntu Backports
---

### Post by pato101 on 2005-06-02
I've followed instructions from ubuntuguide but I cannot authentificate backports packages:

```
gpg --keyserver wwwkeys.eu.pgp.net --recv-keys 1F41B907
gpg --armor --export 1F41B907 | sudo apt-key add -
sudo apt-get update

```

What's wrong?

---

### Post by Mez on 2005-06-02
Those instructions are for marillat.

BackPorts are still working on getting the authentication working, you should see it appear within the next week or so.

---

### Post by pato101 on 2005-06-02
[QUOTE=Mez]Those instructions are for marillat.

BackPorts are still working on getting the authentication working, you should see it appear within the next week or so.[/QUOTE]

I appreciate so much your help.

---

