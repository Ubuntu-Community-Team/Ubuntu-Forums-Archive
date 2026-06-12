---
title: "Using the encryption that Ubuntu creates during an installation"
date: 2017-07-26
forum: Security
---

### Post by Mark_in_Hollywood on 2017-07-26
At install of 16.04.2 I selected the "stock" or "standard" encryption. I have my log in screen password as well as the 32 bit ecryptfs passphrase.

Do I use this:

ecryptfs-unwrap-passphrase

or 

sudo ecryptfs-unwrap-passphrase

and does it matter?

If a wrong passphrase is entered too many times in a row, does the system lock out the user for minutes? Hours? Forever?


Terminal returned:

```
mark@Lexington:/media/mark/9deada4e-82ad-45fa-a1c6-a8e68d8b41f5/.ecryptfs/mark/.Private$ sudo ecryptfs-add-passphrase --fnek
[sudo] password for mark: 
Passphrase: 
Inserted auth tok with sig [de0357543abe6969] into the user session keyring
Inserted auth tok with sig [8a0b80df2b4e58a7] into the user session keyring
```

but the files do not appear to be unlocked or unencrypted.

---

### Post by deadflowr on 2017-07-26
Without sudo is fine.
It's not unlocking/unwrapping anything related to root.

Not sure if there is a set attempt failure timeout for it or not.

---

### Post by Mark_in_Hollywood on 2017-07-26
I'm getting more confused.

```
mark@Lexington:/media/mark$ cd /media/mark/6999871c-cc18-4cae-a3c9-5f743e13a015
bash: cd: /media/mark/6999871c-cc18-4cae-a3c9-5f743e13a015: [B]Permission denied
[/B]
mark@Lexington:/media/mark$ sudo cd /media/mark/6999871c-cc18-4cae-a3c9-5f743e13a015
[sudo] password for mark: 
sudo: cd: command not found

```

I have a backed up /home on an external sata. I'm trying to unlock it.

I did this because I [saw]("https://askubuntu.com/questions/875671/ecryptfs-recover-private-cannot-find-encrypted-home-folder"):

```
INFO: Searching for encrypted private directories (this might take a while)...
find: ‘/run/user/999/gvfs’: Permission denied 
find: File system loop detected; ‘/sys/kernel/debug/pinctrl’ is part of the same file system loop as ‘/sys/kernel/debug’.
```

That terminal outpost, above, is due to running:

```
sudo ecryptfs-recover-private
``` in a Live.iso

which I ran after 

sudo apt-get install -y ecryptfs-utils

and the terminal output of that was it was the most current, etc.

---

