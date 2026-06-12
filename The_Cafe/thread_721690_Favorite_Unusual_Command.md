---
title: "Favorite Unusual Command"
date: 2008-03-11
forum: The Cafe
---

### Post by wormser on 2008-03-11
Do you have a command that is unusual that most users are unaware of or one that is used in an unusual way.  Post any strange tips and tricks.  Maybe it is a couple of commands put together.  Just anything that is cool that others might find handy,  I will start.

```
chattr -i file
```

Chattr with the -i switch sets an immutable bit. These are attributes to be added to the existing attributes of the files.  A file with the &#8216;i&#8217; attribute cannot be modified, it cannot be deleted or renamed,

```
lsattr file
```

Lsattr displays the chattr permissions.

Post'em.

---

### Post by blithen on 2008-03-11
```
free -m
```
It shows the ram usage.

---

### Post by Hallvor on 2008-03-11
[hallvor@localhost ~]$ df
Filesystem            Size  Used Avail Use% Mounted on
/dev/hdb1              11G  3,8G  6,1G  39% /
/dev/hdb3             101G   72G   25G  75% /mnt/hdb3
/dev/sda1             230G   92G  127G  43% /mnt/sda1
[hallvor@localhost ~]$

---

### Post by odiseo77 on 2008-03-11
I don't think these are unusual or something, but are interesting (at least to me):

```
history
history | grep -i <some piece of some command you forgot>
```

As many of you surely know, the *history* command displays the last nn commands used. If you remember a part of a command you want to use now, but you don't remember the whole command with its arguments, etc., you can type the last command I typed before and it will give you the command.

Also:

```
!command_name
```

Will execute the last *command_name* used with all it's arguments (useful when you want to use a command used before, which has a long piece of arguments, pipes, etc. Also usefull for repetitive tasks).

```
tail -f some_file
```

The *tail* command shows the last 10 lines of a file (although I think you can tell it to show more (or less) lines). The *-f* option leaves the file opened as it grows (useful to monitor log files quickly as they grow).

And so on. I'm sure there are lots of useful and unusual commands few people know about :)

---

### Post by p_quarles on 2008-03-11
Useful:
```
du /path/to/dir
```
Summarizes the total disk space usage of the target directory. 

Unusual:
```
kdontchangethehostname
```
Informs KDE about hostname changes.

---

### Post by InfinityCircuit on 2008-03-11
I don't know how unusual this is, but I certainly use variations on it a lot.  Let's say i'm running sidux and I want to remove all metapackages associated with the name "sidux-686"

```
dpkg -l  | egrep *sidux-686 | cut -c 8- | cut -c -43 | xargs sudo dpkg -P
```

I'm old-fashioned.

---

### Post by herbster on 2008-03-12
Dunno if unusual, but sometimes if I know the full objective I'll just put everything on one line:

```
cd Desktop && tar cjf stuff.tar files && mv stuff.tar /media/backup && cd /media/backup && rsync -avz stuff.tar host@sshserver:backup/
```

Hitting the "&&" feels almost like a beat, keepin' that CLI rhythm goin' :D

---

### Post by Erik Trybom on 2008-03-12
```
ls -d */
```

It displays the directories contained in the current directory. Not that obvious and very useful.

---

### Post by spupy on 2008-03-12
It's not installed by default, but
```
sl
```
Try it also with these args: -a -l
:twisted:

---

### Post by NightwishFan on 2008-03-12
I am famous for mentioning this one. :)
```
espeak "what you wanna say"
```

---

### Post by fuscia on 2008-03-12
+1 to *espeak "somethingobsceneandgenerallysophomoric"*

---

### Post by spupy on 2008-03-12
> **NightwishFan said:**
> I am famous for mentioning this one. :)
```
espeak "what you wanna say"
```

Thank you!  Ahahahaha

```
espeak "All your base are belong to us"
```

---

### Post by der_joachim on 2008-03-13
```

oachim@remade:~$ cowsay "`fortune`"
 ___________________________________
/ Life is to you a dashing and bold \
\ adventure.                        /
 -----------------------------------
        \   ^__^
         \  (oo)\_______
            (__)\       )\/\
                ||----w |
                ||     ||

```
:)

---

### Post by spupy on 2008-03-13
Thanks to you guys, this is my latest greatest invention. I bring you...

RoboCow.sh:
```
#!/bin/bash
fort=`fortune -a`
cowsay $fort
espeak "$fort"
```

---

### Post by GNUlancer on 2008-03-13
man, info.
Most users seem to be not aware of these :D

---

