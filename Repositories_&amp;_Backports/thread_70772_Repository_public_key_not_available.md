---
title: "Repository public key not available"
date: 2005-10-01
forum: Repositories &amp; Backports
---

### Post by eirik on 2005-10-01
Hi,
Whenever i add a new repository found at apt-get.org i get the following error when reloading the package list in Synaptic package manager: "W: GPG error: [ftp://ftp.nerim.net](ftp://ftp.nerim.net) etch Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 07DC563D1F41B907."
Can anyone tell me what I'm doing wrong?

in addition, can anyone tell me where to find a good beginner's guide on how to install *.deb and *.tar packages?

thanks!

---

### Post by aysiu on 2005-10-01
[QUOTE=eirik]
Whenever i add a new repository found at apt-get.org i get the following error when reloading the package list in Synaptic package manager: "W: GPG error: [ftp://ftp.nerim.net](ftp://ftp.nerim.net) etch Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 07DC563D1F41B907."
Can anyone tell me what I'm doing wrong?[/quote] Follow the instructions [here](http://www.mepislovers-wiki.org/index.php?title=Public_key_not_available_error). I think I read somewhere once that it's generally a good idea [to enable Ubuntu's own extra repositories](http://ubuntuguide.org/#extrarepositories) instead of adding Debian ones. Can anyone confirm this?

> 
in addition, can anyone tell me where to find a good beginner's guide on how to install *.deb and *.tar packages? For debs ```
sudo dpkg -i packagename.deb
``` For .tar.gz, unzip it (this can be down graphically... I don't remember the command line stuff off the top of my head) and then ```
sudo ./configure
sudo make
sudo make install
```

---

### Post by eirik on 2005-10-02
I get this when following the instructions:

me@mycomputer:~$ sudo gpg --keyserver wwwkeys.eu.pgp.net --recv-keys 9F8E2A98D1A4EDE5
gpg: key D1A4EDE5: public key "Klaus Ethgen <Klaus@Ethgen.de>" imported
gpg: Total number processed: 1
gpg:               imported: 1  (RSA: 1)

me@mycomputer:~$ sudo gpg --armor --export D1A4EDE5 | apt-key add -
gpg: no writable keyring found: eof
gpg: error reading `-': general error
gpg: import from `-' failed: general error

Help anyone?

---

### Post by GTvulse on 2005-10-02
[quote=aysiu] Follow the instructions here. I think I read somewhere once that it's generally a good idea to enable Ubuntu's own extra repositories instead of adding Debian ones. Can anyone confirm this?[/quote]

Absolutely correct. Using the Marillat repositories in particular is the surefire way to break your system to the point of needing to reinstall and start from zero.

---

