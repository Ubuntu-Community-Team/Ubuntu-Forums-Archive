---
title: "Recovery of ecryptfs .Private backup"
date: 2009-08-10
forum: Security
---

### Post by braddock on 2009-08-10
I'm attempting to test recovery of a ~/.Private directory which has been rsync'ed to my backup server.  I still have access to the original working ~/Private for comparison.

I am unable to mount the backup of ~/.Private using mount.ecryptfs.
I get the error: Error mounting eCryptfs: [-2] No such file or directory

Both source and target directories definitely DO exist (as per the FAQ), I've tried both relative and full paths, and I'm on about my 20th attempt.  No help from Google.  Both server and client are running up-to-date Ubuntu 9.04.

Here are my notes documenting what I am doing:
Mounting Ubuntu Private ecryptfs Directories from Backup - 8/10/09

First, do you know your passphrase?
If not, you can recover it from your login password if you have the ~/.ecryptfs/wrapped-passphrase file.  Ubuntu stashes it there to auto-mount upon login. 
[PS - what a HORRIBLE policy!!  Please stash a hash!]

printf "%s" "myloginpass" | ecryptfs-unwrap-passphrase ~/.ecryptfs/wrapped-passphrase -

You also need to know the cipher type,encrypted filename signature, etc etc.  I can find some of this information by looking at an existing Private mount point.  The sigs are stashed in ~/.ecryptfs/Private.sig
$ mount |grep Private 
/home/braddock/.Private on /home/braddock/Private type ecryptfs  ecryptfs_sig=6f5d713c6755dea8,ecryptfs_fnek_sig=8d23588101b5a624,ecryptfs_cipher=aes,ecryptfs_key_bytes=16)

Now, to actually mount the copy of .Private ON MY SERVER:

mount.ecryptfs .Private/ /mnt/mnt
Answer all questions according to parameters above.

I cannot make this work!  "I get Error mounting eCryptfs: [-2] No such file or directory"

Any help would be appreciated.  I'd hate to have to revert to unencrypted backups of ~/Private.

---

### Post by braddock on 2009-08-12
The silence is ominous.  

Could it actually be impossible to mount a .Private directory backup outside of its original machine due to bugs or bad weather?

---

### Post by narnie on 2009-09-24
Bump. I'm having the same problem.

---

### Post by The Cog on 2009-09-24
> **braddock said:**
> The silence is ominous.  

Could it actually be impossible to mount a .Private directory backup outside of its original machine due to bugs or bad weather?
That silence that you hear is the sound of gremlins laughing at you.

Only one thought, I haven't experimented with ecryptfs yet, but maybe mount needs the full path to the .Private directory rather than using your working directory, i.e. ~/.Private rather than .Private. And (yes I know you said it does exist) is it really /mnt/mnt and not just /mnt?

---

### Post by bodhi.zazen on 2009-09-24
See if these two links help you :

