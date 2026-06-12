---
title: "Start script by launcher in USP"
date: 2006-08-29
forum: Ubuntu System Panel
---

### Post by mucha on 2006-08-29
I have made a bashscript like this (to make gimp run in english):
```
~$ cat /usr/local/bin/startgimp 
LC_ALL=C gimp
```

If I launch startgimp in a launcher on a gnome-panel it works just fine. But if I launch it in USP nothing happens. Is there a way to fix this?

---

### Post by chanders on 2006-08-29
I dont think I have tried running any scripts from USP but I dont see why it shouldnt..

Try running

usp run-in-window

and clicking on the script and post your output..

---

### Post by dngpng on 2006-08-30
I also have this problem cause I'm running a launcher to start my DC++ client with Alltray. I have run usp in window but there is nothing more in the output when I click on the item.

---

### Post by mucha on 2006-09-07
> **dngpng said:**
> I also have this problem cause I'm running a launcher to start my DC++ client with Alltray. I have run usp in window but there is nothing more in the output when I click on the item.

Same here, is there no solution for this yet?

---

### Post by chanders on 2006-09-07
Try adding the script header in your script file. I think it is used to let gnome know that it is a bash script.

Also make sure your script is executable (right click and set execute in permissions)

---

### Post by mucha on 2006-09-09
Ah it was so easy :)

```
#!/bin/bash
```
in the beginning made the difference

---

