---
title: "GPG: how to sign and send key to a keyserver (misunderstand)"
date: 2012-05-03
forum: Security
---

### Post by 00oddn4a on 2012-05-03
Hi to all!
I say how sign a GPG key, that is
```
gpg --sign-key KEYUID
```
but if i would, for example, sign one of this key [http://pgp.cs.uu.nl/doc/top_1000.html]("http://pgp.cs.uu.nl/doc/top_1000.html"), assuming the first. then i download it. Import and sign with the previous command, then send it.
But in which address should i send the key? and if, for example, at  the same time that i import and sign the key , another person do the samething, he download the key not yet updated. He signs the key with its own sign and send the key too. At this point, if i have first sent the key before him, and he after send the key too, the key doesn't have my sign. but only its. Then, how can resolve this? Maybe i haven't explained. :oops: I wait for replies. Thanks.

---

### Post by ottosykora on 2012-05-03
dont worry,

the keys are copied from one server to other and the contenst are added, that means kind of merged there. So if two people signe one key and send it to the server, on the server you will find later a key with two sigs on it.

You can send it to any of the servers in fact, sooner or later it will appear on all (except the one of the pgp company itself)

BTW it is goind rather other way round, you download the key, sign it on your computer with your private key and then send it back to one of the servers. The servers have http interface, e-mail interface and hkp interface mostly.

---

### Post by vipulkumar7 on 2012-08-05
```
gpg --send-key keyserver keyserver.ubuntu.com <you-key-id>
```
:(

it's simple buddy :)

---

