---
title: "error executing gpgv; GPG error"
date: 2006-09-10
forum: Repositories &amp; Backports
---

### Post by Floren on 2006-09-10
Hi,

From one day to the next without (apparently) touching any system files I get this problem: When I try to run the Update Manager and click on check I get:


[PHP]W: GPG error: http://us.archive.ubuntu.com dapper Release: Unknown error executing gpgv  
W: GPG error: http://us.archive.ubuntu.com dapper-updates Release: Unknown error executing gpgv  
W: GPG error: http://us.archive.ubuntu.com dapper-backports Release: Unknown error executing gpgv  
W: GPG error: http://archive.canonical.com dapper-commercial Release: Unknown error executing gpgv  
W: GPG error: http://security.ubuntu.com dapper-security Release: Unknown error executing gpgv  [/PHP]

If I try 'sudo apt-get update' from the console, I get the same answer. And I also noticed that all software that I try to install with Synaptic appears as 'Not authenticated'.

I have followed some suggestions that did not work: the date and year are correct. I also tried to run an empty sources.list and then run a clean sources.list and gave me the same problem no matter what I have in my list (except when it's empty).

Any idea what's wrong?

Thanks,
Floren

---

### Post by catlett on 2006-09-10
There is something wrong with your GPG keys for those repositories. Either you have not downloaded and installed the keys or they may have expired.
Search for the gpg key to those repositories. Sometimes you can just hit on the link from your post and the server may have key info. When you get the key you put it into this formula and enter it into the terminal
```
gpg –keyserver subkeys.pgp.net –recv KEY
```
```
gpg –export –armor KEY | sudo apt-key add -
```You replace 'KEY' with the actual numbers of the key.

---

### Post by Floren on 2006-09-11
Thanks a lot for your directions. It turns out that was not the problem either...

When I tried to do what you told me, I got a message saying that a library called /usr/local/lib/libreadline.so.5 was not symbolic link.

I have removed that library (and made a backup) and now everything works perfectly again. The question is... what will stop working without that library? And, why did a library in /usr/local/lib interfered with apt-get and the GPG's?

Thanks again!
    Floren

---

### Post by catlett on 2006-09-11
Sorry to say, I do not really know. I just tried to open /usr/local/lib/libreadline.so.5
 and I do not have that directory. I only have 2 folders in /usr/local/lib. They are a python folder and a win32 folder. Just keep an eye out for any errors and look to the removed library first. Hopefully, there won't be any more.

---

### Post by juriise on 2006-10-25
I had the exact same message, and found that the date on the machine was way off (year 2003 something).

Setting the correct date fixed the problem

---

