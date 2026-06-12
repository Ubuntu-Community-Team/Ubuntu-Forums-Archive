---
title: "[SOLVED] strange file in my home dir"
date: 2008-10-29
forum: Security
---

### Post by SteveNorman on 2008-10-29
I am cleaning house today and noticed a file ```
.#firsh
```I cant open it and it is said to be broken and is listed as a link in nautilus. Is anyone familiar with this file? Its in magenta with ls -a. I dont want to delete something important,,and I dont want to screw around with a key logger or anything like that.

---

### Post by cdenley on 2008-10-29
sounds like a link to a non-existant file
```

ls -l .#firsh

```

---

### Post by Rocket2DMn on 2008-10-29
Anything in the file?  If nothing is in it, it is probably safe to delete.  If it's garbage in the file, still probably safe to delete.  Hidden files are usually config files or backups - non-essential to the system.  If you think it may be a corrupted file and you want to play it safe, you can fsck your root filesystem (and /home if it's on a separate partition).

---

### Post by Gamma746 on 2008-10-29
Run ```
file .#firsh
``` to find what type of file that is.

**Edit:**

To Elaborate on what Rocket2DMn said, the easiest way to fsck your root filesystem would be to run ```
sudo touch /forcefsck
``` and reboot.

---

### Post by SteveNorman on 2008-10-30
```
$ ls -l .#firsh
lrwxrwxrwx 1 steve steve 40 2008-10-20 13:02 .#firsh -> steve@teampeanut-desktop.7603:1211401281
steve@teampeanut-desktop:~$ cat .#firsh
cat: .#firsh: No such file or directory
```

```
~$ file .#firsh
.#firsh: broken symbolic link to `steve@teampeanut-desktop.7603:1211401281'
```


what I got so far,,I did just move my home to a separate partition,, may be the cause. What I am most worried about is some kind of link from a hacker to my desktop. But then again I am the paranoid type.

---

### Post by manpaz on 2008-10-30
Usually your home directory is defined in /etc/passwd, so I suppose in the event you moved your folder, this file could be the result of process running when you moved it.

The numbers at the end suggest a format like file.PID:TIME or just a temporary file.

   Thanks

---

### Post by scragar on 2008-10-30
It's a broken link, if nothing's complained about it so far nothing will.

Just delete the thing.```

rm ".#firsh"

```

---

### Post by SteveNorman on 2008-10-30
thanks everyone,,I will just delete it.

---

