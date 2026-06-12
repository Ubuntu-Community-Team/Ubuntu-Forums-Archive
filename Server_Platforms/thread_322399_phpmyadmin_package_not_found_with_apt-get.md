---
title: "phpmyadmin package not found with apt-get ?"
date: 2006-12-20
forum: Server Platforms
---

### Post by chucklarge on 2006-12-20
Anyone know why i can't install phpmyadmin?  

chuck

>sudo apt-get install phpmyadmin
>Reading package lists... DoneBuilding dependency tree       
>Reading state information... DoneE: 
>Couldn't find package phpmyadmin

---

### Post by az on 2006-12-20
You need to enable the universe repository.

[https://help.ubuntu.com/community/Repositories](https://help.ubuntu.com/community/Repositories)

---

### Post by gregor171 on 2007-01-03
Hi
Don't bother with that, just download it from web, unzip or un-tar and put it to yout www folder and it should work... (you need to have php + php-mysql lib installed)

---

### Post by Brazen on 2007-01-03
yeah, really all you do is download and untar the phpmyadmin file from their website, change a few lines in the config file and that's it.

I would prefer installing it myself anyway because then I can put the files where I want and then alias it into Apache.

---

