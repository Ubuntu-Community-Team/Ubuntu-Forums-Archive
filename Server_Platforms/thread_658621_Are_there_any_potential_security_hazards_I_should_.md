---
title: "Are there any potential security hazards I should know when using linux jailkit?"
date: 2008-01-04
forum: Server Platforms
---

### Post by kevdog on 2008-01-04
The whole concept of creating a linux jail for individual users sounds appealing, particularly if you are going to allow other users to ssh into your box to store files (winscp or scp).  

I created the linux jail with the following package:
[http://olivier.sessink.nl/jailkit/](http://olivier.sessink.nl/jailkit/)

It was actually easy although I had to read and keep rereading the examples until I understood what the documentation was saying.

Are there any potential security risks with using this method?

---

### Post by HermanAB on 2008-01-05
Yes, the main security risk is that chroot doesn't provide much extra security.  It will prevent honest users from reading other user's stuff by accident, but it won't do much to malicious users.  If you have a problem with basically honest users, then go ahead...

I don't use chroot.  It doesn't provide any extra security for my users (military), while it does provide an enormous maintenance problem, which I don't need.

Cheers,

Herman

---

### Post by kevdog on 2008-01-05
Do you recommend another solution??  Is there anyway to get a ftp-like server using ssh?  I know about sftp, but that doesnt seem like an ideal solution.  I want two way encryption.

---

### Post by HermanAB on 2008-01-05
No, using chroot with ssh is the only way I know of.  It will fool most users, but *you* should not trust it to provide extra security.  Your only real security comes from maintaining the user access rights properly, so that users cannot write to sensitive areas.

My own feeling about it is not to bother with chroot.  So users can read system files.  So what?  They can go and download Ubuntu for free anyway.  However, your management of access rights should prevent them from reading each other's files in the /home directory.

Cheers,

Herman

---

### Post by kevdog on 2008-01-05
Thanks for the input.  Its always good to learn some things in areas I don't know a lot about.

---

