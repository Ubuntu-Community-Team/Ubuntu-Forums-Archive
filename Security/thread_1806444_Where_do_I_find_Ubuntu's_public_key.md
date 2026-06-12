---
title: "Where do I find Ubuntu's public key?"
date: 2011-07-17
forum: Security
---

### Post by sneakyimp on 2011-07-17
I've been studying up on [securing apt](https://help.ubuntu.com/community/SecureApt#How%20to%20Find%20a%20Key) and other security type stuff and I find myself wondering **where is Ubuntu's public key?**

For example, I want to instantiate an Amazon EC2 instance of Ubuntu from [one of these images](http://uec-images.ubuntu.com/releases/natty/release).  I see that there are checksums and gpg signatures, but I have no idea where to find the key I should use to validate them.  As I understand it, this public key should be well known and in a public place so that all can have access to it.

---

### Post by bodhi.zazen on 2011-07-17
Depends on the repository, each repo should list the location and name of the key.

See:

[https://help.ubuntu.com/community/SecureApt#How%20to%20Find%20a%20Key](https://help.ubuntu.com/community/SecureApt#How%20to%20Find%20a%20Key)

[http://blog.edseek.com/archives/2007/03/17/apt-key-gpg-key-import-on-ubuntu-and-debian/](http://blog.edseek.com/archives/2007/03/17/apt-key-gpg-key-import-on-ubuntu-and-debian/)

---

### Post by sneakyimp on 2011-07-20
I've read those links and they don't tell me where a particular repository's key is located.  Still wondering if there is some public place where OFFICIAL keys are listed and clearly marked.

I've managed to check my apt keyring and locate which keys came with my install, and I've managed to look these up at [http://keyserver.ubuntu.com](http://keyserver.ubuntu.com), but I still find myself wondering how official these are.

---

### Post by bodhi.zazen on 2011-07-20
> **sneakyimp said:**
> I've read those links and they don't tell me where a particular repository's key is located.  Still wondering if there is some public place where OFFICIAL keys are listed and clearly marked.

I've managed to check my apt keyring and locate which keys came with my install, and I've managed to look these up at [http://keyserver.ubuntu.com](http://keyserver.ubuntu.com), but I still find myself wondering how official these are.

[https://help.ubuntu.com/community/Repositories/Ubuntu#Authentication%20Tab](https://help.ubuntu.com/community/Repositories/Ubuntu#Authentication%20Tab)

> "Authentication keys" are usually obtained from the maintainer of the software repository. The maintainer will often place a copy of the authentication key on a public key server such as [www.keyserver.net](www.keyserver.net).

If you are interested, read about public gpg key servers

[http://www.gnupg.org/gph/en/manual.html#AEN464](http://www.gnupg.org/gph/en/manual.html#AEN464)

> There are several popular keyservers in use around the world. The major keyservers synchronize themselves, so it is fine to pick a keyserver close to you

So you can find the keys on most any public gpg key server, and the ubutnu key server , [http://keyserver.ubuntu.co](http://keyserver.ubuntu.co), is NOT the ONLY place to find the keys.

apt-get will identify the key for you, so I have never looked for a master list for Ubuntu. I suppose you could do a google search or search the gpg key server.

See:
[http://www.rossde.com/PGP/pgp_keyserv.html#search](http://www.rossde.com/PGP/pgp_keyserv.html#search)

[http://wiki.debian.org/SecureApt](http://wiki.debian.org/SecureApt)

---

### Post by sneakyimp on 2011-07-21
Thanks for the link on Authentication. I've since made some progress in understanding how this all works so that makes sense. At the moment, I'm more concerned about verifying the two keys that already live in my apt keyring in a freshly installed Ubuntu, namely 437D05B5 and FBB75451.

I found them at keyserver.ubuntu.com, but somethings puzzle me:
* The site does not serve its results via HTTPS.  This seems like it could easily be remedied.
* Am I to understand that some 40 people have signed these keys? [QV the mit keyserver results](http://pgp.mit.edu:11371/pks/lookup?search=0xFBB75451&op=vindex).
* Sadly, I don't know a single one of those signers:
```

sneakyimp@machine:~$ GET "http://pgp.mit.edu:11371/pks/lookup?op=get&search=0x46181433FBB75451" | gpg --import
gpg: key FBB75451: public key "Ubuntu CD Image Automatic Signing Key <cdimage@ubuntu.com>" imported
gpg: Total number processed: 1
gpg:               imported: 1
gpg: no ultimately trusted keys found
sneakyimp@machine:~$ gpg --check-sigs --fingerprint FBB75451
pub   1024D/FBB75451 2004-12-30
      Key fingerprint = C598 6B4F 1257 FFA8 6632  CBA7 4618 1433 FBB7 5451
uid                  Ubuntu CD Image Automatic Signing Key <cdimage@ubuntu.com>
sig!3        FBB75451 2004-12-30  Ubuntu CD Image Automatic Signing Key <cdimage@ubuntu.com>

39 signatures not checked due to missing keys

```

* what would stop any individual from creating 1 key and self signing it and then creating 40 other keys, self-signing those, and then signing the original key. Seems to me this process could be automated.

---

