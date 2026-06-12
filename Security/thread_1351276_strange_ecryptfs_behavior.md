---
title: "strange ecryptfs behavior"
date: 2009-12-10
forum: Security
---

### Post by hallu on 2009-12-10
ecryptfs mounts the private folder without asking for any passwords after using sudo, is this intended?

for example, i use sudo apt-get update, then i close the terminal and try to mount the private folder by clicking "access your private data" and the folder gets magically mounted without promoting for any passwords

this is highly unwanted behavior, if it's not a bug, i will consider switching to dm-crypt/luks

---

### Post by bodhi.zazen on 2009-12-10
I assume you are asking about an encrypted home directory ?

In that case, yes, your home directory is decrypted when you log in via a GUI (GDM).

In 9.04 if you ssh in , your home directory is not decrypted, have not tried ssh in 9.10 yet.

You may want to look at something like Cryptkeeper:

[http://www.kallasoft.com/cryptkeeper-for-encrypting-user-files/](http://www.kallasoft.com/cryptkeeper-for-encrypting-user-files/)

---

### Post by hallu on 2009-12-11
> **bodhi.zazen said:**
> I assume you are asking about an encrypted home directory ?

No, i mean the Private directory that you can configure by launching ecryptfs-setup-private.

I log in automatically. In my Private directory is a readme file that states

> THIS DIRECTORY HAS BEEN UNMOUNTED TO PROTECT YOUR DATA.

From the graphical desktop, click on:
 "Access Your Private Data"

or

From the command line, run:
 ecryptfs-mount-private

I click on "Acces Your Private Data". I type my password and the private directory is mounted. 

Everything is fine up to this point. The problem is that I do not have to type my password directly to mount my private directory. It is enough to open and close synaptic, then click on "Acces Your Private Data" and the private directory will be mounted automatically without asking for any passwords.

---

### Post by undecim on 2009-12-11
When ecryptfs is set up, it uses your passphrase to "wrap" your encryption key. If you've typed your passphrase into something such as sudo since logging in, it will already have your passphrase to unwrap your key.

Don't worry. Your data is still encrypted (i.e. someone who steals your laptop will still need your password to access those files)

EDIT: If you want to remove this behavior, you can remove the pam_ecryptfs.so entries from your /etc/pam.d/common-* files.

---

