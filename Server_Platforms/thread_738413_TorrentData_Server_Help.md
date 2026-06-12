---
title: "Torrent/Data Server Help"
date: 2008-03-28
forum: Server Platforms
---

### Post by damonjablons on 2008-03-28
Hey,

I'm fairly new to the Ubuntu game, but I decided to dive head first into it.  I've installed the desktop edition on my laptop, and the headless server edition on an old Dell I had laying around.

I was able to install the server fine, with Samba, OpenSSH, and LAMP.  But I want to configure a torrent program to work so that people on my network can use it as a torrent server, and we can store our media files on it.

Currently it has rTorrent installed on it which is command line based, and probably a bit too difficult for the other network members to use.  I chose not to use TorrentFlux because it seems like encryption and other options don't work too well.

**How can I configure rTorrent to have some sort of web interface, or desktop client interface for remote computers on the network?  I understand it can be set up to rescan a folder for new torrents on a timer, and I can NFS/Samba the folder.  How do I make it so that less linux savvy users can view torrent progress?**

Thanks in advance,
D

---

### Post by netlogic on 2008-03-28
There are various recommended interfaces at their site.

[http://libtorrent.rakshasa.no/wiki/UtilsList](http://libtorrent.rakshasa.no/wiki/UtilsList)

---

### Post by damonjablons on 2008-03-29
I'm trying to install wTorrent as you prescribed, but when i get this error when trying to compile.  Can anyone tell me what's going on?  Maybe I need to install C compiling dependencies?  Any help?

```

damon@ringo:~/rtorrent-svn/trunk/libtorrent$ ./autogen.sh
aclocal...
aclocal not found

```

---

### Post by damonjablons on 2008-03-29
> **damonjablons said:**
> I'm trying to install wTorrent as you prescribed, but when i get this error when trying to compile.  Can anyone tell me what's going on?  Maybe I need to install C compiling dependencies?  Any help?

```

damon@ringo:~/rtorrent-svn/trunk/libtorrent$ ./autogen.sh
aclocal...
aclocal not found

```

Alright, I got past this, but now rtorrent won't compile, i get this error:

```

checking if compiler supports __attribute__((visibility("default")))... yes
./configure: line 22683: syntax error near unexpected token `OPENSSL,'
./configure: line 22683: `      PKG_CHECK_MODULES(OPENSSL, openssl,'

```

I tried commenting out the if statement, but that didn't work.  Anyone?

---

### Post by damonjablons on 2008-03-29
Alright!

I got it working with the latest version of rTorrent, even though it's recommended against.  Anyone having trouble with this should check out this tutorial:

[http://flipsidereality.com/blog/linux/rtorrent-with-wtorrent-on-debian-etch-complete-howto/](http://flipsidereality.com/blog/linux/rtorrent-with-wtorrent-on-debian-etch-complete-howto/)

**Some Tips**:
1. Copying and pasting the apt-get commands for dependencies will not work, retype it yourself.  Some of the apache stuff isn't in the repos anymore, and the whole command will fail.  There's probably a force option to get around this, but I don't know how that works.

2. Don't use 

```
svn up -r 1038
```

just use the regular

```
svn up
```

good luck!

---

