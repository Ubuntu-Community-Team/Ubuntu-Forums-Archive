---
title: "remove home dir encryption?"
date: 2009-09-04
forum: Security
---

### Post by i.r.id10t on 2009-09-04
Buddy gave a box to my kids, I'm sharing it too. Normally do my own installs, so I'm sure his is different ...

Basically, a while back I was prompted to write down an encryption key for my home dir.  Did that, but now...

Moving a buch of data (mp3 files) from one directory (my home) to another, on the same ext3 partition.  Taking forever (2gb...) I'm assuming that it has to decrypt everything on the fly and then move the fs pointer.  On unencrypted stuff on all of my other linux boxes (lots), a move to somewhere else on the same partition is instant. 

So... how can I remove (permamently) the encrypt home directory setting/option and permamently decrypt my home dir?

Thanks!

---

### Post by staeiou on 2009-09-22
I'd like to know this too.  Thanks!

---

### Post by i.r.id10t on 2009-09-22
Never got a response, so I just reinstalled...

---

### Post by nyhm on 2009-12-07
I just created this forum user account to ask this very question:

**How to remove home dir encryption?**

I've used Debian for years, but brand new to Ubuntu (9.10). Any information greatly appreciated.

---

### Post by FuturePilot on 2009-12-07
```
ecryptfs-setup-private --undo
``` will tell you what you need to do.

---

### Post by nyhm on 2009-12-07
FuturePilot, thank you for your reply. That command is for removing the ~/.Private ecryptfs mounted directory. I would like to remove the encryption on my $HOME dir itself, which I (rashly) chose during install.

One option may be to backup the home directory contents (in non-encrypted form), delete the user (and home dir), then create a new user without the encrypted home dir.

Is that the only way?

---

### Post by FuturePilot on 2009-12-07
> **nyhm said:**
> FuturePilot, thank you for your reply. That command is for removing the ~/.Private ecryptfs mounted directory. I would like to remove the encryption on my $HOME dir itself, which I (rashly) chose during install.

One option may be to backup the home directory contents (in non-encrypted form), delete the user (and home dir), then create a new user without the encrypted home dir.

Is that the only way?

It works the same way for an encrypted $HOME. Just apply the instructions but use your $HOME directory instead of Private.

Basically, backup your data, unmount your encrypted home, make your home directory writable, and then delete /home/.ecryptfs/$USER  (if you're the only user with an encrypted home, you can probably just delete the whole /home/.ecryptfs), restore your data back to /home/$USER.

---

### Post by nyhm on 2009-12-08
Oh, nice! Thanks for the clarification. I expected there to be something to configure with the login system. Does login simply skip the ecryptfs-mount step if there is no /home/.ecryptfs/$USER dir?

---

### Post by FuturePilot on 2009-12-08
> **nyhm said:**
> Oh, nice! Thanks for the clarification. I expected there to be something to configure with the login system. Does login simply skip the ecryptfs-mount step if there is no /home/.ecryptfs/$USER dir?

Yes. You don't need to modify anything with the login system.

---

### Post by paradigm2 on 2009-12-08
Does anyone have a source of UPDATED documentation on ecryptfs only for 9.10?  I'm finding all the old information confusing and actually quite dangerous since it doesn't always apply or isn't even always necessary to do what is suggested.

I'd like to be able to read up on things, answer some of my own questions, and generally understand what is going on with the encryption more.

Apologies for adding this to the thread but it is somewhat related (people ask these questions in part due to the lack of recent accessible documentation) and I didn't want to start yet another thread.  Thanks.

---

### Post by nyhm on 2009-12-08
I second that request (but have nothing further to add).

---

### Post by cariboo on 2009-12-08
Is [this]("https://help.ubuntu.com/community/EncryptedFilesystemHowto") what you are looking for?

---

### Post by nyhm on 2009-12-08
That's a good resource, but not entirely what I was looking for (speaking for myself). That document is a very general-purpose overview of the subject, rather than specific documentation of Ubuntu 9.10's ecryptfs encrypted home dir.

BTW, here's another pitfall of using encrypted home dir: [File name length becomes limited.]("http://ubuntuforums.org/showthread.php?t=1173541") This is causing me a headache trying to migrate files to my new Ubuntu machine.

---

### Post by nyhm on 2009-12-08
> **FuturePilot said:**
> ```
ecryptfs-setup-private --undo
``` will tell you what you need to do.

Wow - that was harrowing, but I think I did it! Many thanks to FuturePilot (et al.).

Disclaimer: Don't blame me if you lose your home dir.

Here's what I did to remove my home dir encryption (suppose abc is my username, and xyz is another created in this process):

[LIST=1]
[*]While logged in as abc, close all applications and backup home dir to another location (I used tar and made sure to exclude .Private and .ecryptfs)
[*]Create another user (xyz) with "Administer the system" privileges
[*]Log out abc, log in as xyz
[*]Use sudo to remove all files (including hidden) found in /home/abc
[*]Use sudo to remove /home/.ecryptfs/abc
[*]Use sudo to restore /home/abc contents (e.g., from tar file)
[*]Optional: sudo chmod go+rX /home/abc
[/LIST]
In summary, and in conclusion, I was really impressed with Ubuntu 9.10's automatic and painless setup of an encrypted home dir. However, I encountered too many pitfalls (to be documented elsewhere) for my personal use cases.

As a followup, I will attempt to use ecryptfs-setup-private to create a similarly encrypted .Private dir within my home dir, into which I can place/symlink specific files...

---

