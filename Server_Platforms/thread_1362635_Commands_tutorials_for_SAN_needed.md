---
title: "Commands tutorials for SAN needed"
date: 2009-12-23
forum: Server Platforms
---

### Post by tapas_mishra on 2009-12-23
I have a Ubuntu Laptop and have access to a SAN want to know some tutorials which can help me to understand SAN and relevant commands which are used on it.

---

### Post by craigp84 on 2009-12-23
Depends on your connection into the SAN, and in a lot of cases, the vendor of the SAN.

Look up the documentation for the SAN product.

---

### Post by tapas_mishra on 2009-12-23
san is an opensolaris variant called nexenta so its basically debian with ZFS support

---

### Post by Lars Noodén on 2009-12-23
> **tapas_mishra said:**
> san is an opensolaris variant called nexenta so its basically debian with ZFS support

Nexenta is debian using the Solaris kernel.  So the programs available are mostly the same, with the exception of some ZFS-specific utilities, and you'll be able to get them from basic system administration and shell scripting tutorials.  

The real question is about what you want to do with the Storage Area Network.  That will determine what programs to look at first.

---

### Post by tapas_mishra on 2009-12-23
I want to take backups

---

### Post by Lars Noodén on 2009-12-29
> **tapas_mishra said:**
> I want to take backups

It's rather easy then. You'll need to look at **ssh** (with key-based authentication), **sudo** and **/etc/sudoers**, and **rsync**

Here is one example:
[http://sial.org/howto/rsync/#s5](http://sial.org/howto/rsync/#s5)

Optionally, **ssh-add** can be used to work with a key agent.  

ssh is used for the encrypted connection.  
ssh keys are used to automate the log in.
sudo is used to allow a non-root, single-purpose account for the backup
sudoers allows the *exact* backup to be run with privileges
rsync does the incremental backup

You can get a lot of info looking around for those programs, but watch out for any tutorials that use remote root login.  That's a bad practice.  Same with any that use sudo to give carte blanche to the backup account.

That will get most of your data and most of your system.  It provides enough to be able to restore your system and data onto a working bare-bones, clean installation and make it like it was before.  Except if you are planning to backup live databases, then you will need additional instructions, but those are specific to the database used and how you have it set up.

---

