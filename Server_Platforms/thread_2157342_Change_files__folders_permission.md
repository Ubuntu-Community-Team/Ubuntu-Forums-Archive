---
title: "Change files / folders permission"
date: 2013-06-25
forum: Server Platforms
---

### Post by alfirdaous on 2013-06-25
Hello everybody,

I would like to change files persmission to 644 and folders to 755 at once, structure is like this:

```

+Folder1
++ SubFolder1
+++ File1
+++ File2
+++ File3
++ SubFolder2
++ SubFolder3

+ Folder2
Etc


```

how can I do that at once.

Thanks in advance

---

### Post by steeldriver on 2013-06-25
You can use 

```

find Folder1 -type d -exec chmod 755 {} +
find Folder1 -type f -exec chmod 644 {} +

```

or maybe just

```
chmod -R u=rwX,go=rX Folder1
```

---

### Post by alfirdaous on 2013-06-25
Thx, but in this case I should go folder by folder if I have 20 folders from 1 to 20, I should do it 20 times

---

### Post by steeldriver on 2013-06-25
No both methods act recursively (from Folder1 down to all files / folders below)

---

### Post by alfirdaous on 2013-06-25
yes, I agree with you, but this will take effect for Folder1 and subFolders (down of Folder1), will not take in action Folder2, Folder3 etc

---

### Post by steeldriver on 2013-06-25
Apologies, I didn't notice that requirement

It depends what else is in the parent directory of Folder1 and Folder2 - if you want to change EVERY folder you could use a * shell glob (wildcard)

```
chmod -R u=rwX,go=rX ***/**
```

in the parent directory. Or if all the folders you want to change have some identifying element in their name (e.g. if they really are called 'Folder**1**', 'Folder**2**' etc.) then you could do

```
chmod -R u=rwX,go=rX **Folder*/**
```

I don't think it's possible to come up with a general rule that works 100% of the time if we don't know what other files/folders you have in the same directory.

---

### Post by alfirdaous on 2013-06-25
and how about files?

---

### Post by alfirdaous on 2013-07-01
I used this for folders and it works, how about files permission, to be set on 644:

Folders:
[code]

chmod -R u=rwX,go=rX [B]*/
[/B][code]

---

### Post by steeldriver on 2013-07-01
```
chmod -R u=rwX,go=rX */
```

matches all *directories* ('*/') in the current directory, then recursively changes all directories and files below that - the only files it will exclude are those at the top level of the current directory, if you want to include those you can just match everything ('*')

 ```
chmod -R u=rwX,go=rX *
```

---

### Post by alfirdaous on 2013-07-01
could explain to me please this one:

```


u=rwX,go=rX

```

---

