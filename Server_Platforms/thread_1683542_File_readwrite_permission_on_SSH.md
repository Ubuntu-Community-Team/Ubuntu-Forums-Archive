---
title: "File read/write permission on SSH"
date: 2011-02-07
forum: Server Platforms
---

### Post by likeawalrus55 on 2011-02-07
Hi All,

I am currently running a samba server to allow a large group of people to have read/write access to a backed-up intranet-only server.  Most of the clients will be Windows users, but some will be Linux or Mac users.  I have samba set to only allow access to each user's home directory.

But my problem is I also have to allow ssh and sftp access to the server.  When the client connects via sftp, they are able to view all other client's private directories.  If I change the read/write permissions to the home directory in any way which limits access to the owner, samba can no longer serve the folder.

So what I am hoping for:  a way to prevent all (but root & privileged) users who sftp or ssh in, from seeing outside their respective home directories.  I have been reading about using a chroot jail, but have not yet found an appropriate setup which would do what I am looking for.  I am fairly new to the whole server side of linux, but have been using desktop linux for 8+ years.  Any help is appreciated!

---

### Post by arrrghhh on 2011-02-07
I'm no expert on this topic, but I believe what you are describing is a [Chroot Jail](https://help.ubuntu.com/community/BasicChroot) - that's the basic doc on it, Google the term if you want more in-depth explanations.

---

### Post by wormyblackburny on 2011-02-08
This is a good tutorial:[URL="http://www.howtoforge.net/chrooted-ssh-sftp-tutorial-debian-lenny"]
http://www.howtoforge.net/chrooted-ssh-sftp-tutorial-debian-lenny[/URL]

You will probably need to tweak a little bit of it, but seems pretty straightforward. If it is just a fileserver then you can disregard all of the stuff about adding /bin/bash commands to the chroot jail

---

