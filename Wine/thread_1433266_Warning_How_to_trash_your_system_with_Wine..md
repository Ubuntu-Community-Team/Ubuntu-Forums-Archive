---
title: "Warning: How to trash your system with Wine."
date: 2010-03-18
forum: Wine
---

### Post by grandsatrap on 2010-03-18
Background: I have an Ubuntu server - command-line only. This week I put Ubuntu into a partition (2 partitions: swap takes 1) on my hard drive. I loaded Wine and tried one or two things. Then I read the documentation ...

* Never run Wine as root or Sudo -- fine.
* Warning: Drive Z: links to /

This is CRAZY. I dropped down to $HOME/.wine/dosdevices and did ls -l     Yep. There is z: as a link to /  This looks dangerous, I better do something.

Aha! I thought, instead of deleting this, I'll just change the permissions on Z: to 000 . That way nothing will be able to read or write to Z:.

"chmod 000 Z:" gave me an error, so I tried "sudo chmod 000 Z:"  <-- NEVER DO THIS!!!!

What this seems to have done is go through the WHOLE FILESYSTEM and try to set all of the permissions of every file to 000. Gnome started doing crazy things. All of the characters became square boxes as error messages filled the screen. I managed to find a shutdown button somewhere.

Rescuing my files before reinstalling Ubuntu
--------------------------------------------
I think it is trashed. I have gone into the GRUB boot menu and gotten a root shell prompt. I plugged in a USB drive and it seemed to recognize it. I mounted it and can list the files on it.
Now I am doing a tar-file of everything that I have done over the past two days and saving it to my USB drive.

Is there a way to completely undo this other then reinstalling?
What does dkpg do?

---

### Post by Flareside on 2010-03-18
simply not running wine as root will prevent Z: from being written to. Also you may want to read up on symbolic links.

---

### Post by Helix7 on 2010-03-18
dpkg is a package manager

```
man dpkg
```

This link might be of some use [http://ubuntuforums.org/showthread.php?t=942717](http://ubuntuforums.org/showthread.php?t=942717)

---

### Post by grandsatrap on 2010-03-18
> **Flareside said:**
> simply not running wine as root will prevent Z: from being written to. Also you may want to read up on symbolic links.

Yes, I figured that.  Oh well, I guess somethings are learned the hard way.

---

### Post by grandsatrap on 2010-03-18
> **Helix7 said:**
> dpkg is a package manager

```
man dpkg
```

This link might be of some use [http://ubuntuforums.org/showthread.php?t=942717](http://ubuntuforums.org/showthread.php?t=942717)

Yes, in the boot menu it says that it can be used to repair packages. I tried this just now. It can't repair my system. I still get to a login prompt, but the GUI is trashed and I can't actually even cd $HOME.

---

### Post by asdfoo on 2010-03-19
I don't see what this has to do with Wine.  It's just a matter of your inexperience with linux.

You set / to not be executable, which effectively denies access to anything under /.

You could have rectified this by restoring the permission on / from a livecd then everything should have returned to normal.

---

### Post by Funnnny on 2010-03-19
What, I thought that we just can't run wine under sudo ?
Or wine has a big warning that we shouln't run it as root

---

### Post by hikaricore on 2010-03-20
-[censored]-

---

### Post by Brebs on 2010-03-21
> **grandsatrap said:**
> * Warning: Drive Z: links to /

This is CRAZY.
Nonsense. It's the standard security setup for Linux distros, where files which aren't security-sensitive are readable (but not writeable).

> What this seems to have done is go through the WHOLE FILESYSTEM
No, it only changed the permissions on "/", which is a single directory. As you found out, the permissions on it are very important, since it is the top-level directory.

> Is there a way to completely undo this other then reinstalling
chmod 755 /

If you can't login as root, then use a livecd, as asdfoo mentioned.

---

