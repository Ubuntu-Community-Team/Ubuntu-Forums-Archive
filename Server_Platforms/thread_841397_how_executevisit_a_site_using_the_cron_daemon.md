---
title: "how execute/visit a site using the cron daemon?"
date: 2008-06-26
forum: Server Platforms
---

### Post by jasonx22 on 2008-06-26
hi,
i need to execute/visit a site to check if the site is up or not i have a server that have cron shedule that can execute a php file now how can i execute/visite a site using the same way as i execute a file?
thanks a lot for your help

---

### Post by slakkie on 2008-06-26
you might want to have a look at wget:

wget -O file.html [http://a.host.net/index.php](http://a.host.net/index.php)

This will put the contents of index.php in file.html.

man wget.

---

### Post by jasonx22 on 2008-06-26
hi and if i only want visit the site without saving i just want that cron visit the link just that
thanks

---

### Post by cdenley on 2008-06-26
> **jasonx22 said:**
> hi and if i only want visit the site without saving i just want that cron visit the link just that
thanks

```

#!/bin/sh
wget -O /dev/null -q $1
if [ $? -eq 0 ]
then
  echo online
else
  echo offline
fi

```
You can replace $1 with whatever url you want.

---

### Post by slakkie on 2008-06-28
> **cdenley said:**
> ```

#!/bin/sh
wget -O /dev/null -q $1
if [ $? -eq 0 ]
then
  echo online
else
  echo offline
fi

```
You can replace $1 with whatever url you want.


Better yet, if he saves this piece of code into file.sh and adds the executable flag (chmod +x) he could then use it ala: ./file.sh url for different sites without having to recreate the script.

---

