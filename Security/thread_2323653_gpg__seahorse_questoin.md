---
title: "gpg / seahorse questoin"
date: 2016-05-07
forum: Security
---

### Post by fugu2 on 2016-05-07
Since I installed 16.04, i've been have loads of trouble restoring my personal gpg keys. I got them imported, sort of, but they are not showing up in seahosre at all, and when I use the cli, the trust of my personal key is set at unknown. 
```

$ gpg --edit-key 
gpg> trust
5
gpg> save
gpg> quit

```
but it still returns 
```
trust: ultimate      validity: unknown
```
and 
```

[ unknown] (1). Full Name 

```
and any time I go to use it requires user interaction saying this key is not trusted.
Any idea how to fix this?

---

### Post by fugu2 on 2016-05-09
So, I can't figure out what is wrong. It sounds like I'm the only one having import problems with seahorse. I'm close to trying to reinstall 16.04 in hopes that it fixes the problem, unless someone else know uninstall/reinstall the whole integrated seahorse/gpg system without munging up the whole everything.

---

### Post by DuckHook on 2016-05-09
Did you export your secret key or just the public key? It takes some digging down into the key menus to get at the secret key. It's a common error for users to just export their public key, which is all that the top menu does. When you then go to import it into Xenial, you will just be importing your public key.

---

### Post by untrustytahr on 2016-05-10
> **fugu2 said:**
> So, I can't figure out what is wrong. It sounds like I'm the only one having import problems with seahorse. 

   No, you’re not.  I cannot speak to your secret key issue as I only have public keys in my ring for checking signatures, but seahorse definitely is not displaying public keys.  A bug has been filed ( [https://bugs.launchpad.net/ubuntu/+source/seahorse/+bug/1577198](https://bugs.launchpad.net/ubuntu/+source/seahorse/+bug/1577198) ).   
 
 
 It looks to me that seahorse imports using gpg(1) but displays what’s in gpg(2) keyring.  You should verify that in seahorse that under view - > show any is selected.  If the public keys aren’t displaying, you can add your name to the bug by selecting the “this affects me too” line of the bug.  Hopefully it will get picked up by the maintainers.

---

### Post by DuckHook on 2016-05-10
> **untrustytahr said:**
> ...A bug has been filed...seahorse imports using gpg(1) but displays what’s in gpg(2) keyring.  You should verify that in seahorse that under view - > show any is selected.  If the public keys aren’t displaying, you can add your name to the bug by selecting the “this affects me too” line of the bug.  Hopefully it will get picked up by the maintainers.Thanks for bringing this to light, untrustytahr (ha-ha.. interesting choice of handle ;))

@fugu2

The workaround for this bug is in the linked launchpad bug report. As untrustytahr suggests, until the bug is fixed, import your keys using the command line:```
gpg2 --import-keys /path/to/file
```It is very important to invoke gpg2 and not just gpg. And like untrustytahr, I hope you also report the bug.

Interesting note: all of my keys show up in Seahorse. But then, I simply network upgraded from my old Trusty Tahr install. In my case, Trusty has been trusty! :)

---

### Post by fugu2 on 2016-05-11
Yeah, thats exactly what was wrong. it was a gpg vs. gpg2 issue. That was not very clear at all that there are 2 separate systems running, someone messed that up in designing this release. And theres no feedback within seahorse as to which its using. But your right, its using gpg2, once I imported the key its working just fine. Thank you all very much for your help.

---

