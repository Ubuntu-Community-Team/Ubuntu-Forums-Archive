---
title: "Possible to automount encfs?"
date: 2009-05-03
forum: Security
---

### Post by fbn on 2009-05-03
Hi,

I'm using Dropbox and encfs to have an encrypted folder in my Dropbox space.

Unfortunately I have to open a terminal and enter 'encfs ~/Dropbox/Encrypted ~/DropboxEncrypted' every time I login.

Is there a way to automount a custom encfs directory like it's done with the ~/Private directory on Ubuntu? Or even better, is it possible to automount the encfs directory if the user opens the directory?

Thanks,
  Frank

---

### Post by bodhi.zazen on 2009-05-03
Yes you can .

[http://ecryptfs.sourceforge.net/ecryptfs-pam-doc.txt](http://ecryptfs.sourceforge.net/ecryptfs-pam-doc.txt)

---

### Post by nobodysbusiness on 2009-05-12
Wow, you're doing exactly what I just finished writing a blog post about! Here's the post: [Encrypting Your Dropbox Seamlessly and Automatically]("http://pragmattica.wordpress.com/2009/05/10/encrypting-your-dropbox-seamlessly-and-automatically/").

---

### Post by masala on 2010-02-01
I used the instructions in the following post to auto-mount an EncFS folder which has a password different from the one I use to login (which made *pam-mount* and *pam-encfs* fail in my case): [Dropbox, EncFS and mounting pain]("http://obensonne.bitbucket.org/blog/20100130-encfs-keyring.html").

---

