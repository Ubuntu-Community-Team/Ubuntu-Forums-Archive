---
title: "Filename can still be changed, even if permissions are set to &quot;a=r&quot;"
date: 2013-05-16
forum: Server Platforms
---

### Post by roooii on 2013-05-16
Hello there I am again,

I'm starting to understand the permission system more and more. But one thing I don't get is why I can still change the name of the file "testbestand.php". I can't make any other changes to it, but I can change the name. Below you can see the permissions. I can change the name with the FTP (vsFTPd), haven't tried changing it locally. Any ideas? I mean "read only" should be read only right? Does this have to do with vsFTPd ignoring the permissions maybe?

ls -la
-r--r--r-- 1 roy  mycustomgroup    4 May 16 10:42 testbestand.php

Thanks for the responses.

---

### Post by steeldriver on 2013-05-16
The *contents* of the file belong to the file - so changing file permissions determines what each user can do with what's *inside* the file

The *name* of the file belongs to its parent directory - so you need to change *directory* permissions to control who can rename / create / remove the file e.g.

```

$ mv -v tests/file tests/newfile
`tests/file' -> `tests/newfile'
$ 
$ chmod -w tests
$ mv -v tests/newfile tests/file
mv: cannot move `tests/newfile' to `tests/file': Permission denied
$ 
$ chmod ug+w tests
$ mv -v tests/newfile tests/file
`tests/newfile' -> `tests/file'
$ 

```

[If it helps, you can think of a directory as a file that contains the attributes - name, size, type etc. - of each of the files inside it]

---

### Post by Morbius1 on 2013-05-16
What are the permissions of the parent directory of this file?

Let's say you have a folder and it's permissions are 777 - i.e., drwxrwxrwx

Everyone has the ability to read and write to that directory but not necessarily edit any of the files in that directory. But a "write" in this context gives them the ability to rename or even delete a read only file just not edit it's content. There's a bizarre kind of logic to this if you took a lot of drugs in the late 1960's when UNIX was invented.

[COLOR=#0000cd]EDIT: I have to learn to always look to see if someone has posted a response while I create mine. steeldriver answered this far more elegantly but I contend mine was funnier.[/COLOR]

---

### Post by roooii on 2013-05-16
Thanks a lot after setting chmod 775 to the parent directory it got fixed. To be honest, the permissions of the parent-directory were set 777 :P pretty unsafe.

---

### Post by SeijiSensei on 2013-05-16
Unless you are using groups and group ownerships, I'd change the permissions to 755.

---