[http://bodhizazen.net/Tutorials/Ecryptfs/](http://bodhizazen.net/Tutorials/Ecryptfs/)

[http://blog.dustinkirkland.com/2009/03/mounting-your-encrypted-home-from.html](http://blog.dustinkirkland.com/2009/03/mounting-your-encrypted-home-from.html)

---

### Post by runexe on 2009-10-01
> **braddock said:**
> I'm attempting to test recovery of a ~/.Private directory which has been rsync'ed to my backup server.  I still have access to the original working ~/Private for comparison.

I am unable to mount the backup of ~/.Private using mount.ecryptfs.
I get the error: Error mounting eCryptfs: [-2] No such file or directory



One thing I've found (if you haven't solved this already):
~/.Private is really a link to /home/.ecryptsfs/<username>/.Private
So you want to do
```

mount -t ecryptfs /home/.ecryptfs/<username>/.Private /<mountpoint>

```
With no other options it will prompt you for the rest of the info needed (you may or may not need to run this beforehand: ```
ecryptsfs-add-passphrase --fnek
```

---

### Post by JanHolbo on 2009-10-05
> **braddock said:**
> I'm attempting to test recovery of a ~/.Private directory which has been rsync'ed to my backup server.  I still have access to the original working ~/Private for comparison.

I am unable to mount the backup of ~/.Private using mount.ecryptfs.
I get the error: Error mounting eCryptfs: [-2] No such file or directory

Both source and target directories definitely DO exist (as per the FAQ), I've tried both relative and full paths, and I'm on about my 20th attempt.  No help from Google.  Both server and client are running up-to-date Ubuntu 9.04.

Here are my notes documenting what I am doing:
Mounting Ubuntu Private ecryptfs Directories from Backup - 8/10/09

First, do you know your passphrase?
If not, you can recover it from your login password if you have the ~/.ecryptfs/wrapped-passphrase file.  Ubuntu stashes it there to auto-mount upon login. 
[PS - what a HORRIBLE policy!!  Please stash a hash!]

printf "%s" "myloginpass" | ecryptfs-unwrap-passphrase ~/.ecryptfs/wraipped-passphrase -


I have a problem related to this in the sense that I have lost my / partition and thus ~/.ecryptfs as this is a symlink to /var/lib/ecryptfs/[username]

I do know the passphrase. Is there a way to get back into my files? I have tried to mount the directory with -t ecryptfs but the files were still encrypted.

Thanks in advance

Jan

---

### Post by Antti Kaijanmäki on 2009-10-26
I had a problem recovering backup on a different machine. I had the encryption passphrase, but could figure out right away how to get the filename decryption to work so I wrote a blog post about it:

    [http://www.kaijanmaki.net/blog/2009/10/26/recovering-files-from-ecryptfs-encrypted-home/](http://www.kaijanmaki.net/blog/2009/10/26/recovering-files-from-ecryptfs-encrypted-home/)

I noticed that if the filename encryption signature was wrong I would get:

    Error mounting eCryptfs: [-2] No such file or directory

---

### Post by benekastah on 2010-05-14
> **runexe said:**
> One thing I've found (if you haven't solved this already):
~/.Private is really a link to /home/.ecryptsfs/<username>/.Private
So you want to do
```

mount -t ecryptfs /home/.ecryptfs/<username>/.Private /<mountpoint>

```


Thank you so much. This problem was driving me insane until I read this. Finally got it mounted and am backing up all the data :guitar:

Oh, and I don't think this link was posted yet. It really helped me, though: [How to recover encrypted data in Ubuntu]("https://help.ubuntu.com/community/EncryptedPrivateDirectory#Recovering Your Data Manually").

---

### Post by COKEDUDE on 2010-12-12
These links are also helpful. 

[http://goshawknest.wordpress.com/2010/04/16/how-to-recover-crypted-home-directory-in-ubuntu/](http://goshawknest.wordpress.com/2010/04/16/how-to-recover-crypted-home-directory-in-ubuntu/)
[http://blog.dustinkirkland.com/2009/03/mounting-your-encrypted-home-from.html#comment-form](http://blog.dustinkirkland.com/2009/03/mounting-your-encrypted-home-from.html#comment-form)
[http://www.kaijanmaki.net/2009/10/26/recovering-files-from-ecryptfs-encrypted-home/](http://www.kaijanmaki.net/2009/10/26/recovering-files-from-ecryptfs-encrypted-home/)
[http://bodhizazen.net/Tutorials/Ecryptfs/](http://bodhizazen.net/Tutorials/Ecryptfs/)
[http://www.theirishpenguin.com/2010/09/26/accessing-your-encrypted-home-directory-in-ubuntu/](http://www.theirishpenguin.com/2010/09/26/accessing-your-encrypted-home-directory-in-ubuntu/)

---

### Post by COKEDUDE on 2010-12-13
Wanted to also add this link.

[https://help.ubuntu.com/community/EncryptedPrivateDirectory#Recovering%20Your%20Data%20Manually](https://help.ubuntu.com/community/EncryptedPrivateDirectory#Recovering%20Your%20Data%20Manually)

---

