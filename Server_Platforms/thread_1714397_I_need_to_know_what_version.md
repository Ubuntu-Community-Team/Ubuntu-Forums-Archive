---
title: "I need to know what version"
date: 2011-03-25
forum: Server Platforms
---

### Post by _joecrawford on 2011-03-25
I was just handed a CLI only server at work and it hasn't been touched in years. I need to setup an FTP server on it, but I have no idea what version or OS I it is running.  What is a ubiquitous command that I can get that info?  I have root.

---

### Post by falko on 2011-03-25
Take a look at your /etc/apt/sources.list.

---

### Post by ephmanjmm on 2011-03-25
try lsb_release -a

---

### Post by rubylaser on 2011-03-25
This will show you your release.
```
cat /etc/issue
```

This is what the output looks like.
```
root@svr-cc-marketing:~# cat /etc/issue
Ubuntu 10.04.2 LTS \n \l
```

---

### Post by headvampyre@hotmail.co.uk on 2011-03-25
Well its gonna be 10.04(maverick meerkat) then...

---

### Post by rubylaser on 2011-03-25
> Well its gonna be 10.04(maverick meerkat) then...

What do you mean?  I just copied the output of that from one of my server's terminal as an example.  P.S. 10.04 is Lucid Lynx.  10.10 is Maverick Meerkat :)

---

### Post by iissmart on 2011-03-25
```
$ cat /etc/lsb-release
```

You don't need root to find the OS.

---

### Post by _joecrawford on 2011-03-28
Thank you for the help! 

(and it wasn't 10.04 ;) )

---

