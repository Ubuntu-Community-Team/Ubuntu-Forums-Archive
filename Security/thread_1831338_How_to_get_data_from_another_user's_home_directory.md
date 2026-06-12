---
title: "How to get data from another user's home directory (I am allowed to do this)"
date: 2011-08-23
forum: Security
---

### Post by john1923 on 2011-08-23
Hi

I had a student, and she has done some work on her account on my lab computer, but has left the country and is un-contactable.

I have full administrator privileges for this machine, and it is running Ubuntu LTS 10.04

She has a folder which was copied from a windows formatted external hard drive (Probably NTFS) onto her home partition on my machine. 

I can open all of her files, except for those in this folder. 

As I see it the problem is either something to do with the permissions of the files (coming from NTFS), or some kind of Ubuntu security that I am unaware of?

Here are my attempts to open it.

```
$ cd Cambridge/
bash: cd: Cambridge/: Permission denied


$ sudo cp Cambridge/ /home/john/Desktop/
cp: omitting directory `Cambridge/'

$ ls -l
total 2660
drwx------ 6 maria maria    4096 2011-08-12 11:01 Cambridge

$ sudo chmod a+r Cambridge/
$ sudo chmod a+w Cambridge/
$ ls -l
total 2660
drwxrw-rw- 6 maria maria    4096 2011-08-12 11:01 Cambridge

$sudo cp Cambridge/ /home/john/Desktop/
cp: omitting directory `Cambridge/'

$cd Cambridge/
bash: cd: Cambridge/: Permission denied
```

I am a bit stuck, can anyone help?

Thankyou

---

### Post by Azdour on 2011-08-23
Hi,

When copying a directory you need the -r parameter, e.g.

```
sudo cp -r Cambridge/ /home/john/Desktop/

```

After you have copied the directory to /home/john/Desktop you will probably want to change the ownership so you can access the folder and files:

```
sudo chown -R john:john /home/john/Desktop/Cambridge

```

---

### Post by john1923 on 2011-08-23
lol

I was over thinking it.

---

