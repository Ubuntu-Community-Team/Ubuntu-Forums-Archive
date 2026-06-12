---
title: "gpg shell .deb?"
date: 2012-05-14
forum: Security
---

### Post by ottosykora on 2012-05-14
Does someone know if there is somewhere a binary .deb for 64bit of this gpg front end?


Or if not , can someone help with building it, as it seems somehow complicated for me.


[http://www.tech-faq.com/gnupg-shell.html](http://www.tech-faq.com/gnupg-shell.html)

---

### Post by DanR01 on 2012-05-14
If it is a .deb package you should be able to install it through the software centre or using GDebi.

It looks like you may need to unpack the file first.

```
 gunzip gnupgshell-1.0.0.i386.deb.gz 
```As an aside, no sig file or MD5 seems to be provided to verify the integrity of the package.

Edit: just noticed you want it for 64 bit linux and the package is for 32 bit. Sorry.

---

### Post by DanR01 on 2012-05-14
The process should be the same as outlined here:
[HTML]https://help.ubuntu.com/community/CompilingEasyHowTo[/HTML]

Move the tar to a directory where you can read/write to. 

```
gunzip gnupgshell-1.0.0.tar.gz
```

```
tar xvf gnupgshell-1.0.0.tar
```

```
cd gnupgshell/bin
```

```
./wxGnuPGShell 
```

Let me know if you have any problems. I got it working OK on my system.

---

### Post by ottosykora on 2012-05-14
thanks, I tried , but do not manage as I am not so much good in such things.

I have the build-essintials installed, but this seeems to be little complex for me.

Anyway, when I come to make, nothing happends.

 I was just able to untar the contenets, but the rest ??

Can for that I would either need exact command all together or the compiled thing working.

The compilation is problem, as make , makeinstall or anything like this does not do anything so far, I have no idea in which directory to start exactly.

---

### Post by DanR01 on 2012-05-15
You don't need to run make or make install 

If you cd into the directory gnupgshell/bin you will be able to run it with the final command.

If you type ls whilst in gnupgshell/bin you should see wxGnuPGShell written in green.

This is an executable.

Follow the commands in my second post and it should work.

---

### Post by ottosykora on 2012-05-16
well, but for that I have to compile it first as in the normal targz file this directory is empty, in contains an other directory called art with number of icons files.

I have no binary, so I have to make it first and there I am little bit stuck.


Or otherwise can you tell me where did you get the archive congaing the executable from?

---

