---
title: "Server refuses to execute a file"
date: 2010-02-28
forum: Server Platforms
---

### Post by rbb138 on 2010-02-28
[IMG]http://img714.imageshack.us/img714/6343/errorh.jpg[/IMG]

Hello,

Earlier today i started setting up my 3rd ubuntu server under the OS of Ubuntu Linux 9.04 64 bit. I have configured the server to allow root access and am using this to execute this file. As you can see from the screenshot of PuTTy, the file exists but is refusing to load up. I am also able to nano the file. I have tried moving the file to /root/ and still had no luck.

Since i couldnt find any solved threads on this issue i thought i would open a thread for it with proof of the issue.

Hoping for help!

---

### Post by Bachstelze on 2010-02-28
Try

```
file logservice
```

and paste the output. It's probably a 32 bit executable.

---

### Post by rbb138 on 2010-03-01
yes it is now saying its a 32 bit exe when i run that command.

However when i ran exactly the same file on my other 2 servers (which are both 64 bit) it seemed to work fine.

Is there any way to allow for 32 bit executables on a 64 bit machine?

edit:
managed to install lib32 directory and the process is now executing fine.

Thanks for the help.

1 suggestion: instead of it saying it cannot be found the error message should be changed to something along the lines of: "cannot execute 32bit file, run 'apt-get install ia32-libs' to allow support for this file"

---

### Post by noway2 on 2010-03-01
I had the same problem with a small program I wrote.  I created and compiled it on a 32 bit system and then copied it to a 64 bit system.  The 64 bit system wouldn't even appear to locate the executable. My solution was to recompile the source code on the 64 bit system.

---

