---
title: "Auto chmod file to 0755"
date: 2009-02-20
forum: Security
---

### Post by neomaximus2k on 2009-02-20
hey guys, quick question I code several sites on my acer aspire one notebook running ubuntu (Also have an ubuntu server with the same problem), basicly I wasnt to auto set file permissions on every .php file and directory within the /var/www directory to 0755, by default they chmod to some weird number and naturally generate a "Permission Denied" error message which means I have to go into terminal and chmod which I dont want to do all the time as it gives me a major headache especially when doing advanced coding.

Can anyone suggest a method of doing this? 

Thanks in advanced

---

### Post by bodhi.zazen on 2009-02-20
When working with these files, set umask to 022, which should be the default

```
umask 022
```

Or you can set your umask in .bashrc if you want to change your "default" behavior.

---

