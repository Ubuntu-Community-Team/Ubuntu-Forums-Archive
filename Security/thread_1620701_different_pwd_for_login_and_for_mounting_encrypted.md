---
title: "different pwd for login and for mounting encrypted /home"
date: 2010-11-13
forum: Security
---

### Post by newboyo on 2010-11-13
Hi,

I've just reinstalled my box with an encrypted home (used the encrypt home option when installing).

I have a query in this regard -

suppose I lose the box. Won't it be possible for someone to drop into root, reset my passwd and then access my /home.

Is there anyway of having a different passwd for accessing /home?

Thanks


New


p.s my ~ is on a different partition from /.

---

### Post by NIN101 on 2010-11-13
> suppose I lose the box. Won't it be possible for someone to drop into root, reset my passwd and then access my /home.

Altough I am not really familiar with the tool used in ubuntu to encrypt the home directory, i think it's ecryptfs, the answer is: No. Your home is encrypted with your password - not "access protected". The key for the cipher algorithm is your password(well probably not plaintext). He can change the password, but he cannot access your files. It wouldn't make sense to encrypt a home directory if it would be possible to access the data by replacing your password. 


> Is there anyway of having a different passwd for accessing /home?

Yes. I don't know how to do it with ecryptfs. You might take a look at [truecrypt]("http://truecrypt.org"). It could be _probably_ not easy for beginners. If you still wanna do this, you have to read some howtos on truecrypt.

---

### Post by FuturePilot on 2010-11-13
No. Your login password is used to decrypt another passphrase that is used to decrypt your data. So even if someone forcibly changed your password they still wouldn't be able to access your data since they would still need to know your original password. See here for more info. [http://blog.dustinkirkland.com/2009/02/how-encrypted-home-ecryptfs-works.html]("http://blog.dustinkirkland.com/2009/02/how-encrypted-home-ecryptfs-works.html")

---

### Post by newboyo on 2010-11-13
Thank you for your posts. Indeed it is as you say.

I did drop into root and change my passwd, but got an ICE authority error and some other errors, which basically (to my eyes anyway) said that there is no home to mount.

Now I can be sure that my secret to eternal life will be safe.:)

Rgds


New

---

