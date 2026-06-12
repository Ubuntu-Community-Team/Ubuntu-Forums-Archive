---
title: "DropBox in private folder"
date: 2010-07-23
forum: Security
---

### Post by pzico on 2010-07-23
I have DropBox on Ubuntu Netbook syncing to private folder. I'm just concerned if this is secure, because what if someone steals my laptop and just removes private folder and makes a normal one with same name. Doesn't DropBox then sync everything to that unencrypted folder?

Is this risk real and if it is then how to avoid it?

---

### Post by yeleek on 2010-07-23
Encrypt your local hard disk - would mitigate what if the laptop is stolen

and

Use dropbox with a truecrypt volume - would mitigate what if someone got access to your drop box account, as the only thing dropbox would be backing up is an encrypted truecrypt file.

---

### Post by javierrivera on 2010-07-23
> Is this risk real and if it is then how to avoid it?

It is a real risk. But it's quite mitigated by DropBox itself.

Dropbox keeps a copy of your deleted files for a month (you can pay for longer retention). To see them on the web interface, when in the folder view, click on the show deleted files icon. You can always (well within a month) detach the stolen laptop from your DropBox account and restore the deleted files.

---

### Post by pzico on 2010-07-23
> **yeleek said:**
> Encrypt your local hard disk - would mitigate what if the laptop is stolen

and

Use dropbox with a truecrypt volume - would mitigate what if someone got access to your drop box account, as the only thing dropbox would be backing up is an encrypted truecrypt file.

I don't want to make dropbox to back up encrypted data, it would require setting up decryption on other platformss where I use me shared folder as well. Also I'm not afraid someone will catch my dropbox password or the dropbox security itself. I'm only afraid that the person who stole the laptop, would notice, AHAA, the guy was using private folder and dropbox, let's just make it unprivate (rm -Rf, mkdir) and wait until dropbox automatically syncs everything visible!

---

### Post by yeleek on 2010-07-23
Encrypt the local hard disk then - if robbed people can't get in at all.  And the files on dropbox would be in the clear.

---

### Post by pzico on 2010-07-23
> **yeleek said:**
> Encrypt the local hard disk then - if robbed people can't get in at all.  And the files on dropbox would be in the clear.

Yes, that's a choice. However my poor Atom processor is already on it's limit for not being fast enough :(

I was just hoping to hear that the concept of using Ubuntu private folders accompanied with DropBox would be secure for some reason. Probably I just need to choose some other way to make it secure, for example by taking some of your propositions for consideration.

---

