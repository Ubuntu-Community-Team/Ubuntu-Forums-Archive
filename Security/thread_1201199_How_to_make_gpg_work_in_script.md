---
title: "How to make gpg work in script?"
date: 2009-06-30
forum: Security
---

### Post by u-slayer on 2009-06-30
I had a script that used gpg to do simple file encryption. But after update my ubuntu, it is giving me pop up boxes and asking for recipients? I just want to encrypt a file with a password passed on the commandline, how do I do that?

```
$tarcmd | gpg --symmetric --encrypt --cipher-algo $encryption --passphrase "$($hash $keyfile | sed 's/ .*//')" - > $output
```

---

### Post by Agent ME on 2009-07-01
Generally it's considered a bad idea to put a passphrase directly in command line arguments, as it could be seen in the process list. Use the "--passphrase-file" option instead.

Back on topic: Your problem is the "--encrypt" part. This option makes it *encrypt to someone's private key*, but you have no recipients marked. Simply take off this part and it'll work. The "--symmetric" option does what you want by itself.

---

### Post by HermanAB on 2009-07-01
BTW, always compress data before encrypting it (it is impossible to compress afterwards).  Tar can do compression, but PGP also has compression switch.

---

### Post by u-slayer on 2009-07-01
> **Agent ME said:**
> Generally it's considered a bad idea to put a passphrase directly in command line arguments, as it could be seen in the process list. Use the "--passphrase-file" option instead


I tried using the --passphrase-file option:
$tarcmd | gpg --passphrase-file secret --symmetric --cipher-algo $encryption - > test

and it still prompts for a password. I found an ugly way to hack around this by creating a file descriptor for my file:

exec 8>secret
$tarcmd | gpg --batch --passphrase-fd 8 --symmetric --cipher-algo $encryption - > test
Edit: I just tried the above again, and now it won't work! This is getting frustrating. The below will always work however:
$tarcmd | cat secret - | gpg --batch --compress-level 0 --passphrase-fd 0 --symmetric --cipher-algo $encryption - > test


It works, I guess. Thanks for your help.

---

### Post by u-slayer on 2009-07-01
> **HermanAB said:**
> BTW, always compress data before encrypting it (it is impossible to compress afterwards).  Tar can do compression, but PGP also has compression switch.

Yeah, I noticed that. I disabled compression, so tat GPG wouldn't waste time trying to compress the same data twice. It's more efficient if tar handles the compression, because its using a seperate thread. Also, I can tell tar to use gzip, which is much faster.

---

### Post by slimx3m on 2009-11-22
thnx, this really helped me :)

---

