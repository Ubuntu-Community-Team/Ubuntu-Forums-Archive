---
title: "Encrypted home folder and DropBox"
date: 2010-03-09
forum: Security
---

### Post by PalapaGuy on 2010-03-09
Hi All,

I just installed 9.10 on my laptop and selected the option for home folder encryption.  I am running DropBox and placed the DropBox folder on my desktop (meaning it should be encrypted when I am logged out.)

So I have two questions:

1) Shouldn't this setup cause my DropBox files on the server to be encrypted?  Apparently they are not because they appear as unencrypted text using the DropBox Web interface.

2) If they ***were*** encrypted on the server (which doesn't appear to be the case right now), how would it be possible to share them with another client unless the encryption on both clients were set up identically?

Thanks.

---

### Post by ProfDecoy on 2010-03-09
Your files don't show up as being encrypted on Dropbox because to the application, the files are unencrypted.

The reason for this is that the encryption for your home directory is applied at the filesystem level and is decrypted when you log in.  If this didn't happen, you wouldn't be able to access any of your files within your home directory.

Since the dropbox application starts after you log in, it sees your files as being unencrypted, as it's running in the context of your user account (it can see/access what you can).

If you want to have files stored on Dropbox in an encrypted format, take a look at creating a Truecrypt container and storing your files in there.  Then you can sync the container with Dropbox.  However, you would then need to have Truecrypt available on any system you want to access the containers with.

If you wanted to share a Truecrypt encrypted container with other people, you'd need share the passphrase of that container with anyone you wanted to be able to open it.

Hope that was able to answer your question.

---

### Post by PalapaGuy on 2010-03-09
Thank you.  That's clear now.

I did try both TrueCrypt and encFS also.  I had a problem with encFS that I'd appreciate help with.  For good housekeeping I'll start a new thread on that topic.  Thanks again.

---

### Post by nitrogensixteen on 2010-06-21
Your files are obviously not encrypted as the Web Interface shows plaintext. The web interface does not access the data through the stream that provides decryption.

---

### Post by pzico on 2010-07-23
Isn't there such risk that if someone steals your computer, mounts some non-encrypted folder/partition to be your home. Then DropBox syncs your information visible for intruder to new non-encrypted home?

---

### Post by Grenage on 2010-07-23
Aren't dropbox configs stored in the home directory?

---

### Post by yeleek on 2010-07-23
> **Grenage said:**
> Aren't dropbox configs stored in the home directory?

Yeah I thought they were - in which case they'd be encrypted if the OP encrypted his disk.

And truecrypt is the best method of syncing data with dropbox and keeping it 'private'.

---

### Post by FuturePilot on 2010-07-24
> **pzico said:**
> Isn't there such risk that if someone steals your computer, mounts some non-encrypted folder/partition to be your home. Then DropBox syncs your information visible for intruder to new non-encrypted home?

I don't think that would be possible. I'm not exactly sure how DropBox works since I've never used it but I would have to imagine it stores some kind of username/password or some other type of authentication somewhere in your home directory which would be encrypted if you're using an encrypted home directory. (Perhaps gnome-keyring?) In which case if someone tried to do that they would still be missing the DropBox authentication.

---

