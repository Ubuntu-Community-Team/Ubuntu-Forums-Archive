---
title: "wmv"
date: 2006-02-24
forum: The Cafe
---

### Post by dosed150 on 2006-02-24
is there a way i can play wmv files on ubuntu?

---

### Post by BWF89 on 2006-02-24
Codecs my friend, codecs.

[http://www.google.com/search?q=Play+WMV+on+Linux&start=0&ie=utf-8&oe=utf-8&client=firefox-a&rls=org.mozilla:en-US:official](http://www.google.com/search?q=Play+WMV+on+Linux&start=0&ie=utf-8&oe=utf-8&client=firefox-a&rls=org.mozilla:en-US:official)

---

### Post by dosed150 on 2006-02-24
well that was helpful ok i downloaded the codecs but i cant put them in the codecs folder it says im not the owner

---

### Post by GreyFox503 on 2006-02-24
If you are trying to move or copy files somewhere where you don't have permission, then you need root privileges.  To do this, just prefix the command you want with 'sudo', like so:
```

sudo cp file1.gz /somewhere/else
```

As soon as you hit enter, you will be prompted for a password.  Enter your normal user password that you login with, then hit enter again.  The command will be run with root privileges.

Be careful with sudo, because it will let you do anything root can do, delete any file, etc.

---

### Post by dosed150 on 2006-02-24
so if wanted to copy a whole folder id just put the name of the folder in there

---

### Post by majikstreet on 2006-02-24
kind of. 
sudo cp -R folder /somewhere/else

that's what you would do for a whole folder.

---

### Post by GreyFox503 on 2006-02-24
For more help with commands like cp, use:

```
cp --help
``` 
```
man cp
``` 

These two will work for most commands.  Of course there's always google.

---

