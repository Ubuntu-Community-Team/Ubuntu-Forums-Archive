---
title: "How to invoke sudo and keeping user's environment variables"
date: 2008-12-01
forum: Security
---

### Post by istoyanov on 2008-12-01
This might go as well into the general help forum, but since my question is about using "sudo", I decided to post it here.

I have installed some local software (actually TeXLive2008, by using sudo ./install-tl[1]) and added the installed binaries to the path (using ~/.profile). Sofar everything runs OK, but when I try to upgrade the TeX distribution through the tlmgr script[2] by prepending sudo to the command, it seems that the shell doesn't get the existing $PATH and the command isn't found. However, when I run tlmgr as a regular user it complains about missing rights.

My question is: how should I run the (local) binaries through sudo, but keeping the environment of the user? What would be the *recommended* way doing this?

[1] [http://www.tug.org/texlive/quickinstall.html](http://www.tug.org/texlive/quickinstall.html)
[2] [http://www.tug.org/texlive/tlmgr.html](http://www.tug.org/texlive/tlmgr.html)

NOTE: I have *no* root account active as per Ubuntu's defaults

---

### Post by Sarmacid on 2008-12-01
Check out```
man sudo
```
> -E        The -E (preserve environment) option will override the env_reset option in sudoers(5))

---

### Post by istoyanov on 2008-12-02
Thank you, Sarmacid, but the proposed sudo option didn't help:

```
me@ubuntubox:~$ sudo -E tlmgr
sudo: tlmgr: command not found
```

---

### Post by s3gfault on 2008-12-02
how about just ```
sudo ./tlmgr
```

---

### Post by istoyanov on 2008-12-02
I suppose that this would run OK (after cd to the container directory), but once things start to get installed I'd need a unchanged environment anyway... 

Thanks for the suggestion, though!

---

### Post by Sarmacid on 2008-12-02
You can add that folder to the path in a temporary root shell

```
sudo -i
PATH=$PATH:/path/to/files
```

But taking a look at one of the links, you shouldn't have root issues, and should install it as a regular user

> You do not need to be root (administrator on Windows) to install, run, or manage TeX Live. We strongly recommend installing it as a normal user. 

---

### Post by istoyanov on 2008-12-02
The default option was to install everything to /usr/local/texlive/2008/$SUBDIRS, so I *had* to install via sudo. This way I hit the troubles, but I'll try to reach an Ubuntu-friendly way upgrading the TeXLive distribution.

Thanks for now! Once I have tested, I'll report back.

---

### Post by s3gfault on 2008-12-03
In that case, I may suggest something like this, where localuser is replaced by your username:
```

sudo chown -hR localuser /usr/local/texlive/2008

```

---

### Post by istoyanov on 2008-12-03
After some experimenting, I decided to chown the whole directory to an ordinary user (following s3gfault's suggestion) and not to mess with sudo at all. Everything works OK for now :D

Thank you all for the suggestions!

---

