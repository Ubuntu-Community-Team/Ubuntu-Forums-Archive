---
title: "files aren't recognized"
date: 2009-01-17
forum: Server Platforms
---

### Post by davidweaverking on 2009-01-17
I'm new to Ubuntu (previously on Darwin) and I'm trying to set up a web server with Coldfusion 8.  The install went fine but now bash won't recognize the file.

```

root@JMS:/opt/coldfusion8/runtime/bin# ls -lah
total 2.5M
drwxrwxr-x 2 runtime root 4.0K Jan 17 15:55 .
drwxrwxr-x 7 runtime root 4.0K Jan 17 15:30 ..
-rwxr-xr-x 1 runtime root  52K Jan 17 15:30 coldfusion8
-rwxrwxr-x 1 runtime root  52K Mar 18  2008 java2wsdl
-rwxr-xr-x 1 runtime root 2.0M Jan 19  2008 jikes
-rwxrwxr-x 1 runtime root  52K Mar 18  2008 jrun
-rwxrwxr-x 1 runtime root  52K Mar 18  2008 jspc
-rwxrwxr-x 1 runtime root 1.7K Jan 17 15:30 jvm.config
-rwxrwxr-x 1 runtime root  52K Mar 18  2008 migrate
-rwxrwxr-x 1 runtime root  52K Mar 18  2008 sniffer
-rwxrwxr-x 1 runtime root  52K Mar 18  2008 wsconfig
-rwxrwxr-x 1 runtime root  990 Jan 17 15:30 wsconfig_jvm.config
-rwxrwxr-x 1 runtime root  52K Mar 18  2008 wsdl2java
-rwxrwxr-x 1 runtime root  52K Mar 18  2008 xmlscript
root@JMS:/opt/coldfusion8/runtime/bin# ./coldfusion8 
-bash: ./coldfusion8: No such file or directory

```

ls shows the file but bash can't run it!  All the files in this directory do the same thing but every other directory on the box works fine.  HELP!

---

### Post by cariboo on 2009-01-17
never mind

---

### Post by Iowan on 2009-01-19
Try this:```
ls -al coldfusion8
``` It *should* list only that file.  If it doesn't, there may be something in the name.

---

### Post by davidweaverking on 2009-01-20
```

root@JMS:/opt/coldfusion8/runtime/bin# ls -al coldfusion8 
-rwxr-xr-x 1 root root 52760 Jan 20 13:58 coldfusion8

```

Looks just as I should expect.  One other thing I just discovered.  Every binary file in /opt/coldfusion8/ acts exactly the same way.  Shell scripts work fine (other than not being able to run any binary).  I think (best guess here) they're all just java launchers but that shouldn't make any difference since it never even gets into the execution of the file.

---

### Post by davidweaverking on 2009-01-20
So it turns out I just didn't check for the right architecture.  I downloaded a 64bit version and it works perfectly.  Couldn't they find a more descriptive error message than "No such file or directory" for that situation?

---

### Post by mistypotato on 2009-02-15
Where can you "download" Coldfusion ?

You must mean a trial version ?

---

