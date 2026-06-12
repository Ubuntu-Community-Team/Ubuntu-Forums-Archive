---
title: "ecryptfs: keyring not cleared on logout"
date: 2010-01-17
forum: Security
---

### Post by blscreen on 2010-01-17
Hi!

On a fresh karmic install, I have a user account with ecryptfs enabled home directory. I want that directory to be secured when I log out.

This is what puzzles me:

I have two administrator accounts, user1 and user2. I log in as user1 (with ssh, will test regular logins tomorrow), /home/user1/.Private gets mounted to /home/user1, everything is fine. I log out.

I log in as user2, and /home/user1/.Private is indeed unmounted. But I can do 
```
sudo su - user1
```
which will ask me for the password of user2, and then I am logged in as user1, /home/user1/.Private is again mounted, without ever typing the password of user1.

On the other hand if I invoke
```
ecryptfs-umount-private
```
as user1 and then log out, I can no longer access the encrypted data as user2 with the sudo trick:
```
user2@crash:~$ sudo su - user1
keyctl_search: Required key not available
Perhaps try the interactive 'ecryptfs-mount-private'
```

This looks to me as if the ecryptfs passphrase used to mount the encrypted directory is not cleared from the keyring when I log out, but only when I invoke ecryptfs-umount-private.

Can anyone confirm this behavior or explain what is going on?

Best regards.
Raimar

---

### Post by yogesh.girikumar on 2010-01-22
Hi,
 This indeed happens. But not always. You could add the following line to your ~/.bash_logout file to ensure that the private directory is unmounted and hence encrypted again when you logout.
```

# to unmounting ecryptfs private folder

ecryptfs-umount-private
     
``` HTH
--
Yogesh.

---

