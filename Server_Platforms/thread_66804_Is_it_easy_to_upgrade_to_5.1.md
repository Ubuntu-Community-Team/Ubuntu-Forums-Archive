---
title: "Is it easy to upgrade to 5.1?"
date: 2005-09-18
forum: Server Platforms
---

### Post by jlist on 2005-09-18
Hi experts,

If I want to install a new server box, should I use 5.04 or 5.1 preview? I understand that 5.1 is coming out soon (in October.) I should be able to upgrade from either 5.04 and 5.1 preview, am I right? Once I upgrade to 5.1, is there any difference if I upgrade from 5.04 or 5.1 preview?

I have never updated/upgraded a linux box before. I suppose apt-get is the command I should use to upgrade all the installed modules (and will not install the modules that's not needed in the server isntall)? Would it be a single command, something like "apt-get upgrade" ?

BTW, is there a way to list all the installed modules with apt-get? I'd like to know if PHP is installed by default in the server installation. I did a "apt-get -h" and didn't see a list option.

Thanks

---

### Post by Finchwizard on 2005-09-18
Isn't it 'apt-get dist-upgrade' or something like that??

I'm sure you would be able to upgrade fine.

---

### Post by John.Michael.Kane on 2005-09-18
Use 5.04 for now. you can always apt-get the latest stable version when released,,
if more infois neededlook in to the links in my sig. and [http://www.tuxfiles.org/](http://www.tuxfiles.org/)

Welcome to gnu/linux/Ubuntu...

---

### Post by jlist on 2005-09-19
Thanks for the replies!  I think "apt-get dist-upgrade" is the command I was looking for.

---

