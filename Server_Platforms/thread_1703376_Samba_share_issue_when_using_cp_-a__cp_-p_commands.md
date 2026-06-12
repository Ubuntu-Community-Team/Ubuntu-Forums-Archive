---
title: "Samba share issue when using cp -a / cp -p commands"
date: 2011-03-09
forum: Server Platforms
---

### Post by jolig on 2011-03-09
Hello all !


I am currently experiencing issues with samba share.
I have several samba server (9.10, 10.04 & 10.10) in my network, each of them are mounted on my local machine.

For each of these samba share, when I am trying to do a copy preserving the rights, I am getting an error :
```

uuuu@yyyy:~/__corei7$ touch test.txt
uuuu@yyyy:~/__corei7$ ls -al test.txt
-rw-rw---- 1 uuuu gggg 0 2011-03-09 13:04 test.txt
uuuu@yyyy:~/__corei7$ ls -al test.txt
uuuu@yyyy:~/__corei7$ cp test.txt test2.txt --preserve=timestamps
uuuu@yyyy:~/__corei7$ ls test2.txt -al
-rw-rw---- 1 uuuu gggg 0 2011-03-09 13:04 test2.txt
uuuu@yyyy:~/__corei7$ cp test.txt test2.txt --preserve=timestamps,ownership
uuuu@yyyy:~/__corei7$ cp test.txt test2.txt --preserve=timestamps,ownership,links
uuuu@yyyy:~/__corei7$ cp test.txt test2.txt --preserve=timestamps,ownership,links,context
cp: cannot preserve security context without an SELinux-enabled kernel
uuuu@yyyy:~/__corei7$ cp test.txt test2.txt --preserve=timestamps,ownership,links,xattr

uuuu@yyyy:~/__corei7$ cp test.txt test2.txt --preserve=timestamps,ownership,links,xattr
uuuu@yyyy:~/__corei7$ cp test.txt test2.txt --preserve=timestamps,ownership,links,xattr,mode
cp: preserving permissions for `test3.txt': Permission denied

```

While I can do a chmod without any problem the created file :

```

uuuu@yyyy:~/__corei7$ ls -al test2.txt
-rw-rw---- 1 uuuu gggg 0 2011-03-09 13:04 test2.txt
uuuu@yyyy:~/__corei7$ chmod ugo+rwx test2.txt
uuuu@yyyy:~/__corei7$ ls -al test2.txt
-rwxrwxrwx 1 gjoli alse 0 2011-03-09 13:04 test2.txt
uuuu@yyyy:~/__corei7$ rm test2.txt
uuuu@yyyy:~/__corei7$ ls -al test2.txt
ls: cannot access test2.txt: No such file or directory

```


Any hint ?
Thanks in advance !

---

### Post by jolig on 2011-03-09
up :)

---

### Post by jolig on 2011-03-22
up :(

---

### Post by SeijiSensei on 2011-03-22
Are you trying to use "cp -a" to copy files to a share that's mounted from a Samba server?  Samba shares are like Windows shares; they don't have any concept of *nix permissions.

If you want to mount remote filesystems exported from Linux servers and preserve their permissions, you need to use NFS instead of Samba.

---

### Post by jolig on 2011-03-25
> **SeijiSensei said:**
> Are you trying to use "cp -a" to copy files to a share that's mounted from a Samba server?  Samba shares are like Windows shares; they don't have any concept of *nix permissions.

If you want to mount remote filesystems exported from Linux servers and preserve their permissions, you need to use NFS instead of Samba.

Hello,

I tought samba (CIFS) has unix extension in order to handle permissions as well as users management ?
I am actually trying to copy a file from my local mount (ext4) to a CIFS share mount (ext4).
After some test, here are the results :

CIFS  -> CIFS  => cp: preserving permissions for `test.txt': Permission denied
CIFS  -> local => OK !
local -> CIFS => cp: preserving permissions for `test.txt': Permission denied

So, the problems seems to be located on the CIFS mount that is not handling the modification of the permissions.
Any way to fix that ?

---

### Post by jolig on 2011-03-25
Note: It might be related to an old version of samba !
My server runs smbd version 3.4.0 (Ubuntu 9.10)

I've done a short try with samba 3.5.4 <-> 3.5.6 an it seems to be working !
I need to check this more in depth asap (cannot currently upgrade the server, too risky) and i'll get back to you

---

