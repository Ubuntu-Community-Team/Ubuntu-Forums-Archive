---
title: "Enable encryption after install"
date: 2009-07-05
forum: Security
---

### Post by Sims12345 on 2009-07-05
Is there a way to enable the encryption/password on boot option after installing Ubunutu 9.04 64bit? 

Is this encryption similar to what True Crypt does? 

Thanks

---

### Post by Dave_Connor on 2009-07-05
It is MUCH eaiser to reinstall and use an alternet to allow encryption, you can enable encryption after install but it is much more of a pain within the back area due to it being more over complex then needed to be.

---

### Post by Agent ME on 2009-07-05
Do you want per-user encryption or system-wide file-system encryption that asks for the password on boot?

If the first, then just enter in a terminal "sudo apt-get install ecryptfs-utils ; ecryptfs-setup-private". You now have a folder ~/Private which is automatically encrypted.

---

### Post by phr33k-dc on 2009-07-06
how do you delete the folder 'private' after you have made one?

---

### Post by Sims12345 on 2009-07-06
> **Agent ME said:**
> Do you want per-user encryption or system-wide file-system encryption that asks for the password on boot?


System wide with the password on boot

---

### Post by Kobalt on 2009-07-06
Then you should look towards LUKS.

---

### Post by jhaquo on 2010-07-01
Sorry for bringing back the dead but, i was wondering how to activate encryption on my home folder, like sugested when creating the first user? in 10.04

Also, is it any good to use?
It's a work computer with sometimes private documents (cv, docs, etc) and i would like to be sure no one can access it, even in admin.

Kind regards,
Jhaquo

---

### Post by GrantStoner on 2010-07-02
Do this for your /home directory [http://blog.dustinkirkland.com/2009/06/migrating-to-encrypted-home-directory.html](http://blog.dustinkirkland.com/2009/06/migrating-to-encrypted-home-directory.html)

And then to encrypt the swap partition do this:
```
encryptfs-setup-swap
```

you should be good to go.

---

