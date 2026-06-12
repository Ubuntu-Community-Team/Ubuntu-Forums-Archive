---
title: "cant extract to root folders"
date: 2010-02-25
forum: Security
---

### Post by XXMy_Little_ShinigamiXX on 2010-02-25
hi im not sure if this is where i post this or not but i was wondering im trying to extract a skin into the amsn skin directory and it says im not allowed so i went into the users and groups and i set my self up to be able to do all the commands and put myself in the root catagory of users.  this is where im lost im still unable to do anything.. i want complete administrator access on my OS i shouldnt have to type in sudo - every time i go to install something lol. please help 
thanks

---

### Post by mikewhatever on 2010-02-26
All those user changes were unnecessary. Use <gksudo nautilus> for write access in /. As for installing software, you should be asked for the password, and everything else is point and click.

[http://psychocats.net/ubuntu/installingsoftware](http://psychocats.net/ubuntu/installingsoftware)

---

### Post by XXMy_Little_ShinigamiXX on 2010-02-26
> **mikewhatever said:**
> All those user changes were unnecessary. Use <gksudo nautilus> for write access in /. As for installing software, you should be asked for the password, and everything else is point and click.

[http://psychocats.net/ubuntu/installingsoftware](http://psychocats.net/ubuntu/installingsoftware)

ok so i typed in the terminal command 
gksudo nautilus file:///usr/share/amsn/skins 
now i do have write access but nothing from outside can come in i can only create new files and such inside the folder. after figuring this i also did;
gksudo nautilus home/michael/downloads and still nothing. 
now im sure you understand my logic behind that so im not going to explain that part lol.
what im trying to do is extract a skin into that folder. it still says i do not have write access..so after i got that basic access i went in and changed the folders to belonging to me and then i could do what i wanted.. i even tried to copy them while i was in the terminal it didnt work.. :popcorn: but overall problem solved and i learned another useful command .. thank you :)

---

### Post by mikewhatever on 2010-02-28
Generally, routinely changing ownerships of folders in / is a bad idea, unless you know what you are doing. I'd simply extract it to the desktop and then copy to the desired location.

---

### Post by cariboo on 2010-02-28
Wouldn't just be easier to run file-roller as root and extract the files to what ever directory you want?

This command should do it. Press Alt-F2 and type:

```
gksu file-roller
```

---

