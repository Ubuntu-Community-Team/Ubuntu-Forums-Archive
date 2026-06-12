---
title: "Truecrypt on Ubuntu server 9.04"
date: 2009-05-07
forum: Server Platforms
---

### Post by smeerbartje on 2009-05-07
Hi all, I'm trying to install Truecrypt on my Ubuntu 9.04 server. But I'm getting an error while installing. First I have downloaded the .tar.gz file from truecrypt.org. After untarring I start the executable file and the installer is asking me what to do:

1) Install truecrypt_6.1a-0_i386.deb
2) Extract package file truecrypt_6.1a-0_i386.deb and place it to /tmp

I choose to install truecrypt. After confirming and accepting the license terms, I'm getting this error:

```

¨(Reading database ... 26302 files and directories currently installed.)
Preparing to replace truecrypt 6.1a-0 (using /tmp/truecrypt_6.1a-0_i386.deb) ...
Unpacking replacement truecrypt ...
dpkg: dependency problems prevent configuration of truecrypt:
 truecrypt depends on libsm6; however:
  Package libsm6 is not installed.
 truecrypt depends on libgtk2.0-0; however:
  Package libgtk2.0-0 is not installed.
dpkg: error processing truecrypt (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 truecrypt
Error: TrueCrypt installation failed

```

What does this mean? I don't want to install libgtk2.0-0, because it is a GUI thing, right? I just want the command-line truecrypy tool. Anyone some suggestions how to install tryecrypt?

---

### Post by doogy2004 on 2009-05-07
The following will install the unmet dependencies and finish the installation:
```
sudo apt-get install -f
```

---

### Post by smeerbartje on 2009-05-08
> **doogy2004 said:**
> The following will install the unmet dependencies and finish the installation:
```
sudo apt-get install -f
```

Thanks, but how can I see the dependencies for GTK? I don't want to install some kind of GUI on my server...

---

