---
title: "[SOLVED] Is this command safe???"
date: 2008-12-02
forum: Security
---

### Post by Jammanuser on 2008-12-02
Hello, i just got advice from someone on another forum, to run certain commands on my computer, using a LiveCD (i actually have ubuntu 8.10 INSTALLED on my computer, but i cant get into it right now, because of a crc error). however, since i happened to read that warning announcement about malicious commands, i wanted to check here first to make sure that it is legit! ):P

Here is the commands:

```
gksu nautilus
cp
```

according to the guy that wrote it, the first one allows u to run the file browser as root, and the second one is a terminal command to copy files!

Is this true or not?

Looking forward to any and all replies...

:guitar:

---

### Post by pennacook on 2008-12-02
> according to the guy that wrote it, the first one allows u to run the file browser as root, and the second one is a terminal command to copy files!

Is this true or not?

true for second. first should be gksu nautilus

---

### Post by Sub101 on 2008-12-02
Yeh. As above should be nautilus not nautikus. Otherwise all fine.

---

### Post by Jammanuser on 2008-12-02
> **pennacook said:**
> true for second. first should be gksu nautilus

oh...right!!! that was simply a typo...i meant "nautilus"!

i'll fix it immediately...

Cheers! :guitar:

---

### Post by Jammanuser on 2008-12-02
> **Sub101 said:**
> Yeh. As above should be nautilus not nautikus. Otherwise all fine.

ok...cool! just checking!!! 

Thanks! :guitar:

---

### Post by gTinker on 2008-12-03
Jammanuser, if you happen to be in the same situation in the future I want to mention that you can read the manual page for a command by typing man *(command name)* in a terminal. For example: man cp would open the manual page for the copy command. In this way you can read for yourself what a command will do before you use it.

---

### Post by Jammanuser on 2008-12-08
> **gTinker said:**
> Jammanuser, if you happen to be in the same situation in the future I want to mention that you can read the manual page for a command by typing man *(command name)* in a terminal. For example: man cp would open the manual page for the copy command. In this way you can read for yourself what a command will do before you use it.

ahh...ok! Thanks! :D

Cheers! :p

-jammanuser

:guitar:

---

### Post by Kinetic Being on 2008-12-08
And incase you can't read the manpages,

the command "cp" won't do anything by itself, you need to tell it what to copy and to where...

example:

```
cp /home/user/file.filetype /home/user/folder/file.filetype
```

Whould copy the file that is in /home/user/ (your home directory, and user is your username) and named file.filetype to inside of a folder named "folder" and it would have the same name as the source file.

---

### Post by go_beep_yourself on 2008-12-12
You could of found the answer to your questions by using the man command and reading the Descriptions.

For example:

man nautilus

DESCRIPTION
       This  manual  page  documents briefly the nautilus command. This manual
       page was written for the  Debian  GNU/Linux  distribution  because  the
       original program does not have a manual page.

       Nautilus is the file manager for the GNOME desktop.

man cp

NAME
       cp - copy files and directories

DESCRIPTION
       Copy SOURCE to DEST, or multiple SOURCE(s) to DIRECTORY.

---

