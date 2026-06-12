---
title: "Moving an EncryptFS ecrypted /home to a new system"
date: 2009-09-13
forum: Security
---

### Post by cheoppy on 2009-09-13
I have an encrypted home directory made with the ecrypts-utils and I'm using automount upon login on a 32bit Ubuntu Jaunty. 
Recently I bought a new laptop which support 64bit instructions and I want to install a new Ubuntu amd64 but use my old /home without needing to reencrypt everything (moving the data between the laptops is needed of course, but I can manage that). How can I set up the new system to both access my old /home and to automagically mount it upon login? (I think I might need to rewrap my passphrase if I change my login passphrase, but I have no idea how to set it to automount)
Actually I used [_this post_]("http://blog.dustinkirkland.com/2009/02/jaunty-encrypted-home-directories.html") from Dustin Kirkland to set up encrypted home. I looked for a how-to on moving the encrypted directory, but found nothing.

Thanks for the help!

---

### Post by bodhi.zazen on 2009-09-13
By far the easiest way will be to install Ubuntu and again encrypt /home. The move the data.

If you wish to move your encrypted home you will need to loo at how ecryptfs works .

[http://bodhizazen.net/Tutorials/Ecryptfs/](http://bodhizazen.net/Tutorials/Ecryptfs/)

---

### Post by cheoppy on 2009-09-15
In the end I did some research on how this encryption works, and did the following:
[LIST]
[*]Swapped hard disks between the two laptops
[*]Installed new system
[*]Created a user with the **same** username and password
[*]On completion I booted to recovery mode, set the old /home partition in fstab and moved the /var/lib/ecryptfs/<username> directory from the old system to the new (so to have the same old keys) (backup is advised of course)
[*]Booted the new system and everything worked like before
[/LIST]

---

