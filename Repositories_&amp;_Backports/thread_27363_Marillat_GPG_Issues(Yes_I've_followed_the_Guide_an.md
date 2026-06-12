---
title: "Marillat GPG Issues(Yes I've followed the Guide and Wiki)"
date: 2005-04-15
forum: Repositories &amp; Backports
---

### Post by dewey on 2005-04-15
I just reformatted, using the new hoary iso for i386. I used the repos from ubuntuguide.org, and pasted in the lines to get marillat's key. However, I get errors.
```
dewey@ubuntu:~$ gpg --keyserver wwwkeys.eu.pgp.net --recv-keys 1F41B907 gpg: can't open `/home/dewey/.gnupg/pubring.gpg'
gpg: keydb_get_keyblock failed: eof
gpg: no writable keyring found: eof
gpg: error reading `[stream]': general error
gpg: Total number processed: 0
```
```
dewey@ubuntu:~$ gpg --armor --export 1F41B907 | sudo apt-key add - gpg: can't open `/home/dewey/.gnupg/pubring.gpg'
gpg: WARNING: nothing exported
gpg: key export failed: file open error
gpg: no valid OpenPGP data found.
```
```
dewey@ubuntu:~$ ls /home/dewey/.gnupg
gpg.conf           pubring.gpg   secring.gpg
private-keys-v1.d  pubring.gpg~  trustdb.gpg
```
I suspect it's a permissions problem, but I don't know much about apt-get and keys, so I'm not sure. Help is much appreciated.

---

### Post by rolo on 2005-04-16
[QUOTE=dewey]I just reformatted, using the new hoary iso for i386. I used the repos from ubuntuguide.org, and pasted in the lines to get marillat's key. However, I get errors.
```
dewey@ubuntu:~$ gpg --keyserver wwwkeys.eu.pgp.net --recv-keys 1F41B907 gpg: can't open `/home/dewey/.gnupg/pubring.gpg'
gpg: keydb_get_keyblock failed: eof
gpg: no writable keyring found: eof
gpg: error reading `[stream]': general error
gpg: Total number processed: 0
```
```
dewey@ubuntu:~$ gpg --armor --export 1F41B907 | sudo apt-key add - gpg: can't open `/home/dewey/.gnupg/pubring.gpg'
gpg: WARNING: nothing exported
gpg: key export failed: file open error
gpg: no valid OpenPGP data found.
```
```
dewey@ubuntu:~$ ls /home/dewey/.gnupg
gpg.conf           pubring.gpg   secring.gpg
private-keys-v1.d  pubring.gpg~  trustdb.gpg
```
I suspect it's a permissions problem, but I don't know much about apt-get and keys, so I'm not sure. Help is much appreciated.[/QUOTE]

Same here and I have tried many times......

---

### Post by dewey on 2005-04-16
Alright, it was a permissions error.  Somehow, root became the owner instead of me. A simple
```
$sudo chown USERNAMEHERE /home/USERNAMEHERE/.gnupg/pubring.conf
```
Fixed it all right up.

---

