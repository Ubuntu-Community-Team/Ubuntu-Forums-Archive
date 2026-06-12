---
title: "Rolling your own cloud"
date: 2009-10-02
forum: Ubuntu One (CLOSED)
---

### Post by dasunst3r on 2009-10-02
I am liking the level of integration I am seeing on Ubuntu One, but I prefer to store the files on my own web hosting service.  Is there any way for me to do that?

---

### Post by dhysk on 2009-10-06
I would also like to do something like this, however using a home server that I could connect to while I'm traveling.

---

### Post by lukeiamyourfather on 2009-10-06
I'm not sure if Ubuntu One will allow you to store files elsewhere, but you can do it on your own. Mount a folder on your system from an FTP server or other protocols. There are several file systems based on FUSE that can treat your Gmail and other accounts as local file systems. Cheers!

---

### Post by tigergibb on 2009-10-06
[http://code.google.com/p/lsyncd/](http://code.google.com/p/lsyncd/)

Lsyncd uses rsync to synchronize local directories with a remote machine running rsyncd. Lsyncd watches multiple directories trees through inotify. The first step after adding the watches is to rsync all directories with the remote host, and then sync single file by collecting the inotify events. So lsyncd is a light-weight live mirror solution that should be easy to install and use while blending well with your system. See lsyncd --help for detailed command line options.

---

### Post by scorp123 on 2009-10-06
> **tigergibb said:**
> [http://code.google.com/p/lsyncd/](http://code.google.com/p/lsyncd/)  Nice stuff. Thanks for this.

BTW, does anyone know any good iFolder replacements? I have settled on Dropbox for now but I'd definitely prefer if I had the server part under my own control ....

---

### Post by osomphane on 2009-10-07
teamdrive?

---

### Post by scorp123 on 2009-10-08
> **osomphane said:**
> teamdrive? " ... You decide if you want to use your own server or if you want to use our hosting services! ... "

Interesting. Thanks for this!

---

### Post by kenshen on 2009-10-18
Free nas server [http://www.freenas.org/](http://www.freenas.org/)

---

### Post by sanjaya on 2010-04-01
Join the following group and check out the scripts to build iFolder client and Simias server. It is working on 9.04 Ubuntu server and client on Ubuntu 9.10

I am looking for testers, post your reports to this group.

[http://groups.google.com/group/ifolder-ubuntu-debian-dev](http://groups.google.com/group/ifolder-ubuntu-debian-dev)

---

### Post by taranfx on 2010-04-02
I wish it had GlideOS integration. They offer good free space.

---

### Post by Martje_001 on 2010-04-03
Would it be legal to reverse engineer the server software and publish it as FOSS?

---

### Post by joshuahoover on 2010-04-05
> **Martje_001 said:**
> Would it be legal to reverse engineer the server software and publish it as FOSS?

It is possible to create a FOSS server compatible with Ubuntu One. You would do this by looking at our ubuntuone-storage-protocol code on Launchpad: [https://launchpad.net/ubuntuone-storage-protocol](https://launchpad.net/ubuntuone-storage-protocol) If you're interested in doing this, please let me know and I'll see how we can assist you.

Thank you,

Joshua

---

