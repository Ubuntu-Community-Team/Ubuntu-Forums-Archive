---
title: "Ubuntu One and ecryptfs"
date: 2009-11-19
forum: Ubuntu One (CLOSED)
---

### Post by vlc on 2009-11-19
Hi *,

I would like to backup some files in Ubuntu One, but only encrypted using ecryptfs. My idea is to backup the directory *~/.Private* in *~/Ubuntu One*.

I already tried to link (ln -s) or bind (mount --bind) *~/.Private* in *~/Ubuntu One* or even replace one directory with the other using *ln -s* or *mount --bind*, but the files are not synchronized correctly. In Nautilus, all is marked as synchronized, but the files do not appear in Ubuntu One's web page - other files or directories, which I manually copied into *~/Ubuntu One*, do.

Has anybody already used Ubuntu One with ecryptfs? Any hints are welcome.

Thanks a lot in advance!

---

### Post by manoriax on 2009-11-19
I actually have no idea how encryptfs works, but I guess it encrypts the filesystem in the folder to make it unreadable for external devices or systems? If that's so I guess (I repeat: I have no idea how encryptfs exactly works) Ubuntu One is just not able to read the files correctly and therefore they don't appear on the web page. But maybe there is someone else who has got more knowledge ;)

---

### Post by joshuahoover on 2009-11-24
> **vlc said:**
> Hi *,

I would like to backup some files in Ubuntu One, but only encrypted using ecryptfs. My idea is to backup the directory *~/.Private* in *~/Ubuntu One*.

I already tried to link (ln -s) or bind (mount --bind) *~/.Private* in *~/Ubuntu One* or even replace one directory with the other using *ln -s* or *mount --bind*, but the files are not synchronized correctly. In Nautilus, all is marked as synchronized, but the files do not appear in Ubuntu One's web page - other files or directories, which I manually copied into *~/Ubuntu One*, do.

Has anybody already used Ubuntu One with ecryptfs? Any hints are welcome.

Thanks a lot in advance!

We currently don't support syncing symlinks. The best way to do what you want is to store your encrypted files in ~/Ubuntu One/ and then creating the symlink ~/.Private rather than the other way around. We realize this is less than ideal and plan on providing the ability to define which folders (outside of ~/Ubuntu One) you want to synchronize.

Thank you,

Joshua

---

### Post by vlc on 2009-11-25
> **joshuahoover said:**
> We currently don't support syncing symlinks. The best way to do what you want is to store your encrypted files in ~/Ubuntu One/ and then creating the symlink ~/.Private rather than the other way around. We realize this is less than ideal and plan on providing the ability to define which folders (outside of ~/Ubuntu One) you want to synchronize.


Hi Joshua,

thanks for your reply. I think I already tried this and I had a Problem as *~/Private* is mounted to *~/.Private* and this didn't work correctly when *~/.Private* is a symbolic link. I'm not in front of my Ubuntu box right now so I can't test it, but I will try as soon as I'm back.

Thanks a lot!

---

