---
title: "vim ignores file permissions ?!"
date: 2011-03-24
forum: Security
---

### Post by kapetr on 2011-03-24
I'm hoping, it is just my fault/ignorance, but I will ask better ...

See this sequence:
> 
hugo@duron650:~$ vim test.txt
->writing some text
hugo@duron650:~$ ll test.txt
-rw-r--r-- 1 hugo hugo 13 2011-03-24 10:03 test.txt
hugo@duron650:~$ sudo chown root:hugo test.txt
hugo@duron650:~$ ll test.txt
-rw-r--r-- 1 root hugo 13 2011-03-24 10:03 test.txt
hugo@duron650:~$ LANG=en chown hugo:hugo test.txt
chown: changing ownership of `test.txt': Operation not permitted
hugo@duron650:~$ LANG=en chmod g+w test.txt
chmod: changing permissions of `test.txt': Operation not permitted
hugo@duron650:~$ vim test.txt
->when insertig text I get:
->"-- INSERT -- W10: Warning: Changing a readonly file"
->make some changes
->trying save with "x":
->"E45: 'readonly' option is set (add ! to override)"
->**but saving with "x!" succeeds ?!**
hugo@duron650:~$ ll test.txt
-rw-r--r-- 1 hugo hugo 15 2011-03-24 10:05 test.txt
hugo@duron650:~$ 




**How is possible, that vim can write to file and changes his ownerchip ?!**

(BTW: vim binary has no suid permission)

--kapetr

---

### Post by DaithiF on 2011-03-24
this is normal (though admittedly a little surprising when you first encounter it).

In Linux, if you have write access to a directory, and the sticky bit is not set, then you can create / delete anything in that directory.  even stuff that doesn't belong to you, or that you don't have permissions over.

try it:
```
sudo mkdir test
sudo chmod a+w test
sudo touch test/rootsfile
rm -f test/rootsfile

```its gone...
on the other hand ...
```
sudo chmod +t test
sudo touch test/rootsfile
rm -f test/rootsfile
```
fails ... because now the sticky bit is set so i can no longer mess with root's files in that directory.

---

### Post by kapetr on 2011-03-24
Thank You very much for replay and explanation.

In the meantime in I had use "chattr +i" but the use of standard sticky bit is probably cleaner solution. Maybe I could do it for whole dir (like /tmp do).

Just I'm not sure, what in fact vim does by "x!". I would expect vim should in our example to fail with impossibility to change "read only" permission. And vim (if forcing write) deletes the original file and creates new one ?! Or what ?

--kapetr

P.S.: I see just now, that sticky bit on regular file has no effect. So I have to use it on directory.

Before I have try to do that, I have deleted the "i" chattr flag, but now I can not do anything with this file. Not edit, delete, chown, ... as root, ... I'm confused ?:-/

---

### Post by DaithiF on 2011-03-24
> **kapetr said:**
> 
Just I'm not sure, what in fact vim does by "x!". I would expect vim should in our example to fail with impossibility to change "read only" permission. And vim (if forcing write) deletes the original file and creates new one ?! Or what ?

you know the crazy thing about open-source, you can take a look :)
```
apt-get source vim
cd vim-7.2.330/src
grep ":w\!" *.c
```
and you'll see that fileio.c is the file that you want to look at 
in there, this comment:
```
If we can't write to the
    * file and forceit is TRUE we delete the existing file and try to create
     * a new one.
```

---

### Post by kapetr on 2011-03-24
How to reproduce the NEW problem.

- user hugo creates file
- sudo chown root:hugo file
- sudo chattr +i file
-> no one can modify/delete the file (that's OK)
- sudo chattr -i file

-> ?! still no one can modify/delete the file ?!

It the same is done at not chowned file, than after clear of "i" chattr the file is accessable/deletable normally.

What is happened ?

--kapetr

---

