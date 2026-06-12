---
title: "GPG error...."
date: 2005-03-30
forum: Repositories &amp; Backports
---

### Post by L1nVx on 2005-03-30
Hey i'm trying to get w32codecs becuase i want to intsall multimedia plug-in for firefox that way i can go to [www.purevolume.com](www.purevolume.com) and go to a band and use the pop-up player

i did everything they said but i get these errors.....when doing apt-get update

W: GPG error: [ftp://ftp.nerim.net](ftp://ftp.nerim.net) stable Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 07DC563D1F41B907
W: GPG error: [ftp://ftp.nerim.net](ftp://ftp.nerim.net) unstable Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 07DC563D1F41B907
W: GPG error: [ftp://ftp.nerim.net](ftp://ftp.nerim.net) testing Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 07DC563D1F41B907
W: You may want to run apt-get update to correct these problems

anyone have any ideas on how to fix this so i can get that w32codecs?

---

### Post by dusu on 2005-04-08
[QUOTE=L1nVx]Hey i'm trying to get w32codecs becuase i want to intsall multimedia plug-in for firefox that way i can go to [www.purevolume.com](www.purevolume.com) and go to a band and use the pop-up player

i did everything they said but i get these errors.....when doing apt-get update

W: GPG error: [ftp://ftp.nerim.net](ftp://ftp.nerim.net) stable Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 07DC563D1F41B907
W: GPG error: [ftp://ftp.nerim.net](ftp://ftp.nerim.net) unstable Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 07DC563D1F41B907
W: GPG error: [ftp://ftp.nerim.net](ftp://ftp.nerim.net) testing Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 07DC563D1F41B907
W: You may want to run apt-get update to correct these problems

anyone have any ideas on how to fix this so i can get that w32codecs?[/QUOTE]


Hi, it's all explained in step 6 of [http://ubuntuguide.org/#extrarepositories](http://ubuntuguide.org/#extrarepositories) that I reproduce hereafter. Do :
```
gpg --keyserver wwwkeys.eu.pgp.net --recv-keys 1F41B907
gpg --armor --export 1F41B907 | sudo apt-key add -
sudo apt-get update
```
then you'll be able to install the w32codecs (see [http://ubuntuguide.org/#codecs](http://ubuntuguide.org/#codecs) ).

---

