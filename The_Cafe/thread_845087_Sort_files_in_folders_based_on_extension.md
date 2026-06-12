---
title: "Sort files in folders based on extension"
date: 2008-06-30
forum: The Cafe
---

### Post by Carroarmato0 on 2008-06-30
Hi everyone!

I'm looking for a script or application that can sort files and put them in different folders based on their extension.

These files are already in folders but mixed with other file types.

The goal is to go into every folder and move every file it encounters into a specified destination based on the extension.

Expl:  all .jpeg .png and .gif  should be move into the "Pictures" folder.
       
       all .doc  .txt           should be in "Documents".

---

### Post by Dixon Bainbridge on 2008-06-30
That would be a sweet plug-in for nautilus/thunar/whatever you use.

Put my name on the want to know list. :)

---

### Post by DJ_Peng on 2008-06-30
As [K-9]("http://en.wikipedia.org/wiki/K-9_%28Doctor_Who%29") would say, piece of cake, master. In Nautilus, View > Arrange Files > By Type. That should sort your files by the extension.

---

### Post by Barrucadu on 2008-06-30
Ok, this is just a *very* quick and simple solution I whipped together, but it works. It doesn't quite do what you wanted, but you could modify it, or move the sorted files by hand.
```
#!/bin/dash

mkdir "$1"

for file in *.$1; do
  mv "$file" "$1"
done

```

Usage: /path/to/the/script.sh filetype
Note: Do not include a dot in the filetype! Just, for example, jpg .

---

### Post by sisco311 on 2008-06-30
```
find /home/username/mixedfiles -type f \( -iname '*.jpeg' -o -iname '*.png' -o -iname '*.gif' \) -exec cp -i '{}' /home/username/Pictures \;
```**find** - command to find files

** /home/username/mixedfiles **- path to the folder where the mixed files are

** -type f** - search for files (omit directories)

** \( -iname '*.jpeg' -o -iname '*.png' -o -iname '*.gif' \)** - search for jpeg, png and gif files

** -exec** - execute a command

** cp **- copy files

** -i** - interactive (prompt before overwrite)

** '{}'** - will be replaced by the file name (with path) returned by the search

** /home/username/Pictures** - destination directory

** \; **- separate one cp command from the next

---

### Post by Carroarmato0 on 2008-06-30
> **Barrucadu said:**
> Ok, this is just a *very* quick and simple solution I whipped together, but it works. It doesn't quite do what you wanted, but you could modify it, or move the sorted files by hand.
```
#!/bin/dash

mkdir "$1"

for file in *.$1; do
  mv "$file" "$1"
done

```

Usage: /path/to/the/script.sh filetype
Note: Do not include a dot in the filetype! Just, for example, jpg .

> **sisco311 said:**
> ```
find /home/username/mixedfiles -type f \( -iname '*.jpeg' -o -iname '*.png' -o -iname '*.gif' \) -exec cp -i '{}' /home/username/Pictures \;
```**find** - command to find files

** /home/username/mixedfiles **- path to the folder where the mixed files are

** -type f** - search for files (omit directories)

** \( -iname '*.jpeg' -o -iname '*.png' -o -iname '*.gif' \)** - search for jpeg, png and gif files

** -exec** - execute a command

** cp **- copy files

** -i** - interactive (prompt before overwrite)

** '{}'** - will be replaced by the file name (with path) returned by the search

** /home/username/Pictures** - destination directory

** \; **- separate one cp command from the next


Wow thanks guys.... I'll evaluate which one I'll give a try!

---

### Post by Carroarmato0 on 2008-06-30
> **sisco311 said:**
> 
Code:

find /home/username/mixedfiles -type f \( -iname '*.jpeg' -o -iname '*.png' -o -iname '*.gif' \) -exec cp -i '{}' /home/username/Pictures \;

find - command to find files

/home/username/mixedfiles - path to the folder where the mixed files are

-type f - search for files (omit directories)

\( -iname '*.jpeg' -o -iname '*.png' -o -iname '*.gif' \) - search for jpeg, png and gif files

-exec - execute a command

cp - copy files

-i - interactive (prompt before overwrite)

'{}' - will be replaced by the file name (with path) returned by the search

/home/username/Pictures - destination directory

\; - separate one cp command from the next

Is there an option in FIND to also enter sub-directories? Because these mixed files are also in different folders....

---

### Post by Carroarmato0 on 2008-06-30
> **DJ_Peng said:**
> As [K-9]("http://en.wikipedia.org/wiki/K-9_%28Doctor_Who%29") would say, piece of cake, master. In Nautilus, View > Arrange Files > By Type. That should sort your files by the extension.

Thanks, but I need something more advanced than that. :)

---

### Post by sisco311 on 2008-06-30
> **Carroarmato0 said:**
> Is there an option in FIND to also enter sub-directories? Because these mixed files are also in different folders....
find will search automatically in the sub-directories.

---

### Post by Carroarmato0 on 2008-06-30
Thank you. As soon as Photorec has recovered my lost files from my other pc's hard drive I'm going to use this command to make life easier for me to reorganize stuff. :)

---

### Post by sisco311 on 2008-06-30
> **Carroarmato0 said:**
> Thank you. As soon as Photorec has recovered my lost files from my other pc's hard drive I'm going to use this command to make life easier for me to reorganize stuff. :)
NOTE: The command will copy the files(not move). If you want to move the files replace cp with mv. It's allways a good idea to **backup** your files.

---

### Post by Carroarmato0 on 2008-06-30
> **sisco311 said:**
> NOTE: The command will copy the files(not move). If you want to move the files replace cp with mv. It's allways a good idea to **backup** your files.

The funny thing is, that the accident happened while making a backup. :D

I was making a backup through nfs and compressing the files as they came over to the other pc.... but because I thought it would take too much time I stopped the process. Little did I know that it was moving the files instead of copying them. And so here I am recovering my whole hard drive.

Note to myself: next time I install another distro I'd better make a separate Home partition to avoid recovering the whole drive! :)

---

### Post by Akira Takano on 2011-09-20
Sorry to post on a dead thread, but I just wanted to say if I had not found this thread, I would be out of the job, as I mistakingly formatted a clients drive in the process of reinstalling Ubuntu 11.04.    ):P

---

### Post by sisco311 on 2011-09-20
Necrobumping. 

Thread closed.

@Akira Takano
You are welcome! ;)

---

