---
title: "Edgey Eft and php"
date: 2007-04-08
forum: Server Platforms
---

### Post by ravalox on 2007-04-08
I'm trying to install Joomla on an Edgey Eft installation; and after following these simple instructions: [https://help.ubuntu.com/community/Joomla](https://help.ubuntu.com/community/Joomla), when going to localhost/joomla I get a phtml file sent to me as if it were just any other file.  I suspect this means I don't have php configured properly for apache but I have no means of really determining how to diagnose that; I tried this: 
```
sudo apt-get remove --purge php5-common 
sudo apt-get install php
```

And it hasn't changed a thing.

---

### Post by Pyro_Killer on 2007-04-09
with saying 

sudo install php

You don't even point to the program. try the ordinary method:

sudo -i
*/configure
make 
make install

---

### Post by ravalox on 2007-04-09
Are you saying I should build apache from source?

---

