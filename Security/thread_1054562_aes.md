---
title: "aes"
date: 2009-01-29
forum: Security
---

### Post by num on 2009-01-29
Hello,

I am using the following the following tutorial to install dm-crypt and encrypt my hard drive:

[http://news.softpedia.com/news/Encrypted-Ubuntu-7-04-61312.shtml](http://news.softpedia.com/news/Encrypted-Ubuntu-7-04-61312.shtml)

I am using Ubuntu 8.10 Desktop Edition and when I do the following command:

```
modprobe aes
```

I get the following error:

```
WARNING: Error inserting padlock_aes (/lib/modules/2.6.27-7-generic/kernel/drivers/crypto/padlock-aes.ko): No such device
root@ubuntu:/home/ubuntu# modprobe dm-crypt
root@ubuntu:/home/ubuntu# modprobe aes
WARNING: Error inserting padlock_aes (/lib/modules/2.6.27-7-generic/kernel/drivers/crypto/padlock-aes.ko): No such device
root@ubuntu:/home/ubuntu# modprobe dm-mod
root@ubuntu:/home/ubuntu# modprobe sha256
WARNING: Error inserting padlock_sha (/lib/modules/2.6.27-7-generic/kernel/drivers/crypto/padlock-sha.ko): No such device
root@ubuntu:/home/ubuntu#
```

Can anyone please help me?

---

### Post by Tubes6al4v on 2009-01-30
So you are trying to have an encrypted root file system, right? I would suggest that if you are not familiar with this, just download the alternate CD and use LUKS to encrypt it. The tutorial you are looking at is quite dated. There are better ones for 8.04 and 8.10.

Here is one in the community documentation: [https://help.ubuntu.com/community/EncryptedFilesystemOnIntrepid](https://help.ubuntu.com/community/EncryptedFilesystemOnIntrepid)

---

### Post by hyper_ch on 2009-01-30
I agree with the previous poster. New versions (from 8.04) have encryption incorporated into the alternate install cd. Rather use that.

---

### Post by num on 2009-01-30
is all this included in 8.10 or do I have to install the rest of the stuff?

---

### Post by Tubes6al4v on 2009-01-31
It is in 8.10, just make sure you download the alternate CD. I think the link is on the right in the download page.

---

### Post by teddks on 2009-02-01
The specific error there is that you don't have a VIA CPU with the Padlock features. Those features include hardware AES, but you don't have that chip, hence why the device is not found.

You shouldn't have to do any of that, though. Just use the alt. CD like everyone's suggested. :)

---

