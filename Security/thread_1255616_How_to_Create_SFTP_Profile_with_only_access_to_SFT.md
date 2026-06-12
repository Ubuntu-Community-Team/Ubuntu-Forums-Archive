---
title: "How to Create SFTP Profile with only access to SFTP and Media Dir."
date: 2009-09-01
forum: Security
---

### Post by mrmaster on 2009-09-01
Hello,

I have set up an openssh server on my box and I have an external NAS attached to it. When my friend logs into my box I would like her to only see the directory of the box (/media/NAS) and only be able to have SFTP access.  

I don't want her to mess around with my bin, etc, sys... and so on directories found under root. I also do not want her to have any shell access. 

Thanks

---

### Post by Bachstelze on 2009-09-01
> **mrmaster said:**
> Hello,

I have set up an openssh server on my box and I have an external NAS attached to it. When my friend logs into my box I would like her to only see the directory of the box (/media/NAS) and only be able to have SFTP access.  

I don't want her to mess around with my bin, etc, sys... and so on directories found under root. I also do not want her to have any shell access. 

Thanks

Why not use FTP (with SSL if you want encryption)? Chrooting in SSH can be a bit tricky.

---

### Post by DaithiF on 2009-09-01
if you *do* want to go the sftp chroot way, there is a debian guide here:
[http://www.debian-administration.org/articles/590](http://www.debian-administration.org/articles/590)

---

### Post by mrmaster on 2009-09-01
> **HymnToLife said:**
> Why not use FTP (with SSL if you want encryption)? Chrooting in SSH can be a bit tricky.

Can you describe what you mean by use SSL with FTP? From what I'm assuming is that the openSSH running on my server automatically encrypts my traffic when I connect to it via putty. 

If I do establish an SSL connection then use FTP how would i restrict the user trying to get into my box to see only my NAS directory?

---

### Post by Bachstelze on 2009-09-01
> **mrmaster said:**
> Can you describe what you mean by use SSL with FTP? From what I'm assuming is that the openSSH running on my server automatically encrypts my traffic when I connect to it via putty. 

If I do establish an SSL connection then use FTP how would i restrict the user trying to get into my box to see only my NAS directory?

I think you're confusing SSL and SSH. The one you're using when you're connecting through putty is SSH, and it can also be used to transfer files (SFTP). However, as I said, configuring it to restrict the user into a directory can be tricky, so if I were you, I would just setup a FTP server, which can let you restrict users in their home directories more easily, and use SSL to encrypt the trafic should you need encryption.

---

