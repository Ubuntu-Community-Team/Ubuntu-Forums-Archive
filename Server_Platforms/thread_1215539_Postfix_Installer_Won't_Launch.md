---
title: "Postfix Installer Won't Launch"
date: 2009-07-17
forum: Server Platforms
---

### Post by Chernevik on 2009-07-17
When I run
```
sudo aptitude install postfix
```
the installer doesn't run.  I don't have configuration files like /etc/postfix/main.cf, though I do have the directory and some files.

Why isn't the installer running?  How do I get it to run?  I've run 'update' and 'upgrade'.

I suppose I could work up a proper configuration, but the installation scripts are surely a better starting point.  All the postfix setup tutorials go through that installation process.

This is on a headless box running Ubuntu Server, v. 9.04.  I'm connecting via ssh.  Thanks in advance.

---

### Post by shizzy-t on 2009-07-17
dpkg-reconfigure postfix

---

### Post by Chernevik on 2009-07-17
I had found this after my post, and returned to note that it works.

Thanks for the reply.

---

