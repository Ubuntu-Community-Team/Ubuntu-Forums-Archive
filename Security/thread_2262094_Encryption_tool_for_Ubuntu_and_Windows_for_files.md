---
title: "Encryption tool for Ubuntu and Windows for files?"
date: 2015-01-22
forum: Security
---

### Post by chris336 on 2015-01-22
I have sensitive information pertaining to my business that I keep on my computer.  I have been using 7zip on Windows with the settings: No compression (store) and AES256 encryption.  Is there a better/more secure method?  My main worry is that I won't be able to retrieve my information later.  Several years ago, I compressed some files with 7zip and attempted to uncompress them later to no avail.  They were corrupted.  So I basically lost those files.  These new files are much more sensitive.  Also, 7 Zip doesn't work on Ubuntu so I need something cross platform.  Any advice? Thanks
/

---

### Post by Irihapeti on 2015-01-22
I've discovered that you can use gpg keys on Windows. I came across a program called GPG4USB, which will run on both Windows and Linux, and as the name suggests, on a USB drive. You can import your Ubuntu keys and use them to encrypt messages and files. (I'm trying to encourage a family member who is overseas to use it, so far without success.)

Of course, you'd need to be careful that the names of the files don't give away too much. E.g. super_secret_bank_info might not be the best idea.

---

### Post by mastablasta on 2015-01-23
WHAT?: [http://www.7-zip.org/download.html](http://www.7-zip.org/download.html) > p7zip is the command line version of 7-Zip for Unix/Linux, made by an independent developer

anyway what you did is I think possible with default packaging tool. but files can always get corrupted. there is a program that checsk that and tries to prevent it. but versioned autobackup would also help. there are quite a few applications that do that there and encrypt the files as they back them up. might be enough to do backup on external hard disk. 

there are otherwise various option to lock your data. or you can try truecrypt (or rather it's continuation) container: [https://truecrypt.ch/](https://truecrypt.ch/)

---

### Post by coldraven on 2015-01-23
Masterblaster is correct, 7Zip is in the Software Centre. I have installed on Ubuntu 14.04.

---

### Post by sudodus on 2015-01-23
In my Ubuntu 12.04 LTS it is called ***7z*** with the following version ínfo.

```
7-Zip 9.20  Copyright (c) 1999-2010 Igor Pavlov  2010-11-18
p7zip Version 9.20 (locale=sv_SE.UTF-8,Utf16=on,HugeFiles=on,4 CPUs)

Usage: 7z <command> [<switches>...] <archive_name> [<file_names>...]
       [<@listfiles...>]

...
```

I installed it with the package p7zip-full

```
sudo apt-get install p7zip-full
```

But gpg (suggested by *Irihapeti*) is more advanced and a good choice if you are prepared to change to another tool.

---

### Post by bashiergui on 2015-01-24
> **chris336 said:**
> I have sensitive information pertaining to my business that I keep on my computer.  I have been using 7zip on Windows with the settings: No compression (store) and AES256 encryption.  Is there a better/more secure method? AES256 is pretty solid. I rely on it. It's dependent on the password though -use strong ones and different ones for each file. Consider keepass or something to store the passwords safely. And back that up too.

GPG is a good choice, it's just not user friendly.> My main worry is that I won't be able to retrieve my information later.  Several years ago, I compressed some files with 7zip and attempted to uncompress them later to no avail.  They were corrupted.  So I basically lost those files.  These new files are much more sensitive. Solve that with backups. Use a cloud service or two- if you're uploading encrypted files then if the cloud service has a breach no one will be able to read your data.

---

### Post by Habitual on 2015-01-24
[http://www.spi.dod.mil/ewizard.htm](http://www.spi.dod.mil/ewizard.htm) but to trust that source (neighbor of the NSA)?

---

### Post by HermanAB on 2015-01-26
FreeOTFE:
[http://sourceforge.net/projects/freeotfe.mirror/](http://sourceforge.net/projects/freeotfe.mirror/)

It is also used by the government.  It works.

---

### Post by tripp98 on 2015-02-22
[https://truecrypt.ch/](https://truecrypt.ch/)

Is another option.  Files are saved within an encrypted file.  can mount it like a drive.

---

### Post by HermanAB on 2015-02-24
and to protect against bit rot, use rsbep or par2 (also pypar2).

---

