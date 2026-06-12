---
title: "Ecryptfs"
date: 2009-07-16
forum: Security
---

### Post by zxcv on 2009-07-16
Hello!

I've been trying to figure out how ecryptfs works in Ubuntu Jaunty.

Installed Ubuntu from a (beta)alternate CD and put my /home on a separate partition. Love Ubuntu for being so automagic ;) But sometimes I also want to run Gentoo, so I put Gentoo on a separate partition but would like to share the same /home partition for both OSes.

Could someone give some advice how ecryptfs is set from the alternate CD? I just cant figure out how to mount it inside Gentoo. :( Its a laptop and I cant afford to run it without encryption incase it gets stolen or something.

Please advice,

---

### Post by unutbu on 2009-07-16
Hello zxcv!

First off, note that ecryptfs does not give you complete protection in case your laptop gets stolen. Even if /home is encrypted, parts of its contents may "leak out" into /tmp, /var, or a swap partition. 

This faq contains much interesting information on this topic: [http://ecryptfs.sourceforge.net/ecryptfs-faq.html#deployment](http://ecryptfs.sourceforge.net/ecryptfs-faq.html#deployment)

For this reason, you may want to think about using LUKS instead of eCryptfs. (Here is a guide on how to do that [http://kuparinen.org/martti/comp/ubuntu/en/cryptolvm.html](http://kuparinen.org/martti/comp/ubuntu/en/cryptolvm.html)).

On the other hand, if you are satisfied with the level of protection that ecryptfs affords, and have an eCryptfs-Private directory, then on Gentoo, you may be able to decrypt it with a command like this:

```
sudo mount -t ecryptfs -o key=passphrase,ecryptfs_cipher=aes,ecryptfs_key_bytes=16,ecryptfs_passthrough=no,ecryptfs_enable_filename_crypto=yes ~/.Private ~/Private
```

For more info on ecryptfs, see also:
[http://bodhizazen.net/Tutorials/Ecryptfs/](http://bodhizazen.net/Tutorials/Ecryptfs/)
[https://help.ubuntu.com/community/EncryptedPrivateDirectory](https://help.ubuntu.com/community/EncryptedPrivateDirectory)

---

### Post by bodhi.zazen on 2009-07-16
Just a heads up, performing a full encryption using LUKS is quite easy with the Alternate CD.

[http://news.softpedia.com/news/Encrypted-Ubuntu-8-04-85271.shtml](http://news.softpedia.com/news/Encrypted-Ubuntu-8-04-85271.shtml)

My advice is to share a LUKS data partition rather then sharing $HOME. There are tons (well not tons) of config files you really do not need to share across OS in $HOME.

You can always ln -s or mount --bind /data/music $HOME/music

---

### Post by XCan on 2009-07-17
How does LUKS or ecryptfs perform between upgrades? I was too afraid about everything breaking during upgrade to use either when I installed Jaunty on a new computer.

---

### Post by scorp123 on 2009-07-17
> **XCan said:**
> How does LUKS or ecryptfs perform between upgrades? Been there, done that. No problem there.

---

### Post by unutbu on 2009-07-17
It's always good to have backups. That is doubly true when using encryption. Practice restoring from encrypted backups so you'll know what to do if something goes wrong.
Even though upgrading usually goes without a hitch, sometimes things do not go as expected. And as Warren Buffett likes to say, "It's only when the tide goes out that you learn who's been swimming naked."

---

### Post by scorp123 on 2009-07-17
> **unutbu said:**
> It's always good to have backups. +1 on that one. Always make backups. ... Just in case. Better have them and not need them than the other way around. :twisted:

---

