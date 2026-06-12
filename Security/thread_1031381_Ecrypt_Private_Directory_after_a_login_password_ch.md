---
title: "Ecrypt Private Directory after a login password change"
date: 2009-01-05
forum: Security
---

### Post by jaynes on 2009-01-05
In Ubuntu 8.10 I set up a Private directory. It worked fine, automatically mounting when I logged in. Then I changed my login password. Now it doesn't mount automatically when I login. I have to run 'sudo mount -t ecryptfs ~/.Private ~/Private' in a terminal. I assume this has to do with the fact that to unwrap the passphrase that is in .ecryptfs/wrapped-passphrase I still need to use my old login password. I just don't know what to do to get the automounting to use the new login password.

Thanks for any info.

Will

---

### Post by xltrigger on 2009-01-19
I have this same problem and found your thread googling for a solution. If somebody knows how to fix this please let us know.

---

### Post by billjoie on 2011-08-17
Normally, changing your password does not cause any problem with the automount of the Private directory. Your situation is probably due to the fact that you changed your account password as root.

It is explained here: [http://bodhizazen.net/Tutorials/Ecryptfs#Password](http://bodhizazen.net/Tutorials/Ecryptfs#Password)

"If you change your password as root (or if root changes your password), the passphrase to mount your encrypted home will NOT be updated. This is good news in that it keeps root from accessing your data simply by changing your user's password and logging in as your user."

Just change your password again (not as root), and all should be fine.

---

### Post by stortford on 2011-08-28
Hi billijoie

:KSI can't thank you enough for your post September 22 2010 @9:23 p.m. You saved my sanity. Following your notes I was able to recover 16 GiB of data files I thought were gone for ever.

Your help and that of others like you are of immense value to the whole Community. THANK YOU.

May you live long and prosper!!!!

---

