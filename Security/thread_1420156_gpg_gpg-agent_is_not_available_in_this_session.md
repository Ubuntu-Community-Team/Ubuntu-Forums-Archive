---
title: "gpg: gpg-agent is not available in this session"
date: 2010-03-02
forum: Security
---

### Post by go_beep_yourself on 2010-03-02
What is causing this? I've been seeing it over and over again. What is going on?

gpg: gpg-agent is not available in this session

---

### Post by 1awesomeguy on 2010-06-04
Bump.

Getting the same error here. I'm trying the following:

```
user@ubuntu:~$ gpg -c --cipher-algo aes256 test.txt
gpg: gpg-agent is not available in this session
```

---

### Post by lariosa42 on 2010-11-14
Bump.

I'm getting the same issue.  I have a file, "my_file.tar.gz", and I want to encrypt it with:
```
gpg -c my_file.tar.gz
```
Running this command gives:
```
gpg: gpg-agent is not available in this session
```
Encryption/decryption seems to work fine, but the message is a little strange, and it would be good to know what it is referring to.

---

### Post by Primefalcon on 2010-11-24
hmmmm getting this myself, encryption decryption seems to work fine, it just prompts me for the pass in the cli rather than popping up the box though like it should

---

### Post by anthalamus on 2010-11-29
as stated here: [http://www.gnupg.org/documentation/manuals/gnupg/Invoking-GPG_002dAGENT.html](http://www.gnupg.org/documentation/manuals/gnupg/Invoking-GPG_002dAGENT.html), 
"gpg-agent is a daemon to manage secret (private) keys independently from any protocol.  It is used as a backend for gpg and gpgsm as well as for a couple of other utilities."

simply add option "--no-use-agent" to get rid of warning, unless you specifically want to use the GnuPG-Agent.

---

### Post by Primefalcon on 2010-12-06
> **anthalamus said:**
> as stated here: [http://www.gnupg.org/documentation/manuals/gnupg/Invoking-GPG_002dAGENT.html](http://www.gnupg.org/documentation/manuals/gnupg/Invoking-GPG_002dAGENT.html), 
"gpg-agent is a daemon to manage secret (private) keys independently from any protocol.  It is used as a backend for gpg and gpgsm as well as for a couple of other utilities."

simply add option "--no-use-agent" to get rid of warning, unless you specifically want to use the GnuPG-Agent.

Thing is I kind of liked that graphical box but yoh well.... no biggy I spose

Another problem I just noticed is there is no anymore for me to encrypt/decrypt documents on gedit and the plugin option is gone from preferences->plugins

---

