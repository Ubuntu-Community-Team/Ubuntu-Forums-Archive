---
title: "(un)security of eCryptfs ?"
date: 2011-02-04
forum: Security
---

### Post by kapetr on 2011-02-04
Hello,

I'm new in using of eCryptfs, but the first test do not let me
sleep.

I'm using Ubuntu 10.10 - standard installation.

Let see my steps:

1. I mount (as root or with sudo) my first eCryptfs in user1 subdirs
with passwd1.
2. the key is ONLY in keyring @u of root, NOT by user1 - but:

user1 can create and read files in that FS (file system) root can
the same.

?? How can user1 work with files in this FS even if user1 has no key
in his keyring ?!!!

3. root clears kis keyring with keyctl clear @u, but the FS is
usable further ??!!

4. root unmounts this FS and mounts it again with another password
passwd2

5. user1 can not see content of previous files (but can see
names/size in "ls") and can create new files - AGAIN WITHOUT key

5. user1 adds passwd1 with ecryptfs-manager - so passwd2-key is in
@keyring of root and passwd1-key is in keyring of user1

6. user1 can now see content of ALL previous files ??!! root too
??!!

7. and now! another user - user2 can also see all files, even if he
has no keys !!

HOW IS IT POSSIBLE ??

[B]I thing, that access to content of encrypted files should have ONLY
the one, who has key of proper password in his keyring - and NOBODY
ELSE.[/B]

But this is by eCryptfs not so. Once anybody adds passwdX to his
keyring, than anybody else !!! can read files encrypted with this
password. Even if this user deletes this key from his keyring !!!

I can not believe my eyes ?!

Please HELP.

--kapetr

---

### Post by movieman on 2011-02-05
> **kapetr said:**
> HOW IS IT POSSIBLE ??

Ecryptfs only protects the files when they're not mounted; once you mount them with the decryption password anyone with relevant permissions can read them.

If you use encrypted home directories then no-one else can read your files when you're not logged in, but once you log in they're decrypted and anyone with relevant permissions can read them.

---

### Post by kapetr on 2011-02-06
Thank You for replay.

Unfortunately You are right.
I had one times more read FAQs and there is told +- the same.

But - **this behaviour is VERY confusing !**

Why are there user/process/thread keyrings at all ? When if e.g. someone 1. times uses his key, then from this time point anybody can read by this key encoded key of files can read them ?

For what is good _keyctl clear @u_ at all ? If the key is used further ?

What I had expect is IMHO logical. And I do not understand why is it not so made ?!

The problem is that documentation of eCryptfs is minimal and doc. of keys management is NONE at all :-(


Also - I give up eCryptfs and I will use **encfs** - good documented, logical, easy to use, without dark secrets - and if I mount my dir, then only I can see and work with this files (not even root can access them).

--kapetr

---

### Post by DZ* on 2011-02-06
> **kapetr said:**
> I give up eCryptfs and I will use **encfs** - good documented, logical, easy to use, without dark secrets - and if I mount my dir, then only I can see and work with this files (not even root can access them).

Root can access your files while the encfs directory is mounted by doing "su - YourLogin". This is no different from eCryptfs.

---

### Post by kapetr on 2011-02-07
Of course: root can - sorry me.
And sudoers probably too. Fortunately other standard and system users are not automatically sudoers (in admin or sudo groups). So just root (==me) is danger :-)

But the keys and keyrings used by eCryptfs is still a "black box" for me. And in security "things" I don't want to use something, what I do not (+-) understand.

--kapetr

---

