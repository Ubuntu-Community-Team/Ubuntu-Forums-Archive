---
title: "Standard permission for pubring.gpg?"
date: 2014-03-27
forum: Security
---

### Post by cogset on 2014-03-27
I run into an issue trying to import a pgp key,the output of gpg was something like 
```
gpg: can't open `/home/user/.gnupg/pubring.gpg'

```
after noticing that in ~/.gnupg directory the files **pubring.gpg**,**pubring.gpg~ **and **secring.gpg** were owned by root and after examining some related threads on the forum,I've changed their ownership to my user id leaving the group to root
```
rw-------  1 user user 1139 Mar 23 13:01 pubring.gpg
rw-------  1 user  root 0 Jul 10 2013 pubring.gpg~
rw-------  1 user root  0 Jul 10  2013 secring.gpg
rw-------  1 user user 1200 Jul 10  2013 trustdb.gpg
```
is it the above correct or should I change the group "root" to "user" as well?

And,how come those files were owned by root? Why does that happen?
Should I look into something,security wise?

---

### Post by Dave_L on 2014-03-27
In my case, *all* the files in ~/.gnupg are user:user and have permissions 600 (rw-------).

I don't know how the owner became root.  Maybe you used sudo in a situation where it wasn't necessary?

---

### Post by cogset on 2014-03-27
You probably mean 600 ? or are they actually rwx------- ?

I don't remember using sudo with gpg/seahorse,but I may be wrong.

---

### Post by Dave_L on 2014-03-27
Sorry, I meant 600. I'll edit my previous post to fix that.

In any case, I don't see why any files in the home directory need to be owned by root or be in the root group. If 'root' needs to access the files there, it can do so regardless of the permissions.

---

