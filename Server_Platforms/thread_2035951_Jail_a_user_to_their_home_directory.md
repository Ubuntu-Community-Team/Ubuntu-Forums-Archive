---
title: "Jail a user to their home directory"
date: 2012-07-31
forum: Server Platforms
---

### Post by DanHorniblow on 2012-07-31
Hi, I am looking for a method to which will jail a user to their home directory when they SSH to the server.

I don't want to change system wide permissions for this use as I guess there will be system files somewhere that they would need read or write access to.

Is this possible?

Thanks Dan

---

### Post by HermanAB on 2012-08-01
$ man sshd_config

Look for the ChrootDirectory paragraph.

---

### Post by DanHorniblow on 2012-08-02
> **HermanAB said:**
> $ man sshd_config

Look for the ChrootDirectory paragraph.

Hi I have read what you suggested and I can't seem to make much sence out of it. Is the manual referring to jailing users to their home dirrectory when they start a sftp session?

As I want to to jail them to their home directory when they console in to the server via SSH.

Sorry I am a little new to things like this.

Thanks Dan

---

### Post by Lars Noodén on 2012-08-02
ChrootDirectory is easiest when used for SFTP only but it can be used for an interactive shell session, too.  You will have to populate the chroot jail with the appropriate devices and utilities.  Another gotcha is that all components of the chroot jail's pathname must be root-owned directories that are not writable by any other user or group.

Here is one description of using chroot.  It's down the page after the SFTP example.

[http://www.techrepublic.com/blog/opensource/chroot-users-with-openssh-an-easier-way-to-confine-users-to-their-home-directories/229](http://www.techrepublic.com/blog/opensource/chroot-users-with-openssh-an-easier-way-to-confine-users-to-their-home-directories/229)

---

