---
title: "Encrypt tar files during the tar"
date: 2009-02-16
forum: Server Platforms
---

### Post by any.linux12 on 2009-02-16
Hi!

I want to know if it is possible to encrypt a file with a password during the tar. Such than when I tar something (like a backup of my system) I do it at night and I don't need to encrypted after it is done.

Thanks in advance

---

### Post by iponeverything on 2009-02-16
last time I checked tar had no capacity to encrypt itself.

It's easy enough to encrypt any file (including a tar)

see: [http://snippets.dzone.com/posts/show/341](http://snippets.dzone.com/posts/show/341)

---

### Post by any.linux12 on 2009-02-16
hummm ok. I tryed but gave me an error

Bad magic number

How do I set one?

---

### Post by iponeverything on 2009-02-16
encrypt:

tar -c directory | openssl des3 -salt > encrypted.tarfile

decrypt:

cat encrypted.tarfile |  openssl des3 -d -salt |tar -xv

---

### Post by any.linux12 on 2009-02-16
Very nice thanks. I have only one more question. What about size?? for a 40MB files is giving me 48MB and my goal is to use this with 150GB.

I tryed to change the extensions but still the same. Any idea??

---

### Post by iponeverything on 2009-02-16
Just add the flag to use compression:

encrypt:

tar -cj directory | openssl des3 -salt > encrypted.tarfile

decrypt:

cat encrypted.tarfile | openssl des3 -d -salt |tar -xvj

---

### Post by any.linux12 on 2009-02-16
cool man. Thanks a lot. Can you give me you bank number? to make a donnation :P

---

### Post by Skip Da Shu on 2009-06-17
the -cj will give you better compression
using -cz will run faster with a bit less compression

But what does the "-salt" do?  I'm not finding it in man openssl.

---

### Post by unkle_george on 2009-11-10
Old post, but here's what I found about -salt
[http://linux.die.net/man/1/enc](http://linux.die.net/man/1/enc)

The **-salt** option should **ALWAYS** be used if the key is being derived from a password unless you want compatibility with previous versions of OpenSSL and SSLeay. 
Without the **-salt** option it is possible to perform efficient dictionary attacks on the password and to attack stream cipher encrypted data. The reason for this is that without the salt the same password always generates the same encryption key. When the salt is being used the first eight bytes of the encrypted data are reserved for the salt: it is generated at random when encrypting a file and read from the encrypted file when it is decrypted.

---

