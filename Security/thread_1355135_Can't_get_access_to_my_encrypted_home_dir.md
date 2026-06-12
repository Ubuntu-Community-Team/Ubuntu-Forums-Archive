---
title: "Can't get access to my encrypted /home dir"
date: 2009-12-14
forum: Security
---

### Post by Dr Emixam on 2009-12-14
Hi

I have a problem which seems quite hard to solve, I've asked on the French forums and nobody helped me yet.

When I bought my computer a few month ago, the first beta of Karmic had just been released, and, as I experienced some problems with Jaunty on this hardware, I installed the beta version on it.

During the installation, I noticed a new (I guess it's new, I never noticed it before) option that allow to encrypt the /home directory. I do like new features, so I checked the box, just to try…

Everything was working well, but a few day after the Karmic final release, during the starting of the system, I had this error message:
> One or more of the mounts listed in /etc/fstab could not be mounted yet

When it happened, I only installed Ubuntu again with the same settings (same partitions, same login/pass etc…) and everything worked well…

But yesterday, when it happened again, the new install didn't work, instead, I got the following message:
> L'installation nécessite la suppression de fichiers système, mais cette opération est impossible. L'installation ne peut pas continuer.
I know, it's french, that means something like
> The installation needs to delete some system files, but this can't be completed. The installation can't continue.

After that, I began my searches on the web to find how to decrypt these files, I tried many solutions and discovered some things about /home dir encryption (tell me if I mistake about something) :
[LIST]
[*]When /home/login dir is encrypted, it is an empty dir and /home/.encryptfs/login/.Private is mounted on it
[*]The key which decrypts the data is stored with it in /home/.encryptfs/login
[*]The passphrase is required to get the key
[/LIST]

I've got my /home/.encryptfs dir and all its content, and the last thing I tried to do is what described is here: [http://ubuntuforums.org/showthread.php?t=1166013&page=2](http://ubuntuforums.org/showthread.php?t=1166013&page=2)
and here
[http://www.kaijanmaki.net/blog/2009/10/26/recovering-files-from-ecryptfs-encrypted-home/](http://www.kaijanmaki.net/blog/2009/10/26/recovering-files-from-ecryptfs-encrypted-home/)

Unfortunately, when I did this, I got a full directory of encrypted files with encrypted names, something like:
> …
ECRYPTFS_FNEK_ENCRYPTED.FWa92NnfGVr4XEQm8S73s9gXy0ngjfVHozU.ys9iYmZu4MtUS31sQoXvnU--
ECRYPTFS_FNEK_ENCRYPTED.FWa92NnfGVr4XEQm8S73s9gXy0ngjfVHozU.YWlEwhgVgZ0x.-KX65DwV---
ECRYPTFS_FNEK_ENCRYPTED.FWa92NnfGVr4XEQm8S73s9gXy0ngjfVHozU.ZluC7ZKI.uUBisawBYI6Jk--
ECRYPTFS_FNEK_ENCRYPTED.FWa92NnfGVr4XEQm8S73s9gXy0ngjfVHozU.ZnmxOvopnHWKUoY4RFWETU--
…
(I only pasted a few lines because I got hundreds like these four ones)

So,
Is my data lost forever ?
How could I get access to it ?
What did I do wrong ?

Tell me if you need more information to help me.

I apologize for the long post and the language mistakes, thank you for your answers.

---

### Post by Dr Emixam on 2009-12-15
Nobody ? :(

---

### Post by Dr Emixam on 2009-12-15
Ok, I finally got my files back.

So, here is what I did:

First, I renamed my /home/.ecryptfs to avoid any deleting
> sudo mv /home/.ecryptfs /home/encrypted_filesThen, I installed Ubuntu with the same parameters (username/partitions etc...) except I did not choose to encrypt my home dir

Once done, I restarted on the new system, loged to my account and :

Copied /home/encrypted_files/login/.ecryptfs to ~/.ecryptfs
> sudo cp /home/encrypted_files/login/.ecryptfs ~/.ecryptfsand I created a symbolic link to the encrypted file folder

> sudo ln -s /home/encrypted_files/login/.Private ~/.Privatemade a dir to mount the Private one

> mkdir Privateand typed 

> [mount.ecryptfs_private]("http://manpages.ubuntu.com/manpages/karmic/man1/mount.ecryptfs_private.1.html")After that, my data was available in ~/Private

---

