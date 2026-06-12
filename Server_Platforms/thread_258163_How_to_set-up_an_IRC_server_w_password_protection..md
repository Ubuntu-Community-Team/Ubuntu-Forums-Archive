---
title: "How to set-up an IRC server w/ password protection."
date: 2006-09-15
forum: Server Platforms
---

### Post by scott_ttocs46 on 2006-09-15
Hi all,
    I am fairly new to linux. I have setup an Ubuntu server and I need to know how to setup an IRC server that is 100% inaccessable without the user providing a password.

    I have gotten a couple of daemons to work ... but it need to be 100% password/key protected.

    Any ideas/suggestions/comments/links?

Thanks,
Scott

---

### Post by scott_ttocs46 on 2006-09-16
Anyone?

---

### Post by lamego on 2006-09-17
Just read your ircd.conf file, you can put a password on the I: line as it should be described on the sample conf.

---

### Post by scott_ttocs46 on 2006-09-17
Thanks for the reply. A global password would be nice. But I need a password for each user so they do not impersonate each other.

Also, no password - no entry. ](*,) 

I am familiar w/ the global password but not individualized passwords.

Any ideas?


Thanks,
Scott

---

### Post by CzarAlex on 2006-09-18
Something like the popular NickServ as seen on some servers? I have not run my own IRC server (I suppose Im a little unfamiliar with security on it and don't wanna blow my box up) but I -assume- if you can find a way to install a NickServ type service, just try to set the default boot time to like 20 seconds or something, if a user doesn't identify themselves accordingly. 

I'm sorry that I'm not much more of a help but my aim was to think out loud and give ya ideas :wink:

---

### Post by scott_ttocs46 on 2006-09-18
Thanks for the input. Found this package:
[http://packages.ubuntulinux.org/dapper/net/hybserv](http://packages.ubuntulinux.org/dapper/net/hybserv)
Gonna try this and see what happens.

---

### Post by honeydew on 2006-10-26
I dont know if this is too secure of a idea. but I would suggest SILC  [http://silc.org](http://silc.org).  It is a very tasty option and offers the capability to have password protected servers, and even allows for configuration of a key database.. and only peoples keys that you authorize, can connect.  If you are interested I could probally come up with a quick howto for ubuntu

---

### Post by scott_ttocs46 on 2006-11-18
You mean [http://silcnet.org/](http://silcnet.org/)  ?

---

### Post by honeydew on 2006-12-21
yep thats the one.. it works great.  Me and a few buds use it on a regular basis.  I dont think it has a extreme amount of dependencies either.  like ncurses and maybe build-essential.

---

