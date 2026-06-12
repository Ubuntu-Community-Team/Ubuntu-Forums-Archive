---
title: "ecryptfs-recover-private"
date: 2011-09-27
forum: Security
---

### Post by dragonbook on 2011-09-27
Hello

 I have encrypted my home folder during installation of Ubuntu 11.04 and are now **testing** whether I via live CD can "recover" my files in home folder.

 I open terminal and write:
```

 ubuntu@ubuntu:~$ sudo ecryptfs-recover-private
INFO: Searching for encrypted private directories (this might take a while)...
INFO: Found [/media/e7d575a1-be3d-4675-a042-505461e7392f/home/.ecryptfs/dragonbook/.Private].
Try to recover this directory? [Y/n]: y
INFO: Enter your LOGIN passphrase...
Passphrase: 
Inserted auth tok with sig [xxxxxxxxxxxxxxxxxx] into the user session keyring
INFO: Success!  Private data mounted read-only at [/tmp/ecryptfs.iV6aErKB].
``` I go into the folder / tmp/ecryptfs.iV6aErKB But I cannot access.

 I suppose it has something with "Inserted auth tok with sig [xxxxxxxxxxxxxxxxxx] Into the user session keyring" to do. (note that sig is replacing the xxxxxxxxxxxxxxxxxx).

 Someone who knows what I need to do to be able to see my files.

 ::: NOTE I can easily get to my files by booting up into Ubuntu normally. I merely try to come to my encrypted files via live CD to test whether it works (always nice to know if anything happens).

---

### Post by Paddy Landau on 2011-09-28
I have done this. Curiously, the instructions are incomplete and it took a couple of weeks for me to find the answer. This was a couple of versions ago, so I hope it still works!

First, some basic information:


[LIST]
[*]When you boot from your Live CD, your original directory will look like this:
[FONT=Fixedsys]/home/.ecryptfs/**dragonbook**/.Private[/FONT]
(I have assumed your user name is **[FONT=Fixedsys]dragonbook[/FONT]**; obviously, change to whatever it really is.)
[*]You will find your *ecryptfs signature* here:
[FONT=Fixedsys]/home/.ecryptfs/**dragonbook**/.ecryptfs/Private.sig[/FONT]
We use this as a double-check later.
[*]The contents and file names are decrypted separately.
[/LIST]

Now, boot from your Live CD.


[LIST=1]
[*]Create a folder where you can mount your decrypted files.```
 sudo mkdir /mnt/dragonbook
```
[*]Get the key decryption strings as follows.
```
sudo ecryptfs-add-passphrase --fnek
[COLOR=Navy]Passphrase:[/COLOR] [COLOR=DarkRed]*Enter your 32-character code.*[/COLOR]
[COLOR=Navy]Inserted auth tok with sig [xxxxxxxxxxxxxxxx] into the user session keyring
Inserted auth tok with sig [yyyyyyyyyyyyyyyy] into the user session keyring[/COLOR]
```Note the strings [FONT=Fixedsys][xxx...][/FONT], used to decrypt the contents, and [FONT=Fixedsys][yyy...][/FONT], used to decrypt the file names.
[*]Check that [FONT=Fixedsys][xxx...][/FONT] and [FONT=Fixedsys][yyy...][/FONT] agree with the the lines 1 and 2 respectively in your *ecryptfs signature* (from above). If not, you might have mistyped your 32-character code.
[*]Decrypt the folder as follows. If you wish to access it read-only, change [FONT=Fixedsys]-t[/FONT] (in the first line) to [FONT=Fixedsys]-rt[/FONT]. Accept the defaults (i.e. press Enter) to all prompts except where I say otherwise.
```
sudo mount -t ecryptfs /media/backup/**dragonbook**/.Private /mnt/**dragonbook**
[COLOR=Navy]Passphrase:[/COLOR] [COLOR=DarkRed]*Enter (again) the 32-character code.*[/COLOR]
    :    :    :    :    :
[COLOR=Navy]Enable filename encryption (y/n) [n]:[/COLOR][COLOR=DarkRed] y[/COLOR]
[COLOR=Navy]Filename Encryption Key (FNEK) Signature [xxxxxxxxxxxxxxxx]:[/COLOR] [COLOR=DarkRed]*Enter [yyy...] string from point 2.*[/COLOR]
    :    :    :    :    :
[COLOR=Navy]Would you like to proceed with the mount (yes/no)? :[/COLOR] [COLOR=DarkRed]yes[/COLOR]
    :    :    :    :    :
[COLOR=Navy]in order to avoid this warning the future (yes/no)? :[/COLOR] [COLOR=DarkRed]*Enter 'no' for more security, or 'yes' to note it permanently.*[/COLOR]
```
[/LIST]

Also see, if you are interested, the following two threads:
[Where I found the answer]("http://ubuntuforums.org/showthread.php?p=8473251#post8473251")
[How to access your folder from Recovery Mode]("http://ubuntuforums.org/showthread.php?t=1630994")

Let us know if it works.

---

### Post by dragonbook on 2011-09-30
Hi Paddy Landau

 Should I start in a specific directory before I run:
 sudo ecryptfs-add-passphrase - fnek

 I've tried everything you suggest but it gives me an error at the end.

---

### Post by Paddy Landau on 2011-09-30
> **dragonbook said:**
> Should I start in a specific directory before I run:
 sudo ecryptfs-add-passphrase - fnek

 I've tried everything you suggest but it gives me an error at the end.
Please tell us the error! We cannot help if we don't know what's going on. I am not aware of needing to change to a specific directory, but the error will help us determine this.

---

