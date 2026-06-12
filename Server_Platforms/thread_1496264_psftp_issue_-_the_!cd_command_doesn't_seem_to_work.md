---
title: "psftp issue - the !cd command doesn't seem to work"
date: 2010-05-29
forum: Server Platforms
---

### Post by Ishimaru Chiaki on 2010-05-29
Hello everyone !

Lately, someone lent me a server that runs under Ubuntu 10.04, so I can do online testing on my LAMP, and access my Web pages documents even if I'm away from home.

So I began to configure it.  LAMP is now installed and works fine.

Since I connect with PuTTy, I so use a .ppk keyfile the guy who lent me the server sent me.  Tonight, I have just learnt about the existence of **pscp** and **psftp** who also use the .ppk format.

But right now, I encountered a problem with psftp : the !cd command I want to use to change directory on the local side doesn't seem to work.

Here's an sample that comes from my console :
```
psftp> !pwd
/usr/share/man
psftp> !cd /home/caroline/web
psftp> !pwd
/usr/share/man
psftp> !cd ../..
psftp> !pwd
/usr/share/man
psftp> pwd
Remote directory is /var/www/htdocs
psftp> !cd ..
psftp> !pwd
/usr/share/man
psftp> cd ..
Remote directory is now /var/www
psftp> cd htdocs
Remote directory is now /var/www/htdocs
psftp> !cd ..
psftp> !pwd
/usr/share/man
psftp> pwd
Remote directory is /var/www/htdocs
psftp> !pwd
/usr/share/man

```

As you can see, whatever I do, the !cd doesn't work, I stay in the same directory locally, while cd (without the !) works fine.

So this is quite embarrassing since I have to type a long path if I want to send a file or a directory to my server.

For your information, my local computer runs under Ubuntu 9.04.  I would like to know if this happens only on this version and doesn't happen on Ubuntu Lucid.

I found only one search result mentioning this issue (mofeel.net), but the link doesn't work properly, the whole website's content is archived and is a pain to navigate - I had to disable style, but the topic titles don't facilitate my researches.

If you need more info, ask me.

Thanks in advance.

Ishimaru

---

### Post by Ishimaru Chiaki on 2010-05-30
Bump !

The problem is the same when I test with Ubuntu Lucid's LiveCD !

```
Remote working directory is /root
psftp> !pwd
/home/ubuntu
psftp> !ls
Desktop  Documents  Images  Modèles  Musique  Public  Téléchargements  Vidéos
psftp> !cd Images
psftp> !ls
Desktop  Documents  Images  Modèles  Musique  Public  Téléchargements  Vidéos
psftp> !cd Documents
psftp> ls
Listing directory /root
drwx------    4 root     root         4096 May 26 18:30 .
drwxr-xr-x   22 root     root         4096 May 27 05:38 ..
-rw-------    1 root     root          886 May 29 23:10 .bash_history
-rw-r--r--    1 root     root         3106 Mar 25 14:26 .bashrc
drwxr-xr-x    2 root     root         4096 May 26 18:30 .cache
-r--------    1 root     root            9 May 26 10:56 .p
-rw-r--r--    1 root     root          140 Nov 19  2007 .profile
drwxr-xr-x    2 root     root         4096 Apr 22 11:12 .ssh
psftp> cd /var/www
Remote directory is now /var/www
psftp> pwd
Remote directory is /var/www
psftp> cd htdocs
Remote directory is now /var/www/htdocs
psftp> pwd
Remote directory is /var/www/htdocs
psftp> !pwd
/home/ubuntu
psftp> !cd ..
psftp> !pwd
/home/ubuntu
psftp> 

```

---

