---
title: "3 ways of listing files and directories, any more?"
date: 2009-07-07
forum: The Cafe
---

### Post by dragos240 on 2009-07-07
Hi, I noticed that you can list all the files and directories, 3 ways:

ls
dir
echo *

any more?

---

### Post by andrewc6l on 2009-07-08
find . -maxdepth 1

---

### Post by Trail on 2009-07-08
locate $(pwd), i guess. I don't have locate installed atm to test.

---

### Post by dragos240 on 2009-07-08
> **Trail said:**
> locate $(pwd), i guess. I don't have locate installed atm to test.
That locates all the files inside the current directory :o

---

### Post by adrianx on 2009-07-08
tree

---

### Post by Trail on 2009-07-09
> **dragos240 said:**
> That locates all the files inside the current directory :o

Ah, you don't want subdirectories...

```

locate $(pwd) | egrep ^$(pwd) | cut -d'/' -f$(expr 1 + $(echo $PWD/ | tr -cd '/' | wc -c)) | sed /^$/d | sort | uniq

```

 :P

Doesn't work for / though.

---

