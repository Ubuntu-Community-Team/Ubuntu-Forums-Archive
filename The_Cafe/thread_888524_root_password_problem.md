---
title: "root password problem"
date: 2008-08-13
forum: The Cafe
---

### Post by BarryBKS on 2008-08-13
[FONT="Verdana"]Hi all,

Sorry if this has already been covered, but I couldn't locate a thread on it anywhere.

I have just installed Ubuntu on to my Apple MacBook Pro through Parallels. It has installed without any problems, but it has not asked me to set up a root password and I need to log in as root to install some software.

I tryed to log in as root and leave the password field blank, but that didn't work. :(

Any ideas would be most welcomed.

Thanks,

Barry.[/FONT]

---

### Post by JillSwift on 2008-08-13
By default, root is password-less and can't be logged into. This is for security, and the vast, vast majority of Ubuntu users will never have to log in as root.

The account you made when installing Ubuntu is an administrator's account, and can run things as root using "sudo" (super-user do), or in a GUI via "gksu" (still from a command line).

example; to install something from the repositories:
```
sudo apt-get install [COLOR=DarkRed]*<package name>*[/COLOR]
```It will ask for a password, you type in your administrator account's password (it will not give feedback), and it then runs the command as root.

---

### Post by lisati on 2008-08-13
With Ubuntu, it's more common to use "sudo" for any commands that require root privileges than it is to log in to the "root" account.

---

### Post by az on 2008-08-13
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by taseedorf on 2008-08-13
Well, sometimes when I have installed it has not asked me either.  Go into the user and group settings and manually set the root password.  Make sure you also enable root login.  This is done in the login window manager in the administration tab in gnome.

---

### Post by pparks1 on 2008-08-13
> **taseedorf said:**
> Well, sometimes when I have installed it has not asked me either. Ubuntu never prompts you to setup the root account and password.  By default, Ubuntu relies entirely on the sudo system and doesn't use the root account.


> **taseedorf said:**
> Go into the user and group settings and manually set the root password.  Make sure you also enable root login.  This is done in the login window manager in the administration tab in gnome.
There really isn't a good reason to have to do this.  It does nothing more than circumvent the sudo system that is in place on the box.  Prefacing your commands with sudo will take care of everything that you need root access for.  Plus, it caches the password for 5 minutes...so if you have a string of commands that you are using, it won't prompt you each and everytime for the password. Most things within the GUI will prompt when root access is needed.

---

