---
title: "Shred a folder?"
date: 2010-12-02
forum: Security
---

### Post by PDA1 on 2010-12-02
I use Shred to delete individual files but can't figure out how to delete an entire folder using it.



Can someone please give me simple instructions for how to delete a folder?  Please make it easy to understand- I'm not really tech lingo-savy.

---

### Post by amauk on 2010-12-02
You're not Mr. Assange are you? :p

you can perform operations on multiple files by using wildcards

Ie.
shred /path/to/dir/*

---

### Post by wojox on 2010-12-02
Shred is just for files. Download secure-delete

```
sudo apt-get install secure-delete
```

```
srm -r myfiles/
```

---

### Post by PDA1 on 2010-12-02
> **amauk said:**
> You're not Mr. Assange are you? :p



you can perform operations on multiple files by using wildcards

Ie.
shred /path/to/dir/*


I'm Elvis

---

### Post by PDA1 on 2010-12-02
> **wojox said:**
> Shred is just for files. Download secure-delete

```
sudo apt-get install secure-delete
``````
srm -r myfiles/
```


Thanks, but would you please give me an example using the folder /Pictures

I have no idea how to interpret the syntax for crm.

---

### Post by wojox on 2010-12-02
```
srm -r Pictures
```

---

### Post by PDA1 on 2010-12-02
> **wojox said:**
> ```
srm -r Pictures
```


Shouldn't it be srm -r /Pictures     ?

---

### Post by cariboo on 2010-12-02
Using the slash before Pictures implies that the folder is in the root directory.

---

### Post by PDA1 on 2010-12-02
I entered-  srm -r Pictures/


The error message I got was; 

Error: File SRM - No such file or directory
Error: File Pictures/ - No such file or directory

---

### Post by PDA1 on 2010-12-02
I figured it out;

srm -r /home/Frank/Pictures



Pretty easy but it take a while to delete large files.

---

### Post by cariboo on 2010-12-02
Using ~/Pictures does the same thing, and you don't have to type as much. :)

---

### Post by mehmeh12 on 2010-12-02
Dont mean to hijack this thread but does moving files from a home folder to the trash and then deleting the trash under the program 'bleachbit' securely delete these files for good?

---

### Post by phillips321 on 2010-12-03
There is no secure way to delete all the porn you have collected other than to write over the hard disk area over and over.

Beware though, digital forensics has shown that even when a file has been "wiped" it is possible to still retrieve it due to disk align errors.

---

### Post by wojox on 2010-12-03
> **mehmeh12 said:**
> Dont mean to hijack this thread but does moving files from a home folder to the trash and then deleting the trash under the program 'bleachbit' securely delete these files for good?

I know there is an "Overwrite" Option in bleachbit, but I don't know how many passes it takes.

I really don't really believe any files are "securely deleted". ;)

---

### Post by mehmeh12 on 2010-12-03
> **phillips321 said:**
> There is no secure way to delete all the porn you have collected other than to write over the hard disk area over and over.

Beware though, digital forensics has shown that even when a file has been "wiped" it is possible to still retrieve it due to disk align errors.


So how does one security delete files permanently? reformat the system? physical destruction of the drive itself?

---

### Post by mehmeh12 on 2010-12-03
> **wojox said:**
> I know there is an "Overwrite" Option in bleachbit, but I don't know how many passes it takes.

I really don't really believe any files are "securely deleted". ;)

it says on the bleachbit sourceforge website that it only wipes files once.... How many times does the 'secure delete' terminal command in ubuntu do?

---

### Post by wojox on 2010-12-04
> **mehmeh12 said:**
> it says on the bleachbit sourceforge website that it only wipes files once.... How many times does the 'secure delete' terminal command in ubuntu do?

Open a terminal and 

```
man srm
```

After you have installed secure delete. It will give you different options.

---

### Post by Andrew.Z on 2010-12-04
> **mehmeh12 said:**
> Dont mean to hijack this thread but does moving files from a home folder to the trash and then deleting the trash under the program 'bleachbit' securely delete these files for good?

BleachBit 0.8.x has a menu option for deleting files anywhere (it lets you browse), and 0.8.3 (due soon) adds a menu option for deleting whole folders (including subdirectories).

> **phillips321 said:**
> There is no secure way to delete all the porn you have collected other than to write over the hard disk area over and over.

Beware though, digital forensics has shown that even when a file has been "wiped" it is possible to still retrieve it due to disk align errors.

It's a [myth that multiple passes are needed to permanently delete files](http://bleachbit.sourceforge.net/documentation/shred-files-wipe-disk).  By disk align errors I think you mean slack space: it is possible after overwriting free disk space to recover small bits of information (smaller than 4K each), but this is not enough to reconstruct meaningful information from most kinds of file.  

> **mehmeh12 said:**
> So how does one security delete files permanently? reformat the system? physical destruction of the drive itself?

The link has a guide to [what it takes to permanently data](http://bleachbit.sourceforge.net/documentation/shred-files-wipe-disk).  Basically there is an order of progression (based on the expected threat) of five steps from shredding an individual file to destroying copies in backups, ISP logs, and online accounts.

---

