---
title: "Cant download into a created folder"
date: 2012-09-17
forum: Ubuntu +1 (Quantal Quetzal) (Closed)
---

### Post by dino99 on 2012-09-17
I'm trying to download the latest kernel debs into a dedicated folder i've just created inside my /home, and it refuse to save it there.

[HTML]You don't have permission to write in this location.[/HTML]

but 


[HTML]drwxr-xr-x  2 oem oem 4,0K sept. 17 10:27 kern/[/HTML]

so i'm missing something evident, but what ?

---

### Post by BrianBlaze on 2012-09-17
You need write permissions... unless you sudo it of course... I see normal users onlu have read and execute permissions.... chmod 777 should allow you to do what you wish...

---

### Post by dino99 on 2012-09-17
Seems to be some other reasons, it still refuse.


[HTML]drwsrwsrwx  2 oem oem 4,0K sept. 17 10:27 kern/
[/HTML]

---

### Post by doktorOblivion on 2012-09-17
I am assuming you (oem) are the owner of that directory?  If so, its not the 755 killing you its something else.  If not, you should take ownership of the folder.
```

sudo chown -R <uid>:<gid> kern/

```
Otherwise, I would you suggest you take a look at the process running the browser to make sure your euid/egid line up to have access to that directory.

---

### Post by dino99 on 2012-09-17
Finally found where the problem was (but not fixed): chromium or firefox can download inside that folder (or somewhere else), but midori refuse (appeared with the latest dev upgrade)

---

