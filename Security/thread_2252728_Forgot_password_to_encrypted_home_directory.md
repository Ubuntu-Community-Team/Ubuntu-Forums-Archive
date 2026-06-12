---
title: "Forgot password to encrypted home directory"
date: 2014-11-14
forum: Security
---

### Post by jonnyboysmithy on 2014-11-14
Hi all,

I have a computer that I've put away for some time. Recently I've come to need the data on the machine. The homefolder was encrypted using encryptfs. Now as it turns out, I have forgotten the password!! :frown: 
I had the password written down and put in the usual place, but allas, its not their anymore.. :shock::cry::-k


I think I may have some shreds of words of what the password may have contained, john the ripper comes to mind as a last resort.

Can someone help me get john the ripper setup to try brute force this thing?

I can figure out how to use john the ripper with the man pages, its getting it to pipe the password attempts into ecryptfs that is the bit that I'm stuck on or however it is that they can be linked to work.



EDIT: I've found the wrapped passphrase. I've also found this so its a start: [http://www.spinics.net/lists/ecryptfs/msg00477.html](http://www.spinics.net/lists/ecryptfs/msg00477.html)

---

### Post by TheFu on 2014-11-14
[http://www.howtogeek.com/116297/how-to-recover-an-encrypted-home-directory-on-ubuntu/](http://www.howtogeek.com/116297/how-to-recover-an-encrypted-home-directory-on-ubuntu/)
[http://askubuntu.com/questions/38336/how-do-i-recover-my-data-from-an-encrypted-home-directory](http://askubuntu.com/questions/38336/how-do-i-recover-my-data-from-an-encrypted-home-directory)
[https://help.ubuntu.com/community/EncryptedPrivateDirectory](https://help.ubuntu.com/community/EncryptedPrivateDirectory)

There are sections for recovering data - of course, when using encryption, having great backups is absolutely critical - absolutely.
I wish you luck.

---

### Post by jonnyboysmithy on 2014-11-15
I'm stuck on trying to find a way to get john to feed ecryptfs-unwrap-passphrase with attempts. Something like ```
john | ecryptfs-unwrap-passphrase ./wrapped-passphrase
```

How can I do this?

---

### Post by jonnyboysmithy on 2014-11-15
Turns out there's a python script for this called ecryptfs2john.py in the community release of john the ripper that can handle this. Solved.

---

