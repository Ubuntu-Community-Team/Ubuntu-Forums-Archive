---
title: "Chown file in external HDD"
date: 2012-05-01
forum: Security
---

### Post by 0011235813 on 2012-05-01
Hi, I'm backing up a file created with tiger john chkrootkit, to my external HDD for safekeeping. That way, if the system is compromised and the file is edited or removed, I will still have the file backed up so I can check it with the new report (this is all just hypothetical of course). Trouble is, I can't get the file to change permissions! When I try;
```
sudo -i
``````
(root@computername:~#)cd /media/My Book/Security
```
```
bash: cd: 'My': no such file or directory found
```
(My Book is the name of the HDD, and Security is the name of the directory it's {the file} is stored under).
or:
```
cd /media/My-Book/Security
```
doesn't work either. But when I do:
```
cd /media
(root@computername:/media#)
```
it works. Using the command;
```
ls
```
I get:
```
My Book
```
But I can't go to it! Does anyone know how to do this? Or any alternative (graphical) method? I can just back it up to cryptkeeper folder, but still.

---

### Post by 0011235813 on 2012-05-01
No matter, I've just compressed it with a simple password to foil any programs or hackers that get in.

---

### Post by cryptotheslow on 2012-05-02
For future reference, using the command line you need to escape the spaces in any path or filenames with a backslash   \

e.g.
```

crypto@ubulaptop1204:~$ cd My\ Book/
crypto@ubulaptop1204:~/My Book$

```

Alternatively use the bash tab to auto-complete.

e.g. 
Type
```
cd My
```

Then press the >Tab< key and the path will be auto-completed with the escaped space already in there.

---

### Post by 0011235813 on 2012-05-02
> **cryptotheslow said:**
> For future reference, using the command line you need to escape the spaces in any path or filenames with a backslash   \

e.g.
```

crypto@ubulaptop1204:~$ cd My\ Book/
crypto@ubulaptop1204:~/My Book$

```Alternatively use the bash tab to auto-complete.

e.g. 
Type
```
cd My
```Then press the >Tab< key and the path will be auto-completed with the escaped space already in there.
Thanks for that!
```
cd /media/My\ Book/
```
worked.

---

### Post by Damascushead on 2012-05-03
I am no expert in this area, but I know from experience that depending on the external device and how it may be formated, it sometimes will simply not allow you to change file permissions even as root. I remember running into this problem with a proprietary external drive that i have myself. 
 
:KS

---

### Post by CharlesA on 2012-05-03
> **Damascushead said:**
> I am no expert in this area, but I know from experience that depending on the external device and how it may be formated, it sometimes will simply not allow you to change file permissions even as root. I remember running into this problem with a proprietary external drive that i have myself. 
 
:KS
If the device is running NTFS or FAT, it won't let you chown or chmod, the owners/group and permissions are set at mount.

---

### Post by beboylips on 2012-05-04
Hey,

When using paths with spaces or capitals, etc, use single quotes around the path.

Ex:

```

cd '/media/HDD/My Backup/file.txt'

```

Also CaSe sensitive.

If your HD is running NTFS, no file permissions are supported.

---

