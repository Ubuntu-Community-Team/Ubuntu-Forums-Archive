---
title: "Restricting SSH and SFTP?"
date: 2008-06-20
forum: Security
---

### Post by CarbineMonoxide on 2008-06-20
Well, I'm setting up a site with a friend. I've got SSH set up to only allow myself to access my server via shell. I was wondering if I were able to add an account to my server, and only allow it access to one directory via SFTP without shell access. Anyone know how I could go about doing this?

---

### Post by HalPomeranz on 2008-06-20
You want to check out the scponly shell:

[http://sublimation.org/scponly/wiki/index.php/Main_Page](http://sublimation.org/scponly/wiki/index.php/Main_Page)

---

### Post by kevdog on 2008-06-20
I see scponly uses chrootkit.  Is this in any way different that creating a linux jail (ie using jailkit: [http://olivier.sessink.nl/jailkit/](http://olivier.sessink.nl/jailkit/)), other than the functionality is limited to "ftp-like" activities only?  Both programs make use of a chrootkit.

---

### Post by HalPomeranz on 2008-06-20
> **kevdog said:**
> I see scponly uses chrootkit.  Is this in any way different that creating a linux jail (ie using jailkit: [http://olivier.sessink.nl/jailkit/](http://olivier.sessink.nl/jailkit/)), other than the functionality is limited to "ftp-like" activities only?  Both programs make use of a chrootkit.

No particular difference.  In fact, there's a link to the jailkit info off of the link I posted above.

---

### Post by hyper_ch on 2008-06-21
I use mysecureshell... it also chroots... and has a wide array of options. Very simple to setup.

---

### Post by kevdog on 2008-06-21
How safe is the use of chroot (the actual tool all these various processes use)?  I understand the more executables you allow a chrooted user to run, you increase the chance that a user can break out of the jail.  However, is the actual risk of running a linux jail (basically that's what all these programs do), very high in terms of a security risk and the user "breaking out" of the jail, and accessing the remainder of the system.

---

### Post by HalPomeranz on 2008-06-22
> **kevdog said:**
> How safe is the use of chroot (the actual tool all these various processes use)?  I understand the more executables you allow a chrooted user to run, you increase the chance that a user can break out of the jail.  However, is the actual risk of running a linux jail (basically that's what all these programs do), very high in terms of a security risk and the user "breaking out" of the jail, and accessing the remainder of the system.

I'm not sure I entirely understand your question.  Running an application under chroot restriction can't be any less secure than running it without chroot.  Of course, the two cases may be equivalently secure if you do a bad job setting up the chroot environment!  :-)

All chroot exploits that I'm aware of first require the attacker to gain root privs within the chroot environment.  So when running an application under chroot restriction, it has to run as an unprivileged user.  Also don't put set-UID executables into your chroot directory structure.  Avoid allowing people to upload files/data into the chroot directory structure, and if you must allow this then make sure you strip the execute bits (including the set-ID bits) on all uploaded files.

You may find this link helpful as well:

[http://www.zdziarski.com/papers/chroot.html](http://www.zdziarski.com/papers/chroot.html)

It discusses the general process for chroot-ing arbitrary apps and has some good examples.

---

