---
title: "wrong command = security issue"
date: 2009-02-10
forum: Security
---

### Post by sblanzio on 2009-02-10
Hi!
unfortunately, while i was trying to change permissions to every file in a subdirectory, i filled the following [COLOR="Red"]**WRONG command**[/COLOR]:

```
sudo chown -R username / 
```

after 1/2 second I realized it was a mistake and pressed CTRL+C but it was late.

Every time i use a sudo command now it says:

```
sudo: /var/run/sudo owned by uid 1000, should be uid 0
```

So I guess i changed the owner of an undefined amount of files/directories.

How do I revert this thing to give item the right permission? Is it possible?
Thank you very much.

sblanzio

---

### Post by surj08 on 2009-02-10
use

su 

and change it back as root

---

### Post by The Cog on 2009-02-10
Unfortunately not all files should be owned by root, so chown -R root / won't fix it. I think you really need to use recovery mode to back up your user data and then reinstall. You can fix the ownership of the users files either before making teh backup or after restoring it onto the new system. Sorry, but it's the only way to reliably fix things.

---

### Post by sblanzio on 2009-02-10
> **The Cog said:**
> Sorry, but it's the only way to reliably fix things.

uhm, I guessed that. 

Thank you very much!
sblanzio

---

### Post by bodhi.zazen on 2009-02-10
> **the cog said:**
> unfortunately not all files should be owned by root, so chown -r root / won't fix it. I think you really need to use recovery mode to back up your user data and then reinstall. You can fix the ownership of the users files either before making teh backup or after restoring it onto the new system. Sorry, but it's the only way to reliably fix things.

+1

---

