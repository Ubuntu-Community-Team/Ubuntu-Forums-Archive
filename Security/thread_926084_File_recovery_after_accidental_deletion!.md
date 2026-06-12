---
title: "File recovery after accidental deletion!"
date: 2008-09-21
forum: Security
---

### Post by jesushero on 2008-09-21
I accidentally typed in rm * instead of rm *~ just before doing a backup.. Nothing EXTREMELY severe, not worth removing any hardware or stuff like that to recover it. However I did some attempts in simple ways and I am a bit stuck. Any ideas?


ls output:
```
user@server:~/test/randtest$ ls -l
total 0

```


fls output:
```
user@server:~$ sudo fls /dev/sda1 35667973
r/r * 35667982:	mainprog.sh
r/r * 35667981:	loop.sh
r/r * 35667976:	append.num
r/r * 35667978:	fold.num
r/r * 35667979:	time.log
r/r * 35667982:	.gedit-save-0N4SHU
r/r * 35667980:	loop.sh~
r/r * 35667975:	mainprog.sh~

```

I tried using icat with the fls output numbers, but it returned NO output! 

Then I tried with dcat:
```
user@server:~$ sudo dcat /dev/sda1 35667982 > file
```

The file is full of some weird characters, like cat-ing a binary file. Nothing useful there!

Is there a way I can read the files or mark them as "still there" instead of "free space"?

All the files on the fls output were deleted. I would like to recover all of them if possible.

---

### Post by Irihapeti on 2008-09-21
These links might be helpful.

[http://www.psychocats.net/ubuntucat/recovering-windows-files-with-a-ubuntu-cd-i-the-backstory/](http://www.psychocats.net/ubuntucat/recovering-windows-files-with-a-ubuntu-cd-i-the-backstory/)
[http://www.cgsecurity.org/wiki/PhotoRec](http://www.cgsecurity.org/wiki/PhotoRec)

---

### Post by jesushero on 2008-09-22
> **Irihapeti said:**
> These links might be helpful.

[http://www.psychocats.net/ubuntucat/recovering-windows-files-with-a-ubuntu-cd-i-the-backstory/](http://www.psychocats.net/ubuntucat/recovering-windows-files-with-a-ubuntu-cd-i-the-backstory/)
[http://www.cgsecurity.org/wiki/PhotoRec](http://www.cgsecurity.org/wiki/PhotoRec)



Thanks, but it's neither photos nor windows files that I'm trying to recover. It's Unicode Text files, saved on an ext3 partition, under Linux.

PhotoRec works for photos and the first link gives details on booting a Linux live CD to recover FAT or NTFS partitions.

Thanks anyway.

---

### Post by Irihapeti on 2008-09-22
OK, I didn't quite make myself clear. PhotoRec works for any kinds of files, not just photos. Also, although the psychocats link describes Windows recovery, it will work on other system types.

Having said that, I've not actually used the program myself. Maybe someone who has can comment.

Irihapeti

---

