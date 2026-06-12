---
title: "Quickest way to create directories from a .txt file."
date: 2011-02-08
forum: Server Platforms
---

### Post by Mr Mookie on 2011-02-08
I'm trying to figure out the quickest way to create directories from a .txt or .csv file. A single command would be great but I can use a script as well.

The windows equivalent would be:

FOR /F %n IN (newfolders.txt) DO MKDIR %n

---

### Post by slooksterpsv on 2011-02-08
> **Mr Mookie said:**
> I'm trying to figure out the quickest way to create directories from a .txt or .csv file. A single command would be great but I can use a script as well.

The windows equivalent would be:

FOR /F %n IN (newfolders.txt) DO MKDIR %n

for line in file.txt; do mkdir $line; done

I think will work.

---

### Post by Mr Mookie on 2011-02-08
That's close I think..

tried:
```
for line in folders.txt; do mkdir $line; done
```

```
"mkdir: cannot create directory `folders.txt': File exists"
```

thanks

---

### Post by slooksterpsv on 2011-02-08
for line in $(cat folder.txt); do mkdir $line; done

That's what I missed!

---

### Post by Mr Mookie on 2011-02-08
Thanks! Worked great!

I've been trying to sort this out for hours..

Getting trickier how about a .csv or .xls file that is comma delimited?

---

### Post by slooksterpsv on 2011-02-08
> **Mr Mookie said:**
> lol.. getting warmer?

tried:
```
for line in $(cat folder.txt); do mkdir $line; done
```


recieved:
```
cat: folder.txt: No such file or directory
```

How about:
for line in $((cat folder.txt)); do mkdir $line; done

Odd I'm having to do 2 (( now )) to have it execute what's in between.

---

### Post by Mr Mookie on 2011-02-08
Sorry, I was silly and edited my reply. I had just spelled folder.txt wrong. It was "folders.txt". My next quest would be to do the same for .csv comma delimited files.

---

### Post by Mr Mookie on 2011-02-08
Finally figured it out for a .csv Comma delimited file to create multiple directories.


```
for line in $(cat folder.txt | sed 's/\,/\n/g'); do mkdir $line; done
```


Thanks for the help!

---

