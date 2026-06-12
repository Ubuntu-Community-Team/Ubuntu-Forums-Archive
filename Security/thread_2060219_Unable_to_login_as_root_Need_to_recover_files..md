---
title: "Unable to login as root_Need to recover files."
date: 2012-09-19
forum: Security
---

### Post by marklinwinona on 2012-09-19
I am not very experienced in linux commands or terminal operations. I need to copy my files to an external drive. I can't remember how to login as the root and I don't know what my user name was. I have the password but I need the login format and a way to recover my root username. Or a work around that let's me move those files off to an external hard drive.

Mark L.

---

### Post by LiamOS on 2012-09-19
> **marklinwinona said:**
> I am not very experienced in linux commands or terminal operations. I need to copy my files to an external drive. I can't remember how to login as the root and I don't know what my user name was. I have the password but I need the login format and a way to recover my root username. Or a work around that let's me move those files off to an external hard drive.

Mark L.
If you want to do it with your file manager, use 'gksu nautilus'. If not, 'sudo su -' should sort you out as root in a terminal, assuming you have sudo privelages.

---

### Post by Laiquendi on 2012-09-19
Your user name should be visible somewhere in login GUI, if not, it depends if you have the root login enabled.
If yes, to login as root simply put "root" and root password.
If not, then you can enable login as root from virtual terminals (ctr+alt+1), but it involves terminal commands. Tutorial below:
 ```
<snip>
```

As a workaround i would try using bootable medium (flash,CD) and just mount and copy files.

---

### Post by coffeecat on 2012-09-19
A reminder of forum policy:

[http://ubuntuforums.org/showthread.php?t=1486138](http://ubuntuforums.org/showthread.php?t=1486138)

> Our "line in the sand" is with tutorials or posts that show people how to LOG IN to a graphical desktop (gnome, KDE, etc) as root. This is completely inappropriate and unnecessary.

@everyone, please do not post links to tutorials telling people how to log into a GUI as root.

@marklinwinona, you do not need to log in as root in order to copy files to an external drive. If you need information on temporary elevation to root privileges and the use of sudo, see here:

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by CharlesA on 2012-09-19
What coffeecat and Liam said.

Also: Booting off a livecd and copying from there should work too.

---

