---
title: "Can't Install Virtual Box Extension Pack"
date: 2022-12-31
forum: Virtualisation
---

### Post by daniell59 on 2022-12-31
I just installed Virtual Box 6.1 through the terminal.
I then tried to install Virtual Box Extension Pack in the terminal.
Unable to locate package virtualbox—ext–pack
What am I doing wrong?
Thanks

---

### Post by tea for one on 2022-12-31
Did you use the correct package name?
```
edited@edited-22-04:~$ apt policy [COLOR="#0000FF"]virtualbox-ext-pack[/COLOR]
virtualbox-ext-pack:
  Installed: (none)
  Candidate: 6.1.32-1
  Version table:
     6.1.32-1 500
        500 http://gb.archive.ubuntu.com/ubuntu jammy/multiverse amd64 Packages
        500 http://gb.archive.ubuntu.com/ubuntu jammy/multiverse i386 Packages
edited@edited-22-04:~$
```

Edit: The package name uses hyphens rather than dash or en dash or em dash

---

### Post by daniell59 on 2022-12-31
I was able to install Virtual Box Extension Pack with these commands.

$ sudo apt update
$ sudo apt install virtualbox-ext-pack

---

### Post by MAFoElffen on 2023-01-01
You know that the extension pack gets installed to the linux guest, not the host right?

---

### Post by daniell59 on 2023-01-02
> **MAFoElffen said:**
> You know that the extension pack gets installed to the linux guest, not the host right?

Thanks,
I did not know that. I installed it to the host. What should I now do?

---

### Post by tea for one on 2023-01-02
I think that there may be a misunderstanding with the package descriptions.
Virtualbox Extension Pack vs Virtualbox Guest Additions 
> 
    Oracle VM VirtualBox Base Package: the executable that you have to install on your host operating system
    Oracle VM VirtualBox Extension Pack: a binary package that extends the functionality of the VirtualBox base package
    Oracle VM VirtualBox Guest Additions: consist of device drivers and system applications that optimize the guest operating system for better performance and usability

Taken from here [https://blogs.oracle.com/virtualization/post/friday-spotlight-virtualbox-extension-pack-guest-additions](https://blogs.oracle.com/virtualization/post/friday-spotlight-virtualbox-extension-pack-guest-additions)

---

