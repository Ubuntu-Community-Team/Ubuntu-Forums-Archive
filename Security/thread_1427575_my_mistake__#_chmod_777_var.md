---
title: "my mistake : # chmod 777 /var"
date: 2010-03-11
forum: Security
---

### Post by cx1max on 2010-03-11
hello

i did a big mistake today on my personal desktop...
i send this : chmod -R 777 /var _with root_ prompt instead of ./var on a website files tree...

the question : is there any way to 'rollback' this? or the better thing to do is to re-install the system?
reinstalling is not really a problem (/home is on a separate partition), i just want to save time and to know where to find appropriate guides to repair things like that in case of...

thank you a lot for your help

---

### Post by gnupipe on 2010-03-11
```
sudo chmod 755 /var 
```?

---

### Post by cx1max on 2010-03-11
sorry?

Oops : here is what i did : 

```

root prompt# chmod -R 777 /var

```

with root (sudo su) and the -R switch
thats why there is a problem with the /var dir now

---

