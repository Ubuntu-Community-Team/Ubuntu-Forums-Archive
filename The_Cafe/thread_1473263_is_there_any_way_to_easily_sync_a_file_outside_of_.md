---
title: "is there any way to easily sync a file outside of $home with ubuntu one?"
date: 2010-05-05
forum: The Cafe
---

### Post by 133794m3r on 2010-05-05
I ask because right now i'm doing a bit of web development with xampp installed and the normal directory of course is \htdocs\ for the folder with them. Since i don't want to reroute apache to somewhere in the home folder since it seems every time that i do try to do something like that(at least in windows) it decided to just break on me. As i doubt that they'd allow it to work but i was wondering if it was possible.

---

### Post by colaho on 2010-05-05
Dropbox is your friend ;)

---

### Post by 133794m3r on 2010-05-05
> **colaho said:**
> Dropbox is your friend ;)

i guess but i dont' know that company and i do know Canonical, so i believe i can trust them more than i can that random company offering 2GB of free space...

---

### Post by surfdoc on 2010-05-13
Ditto this.

I seemed to be able to trick the client slightly by creating a symlink in my home folder to the desired path. Buy navigating through this link in nautilus, the "sync on ubuntu one" option appeared in the right click menu. However selecting this option doesn't seem to work :-(

---

### Post by surfdoc on 2010-05-13
```
u1sdtool --create-folder=[path to the folder i want to sync]

FolderCreateError: INVALID_PATH: path isn't inside user home:
```

Definitely doesn't want to do it - can't really understand why?

---

### Post by surfdoc on 2010-05-13
I moved the mount point of the folder I wanted to sync into my home folder. It still wont play

```
FolderCreateError: UDFs can not be nested

```

---

### Post by Sam on 2010-05-13
Why don't you set the xampp DocumentRoot to something in your home directory? Problem solved.

---

### Post by 133794m3r on 2010-05-14
> **Sam said:**
> Why don't you set the xampp DocumentRoot to something in your home directory? Problem solved.

never works, tried it in the past. I went and changed the document root in all of the places i knew of and well the site wouldn't load. I'd go to localhost and it'd show the xampp folder still but notthe other ones and was still using /opt/lampp as it'sroot eventhoughi changed it to $home/htdocs/ don't know why it just refuses it.

---

