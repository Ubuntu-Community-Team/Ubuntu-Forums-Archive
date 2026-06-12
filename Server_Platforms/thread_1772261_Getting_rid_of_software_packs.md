---
title: "Getting rid of software packs"
date: 2011-05-31
forum: Server Platforms
---

### Post by tapi0n on 2011-05-31
Yesterday I was tinkering on my postfix/dovecot setup and decided I was in such a mess it would be better to  just get rid of the whole thing and start over.

So I found someone who mentioned using 
 
```
apt-get delete postfix dovecot
```.

I get prompted to delete the files, clearing up xx space on my hard disk. I continue answering Y to the question to keep going. I get a message saying the removal was completed.

But when logging in now and reinstalling postfix and dovecot I got the same configurations I had yesterday.

Is there some explenation for the configs still being on the machine?

---

### Post by CharlesA on 2011-05-31
Purge it:

```
sudo apt-get purge *packagename*
```

EDIT: I tried apt-get delete on a lucid box and got back:

E: Invalid operation delete

I'm thinking they meant "remove" which keeps the config files, purge purges the config files.

---

### Post by tapi0n on 2011-05-31
Ah yes could have been *remove *too. Couldn't remember 100% what it was. 

Does purge also remove the packs? Or is it just to get rid of the remaining files? I'll definitely look into it when I get home tonight.

Cheers

---

### Post by CharlesA on 2011-05-31
Purge removes the package as well as any config files.

---

