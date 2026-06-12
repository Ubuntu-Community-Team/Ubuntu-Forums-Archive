---
title: "Seemingly nonexistent file"
date: 2012-05-04
forum: Server Platforms
---

### Post by mcookie on 2012-05-04
So I recently switched from the 10.04 LTS to server edition, and I have been having some problems with some file permissions (most of which I have cleared up) and some other problems. This server is hosting quite a few different things, or was, at least; one of these was a ventrilo server. I transfered the tarball via FTP, which worked fine after some fiddling, and the untarred it using "tar -zxf...". With 10.04, navigating to the correct directory and then typing "./ventrilo_srv would run the server just fine, but I have a rather strange problem with the server edition. 

I try doing it the same way I did in 10.04, but it returns ```
bash: ./ventrilo_srv: No such file or directory
```.  Having seen the file there a few minutes ago, I ls -l'd and found that it was, in fact, there. This has me stumped, however I am not exactly an expert, so I hope someone can help.

inb4 wrong forum

---

### Post by codemaniac on 2012-05-05
Just to make sure , can you try using the full path name of ventrilo_srv , while running this executable instead of ./ventrilo_srv .

---

### Post by mcookie on 2012-05-05
Same problem:
```
/home/shark/ventrilo/ventsrv/ventrilo_srv
```
```
bash: /home/shark/ventrilo/ventsrv/ventrilo_srv: No such file or directory
```

---

### Post by CharlesA on 2012-05-05
Run this:

```
ls -l /home/shark/ventrilo/ventsrv/ventrilo_srv
```

---

### Post by mcookie on 2012-05-05
It gives me
```
-rwxr-x--- 1 shark 468420 Nov 18 2008 /home/shark/ventrilo/ventsrv/ventrilo_srv
```

---

### Post by CharlesA on 2012-05-05
```
chmod +x /home/shark/ventrilo/ventsrv/ventrilo_srv
```

Should work now.

---

### Post by David Andersson on 2012-05-05
> **mcookie said:**
> It gives me
```
-rwxr-x--- 1 shark 468420 Nov 18 2008 /home/shark/ventrilo/ventsrv/ventrilo_srv
```

There should be *two* names around "shark", the owner and a group. Do you, as a user *or* group, have both read *and* execute access?

A less likely cause for that error message could be if the script by accident have got DOS-line-endings (CR+LF) instead of Unix-line-endings (LF). If you open the file in *nano* I think it will show the CR in the line endings.

---

### Post by mcookie on 2012-05-05
That was a typo by me. it *was* 
```
-rwxr-x--- 1 shark shark 468420 Nov 18 2008 /home/shark/ventrilo/ventsrv/ventrilo_srv
```

After "chmod +x ...." I get the exact same problem. Even if the file wasn't set to be executable, wouldn't it still return something beside "No such file or directory"?

---

### Post by CharlesA on 2012-05-05
Run a fsck on the drive.

```
sudo touch /forcefsck && sudo reboot
```

---

### Post by mcookie on 2012-05-05
Exact same problem. Also, very nice Firefly-class spaceship.

---

### Post by CharlesA on 2012-05-06
> **mcookie said:**
> Exact same problem. Also, very nice Firefly-class spaceship.

Thanks. ;)

It should give you a permission denied message if you don't have execute permissions.

```
charles@Thor:~$ chmod -x archive.sh
charles@Thor:~$ ./archive.sh
-bash: ./archive.sh: Permission denied

```

Have you tried unpacking the archive again?

---

### Post by mcookie on 2012-05-06
The file I'm trying to execute isn't a shell script. It doesn't even have a file ending. Howver this same exact method worked fine on 10.04 with a GUI. It isn't saying that my permission is denied, I even did chmod +rx <file path> and I still have the same problem.

---

### Post by David Andersson on 2012-05-06
> **mcookie said:**
> The file I'm trying to execute isn't a shell script. It doesn't even have a file ending.
What file type does **file ventrilo_srv** say it is?

> **mcookie said:**
> It isn't saying that my permission is denied, I even did chmod +rx <file path> and I still have the same problem.
If *read* permission is lacking I get "No such file or directory". (It's a bit unintuitive, but the OS reads the file twice, first to see the #!-line and then start it with the interpreter it found there. How I understand it, it must do things in such a way that you cannot replace the file with another file with different permissions between the two reads.)

If the permission of the file is right, can you see if the filesystem containing the file is mounted with limited permissions (thou mount option "noexec" would give "Permission denied"). Or if the parent directories have limitations in their permissions (thou I don't know how that would matter)?

EDIT: Do you start the script as "shark" or "root"?

---

### Post by mcookie on 2012-05-06
> **David Andersson said:**
> What file type does **file ventrilo_srv** say it is?
It says
```
./ventrilo_srv: ELF 32-Git executable, Intel 80386, version 1 (SYSV), dynamically linked (uses shared libs), stripped
```

> **David Andersson said:**
> EDIT: Do you start the script as "shark" or "root"?
I have tried both, and both give the "No such file or directory".

[IMG]http://s3.kkloud.com/gett/9icKB0H/IMG_20120506_194446.jpg.0x675.yfij6s0lsb1n61orp564kb4g7ckp4x6r.jpg[/IMG]
A picture of the filename from "ls -l".

---

### Post by Meriani on 2012-05-09
I'm running into the exact same problem.

From running a strings against ventrilo_srv, I see that it's trying to use the library /lib/ld-linux.so.2 - which was apparently removed during the upgrade from 11.10 to 12.04.

Thankfully, I had a backup copy of this library, which I copied into my /lib directory, after which I then ran 'ldconfig'.

This has now changed the error to:
```
# ./vent/ventrilo_srv
./vent/ventrilo_srv: error while loading shared libraries: libdl.so.2: cannot open shared object file: No such file or directory
```I then recovered this library from my backup: /lib/i386-linux-gnu/libdl.so.2. Ventrilo then stated it needed libc.so.6, also from /lib/i386-linux-gnu, so I grabbed it too.

After getting all of these libraries and running ldconfig, I am able to start my ventrilo server.

Hope it helps. Also, set your ventrilo_srv permissions back to 750. :)

---

### Post by mcookie on 2012-05-09
Actually, I just a few hours ago got it running from a tutorial  followed. Apparently, it is now required to move some things to /etc/init.d and to /usr/bin. It works perfectly now; here's the tutorial if anyone cares for it.

[http://rocketeerbkw.com/content/installing-ventrilo-server-ubuntu-910-karmic-koala]("http://rocketeerbkw.com/content/installing-ventrilo-server-ubuntu-910-karmic-koala")

---

