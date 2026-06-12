---
title: "backup and upgrade"
date: 2007-11-07
forum: Server Platforms
---

### Post by gorbunok on 2007-11-07
I have 2 quick questions

1. I have a vps hosted  server  that is built with 6.06 version. I there is a bug in the lighttpd that is shipped with 6.06 but I do have a work around so it is not critical. Do you recommend to upgrade to 7.10 server? I know it will solve my lighttpd problem but are there any other real benefits. (P.S. my vps is quite wimpy so i am running server minimal distro. I don't want to blaot up server with upgrade if possible)

2. Can someone recommend away to take an image from a server in case there some kind of disk failure. i am not talking about backing data files but somehow to be able to restore entire server as is. In case my vps disk goes or I mess something up in config :) i would like to be able to recover. instead of rebuilding and configuring the server again from scratch.

Thanks for your help!

---

### Post by bmathis on 2007-11-07
There is no need to upgrade if your system works fine, plus you have LTS with 6.06. If you have issues with lighttpd, you can try to removing what you have and install from source. You can also try to file a bug and see if the dev team will update the package for Dapper.

Here is a pretty good howto for backing up and restoring your box. [http://ubuntuforums.org/showthread.php?t=35087]("http://ubuntuforums.org/showthread.php?t=35087")

---

### Post by gorbunok on 2007-11-07
The back up guide is exactly what I was looking for. Thanks.

About the bug in lighhtpd. I tried d/l the deb package by it self but it needed a bunch of newer libraries as well so I would have to resolve all the dependencies manually  and that would be very painful.  is there a way to do this automatically?

---

### Post by bmathis on 2007-11-08
Have you tried to do a "sudo aptitude install *dependencies*" and then installing the deb? This is what I usually do.

---

