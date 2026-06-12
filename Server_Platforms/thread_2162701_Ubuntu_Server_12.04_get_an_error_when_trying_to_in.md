---
title: "Ubuntu Server 12.04 get an error when trying to install phpPgAdmin"
date: 2013-07-15
forum: Server Platforms
---

### Post by Codin2013 on 2013-07-15
I am using Ubuntu 12.04 as my server and I have apache2 installed and php and postgresql installed also. Whenever I try to install phppgadmin from terminal with the command sudo apt-get install phppgadmin I get an error. Errors were encountered while processing: phppgadmin E: Sub-process /usr/bin/dpkg returned an error code (1). I do not know what to do I would really like to get this installed all help greatly appreciated.

---

### Post by SeijiSensei on 2013-07-16
Start by trying 

```

sudo apt-get update
sudo dpkg --configure -a
sudo apt-get install -f 

```

Usually there is more to the error than you posted.  If after this you still cannot install phppgadmin, post the entire error message inside of [noparse]```

```[/noparse] tags.

---

