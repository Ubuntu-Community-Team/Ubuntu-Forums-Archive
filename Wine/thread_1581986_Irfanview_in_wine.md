---
title: "Irfanview in wine"
date: 2010-09-25
forum: Wine
---

### Post by jcolyn on 2010-09-25
After installing and configuring wine  and after changing to the download folder where I downloaded iview427_setup.exe I tried to install Irfanview4 ```
wine iview427_setup.exe
``` but it won't install. Thinking it may be a wine issue I tried the same with Opera which installed without a hitch.

I did install the missing mfc42.dll into the system32 folder that is needed to run iview

Irfanview looks to be compatible based on the winehq website.

Am I doing something wrong here??

---

### Post by mrhhug on 2010-09-25
wait you installed opera with wine? opera has ubuntu specific version....

can you post some of the error messages your getting from wine?

---

### Post by jcolyn on 2010-09-25
> **mrhhug said:**
> wait you installed opera with wine? opera has ubuntu specific version....

I did it as a test to see if I was doing something wrong.

> **mrhhug said:**
> can you post some of the error messages your getting from wine?

No error messages.

After typing ```
wine iview427_setup.exe
``` nothing happened except it went back to the prompt.

---

### Post by mrhhug on 2010-09-25
nothing!? wine is usually nice and verbose

what are you permissions like on iview427_setup.exe?

try executing it with absolute file referencing like :
wine /home/michael/Desktop/iview427_setup.exe

also please post your : wine --version

---

### Post by jcolyn on 2010-09-25
> **mrhhug said:**
> nothing!? wine is usually nice and verbose

what are you permissions like on iview427_setup.exe?

try executing it with absolute file referencing like :
wine /home/michael/Desktop/iview427_setup.exe

also please post your : wine --version


The file is executable.

wine /home/colyn/iview427_setup.exe does nothing.

Version is 1.2

I may delete the file and try downloading it from another source to see if it is a bad download..

---

### Post by mrhhug on 2010-09-25
good call on the redownload

also winecfg lets you change the version of windows it fools the program into thinking your running, since your redownloading anyway, try and get a windows XP version, they are usually better tested and supported (and then change to xp in winecfg)

---

### Post by jcolyn on 2010-09-26
It seens wine was in fact the problem. I decided to uninstall wine then reinstall it. Once done iview installed like it should..

---

