---
title: "Off apt-get issue"
date: 2010-07-07
forum: Server Platforms
---

### Post by guessswh0 on 2010-07-07
I have the server attempting to update its repositories and install applications through apt-get.  It currently connects through a proxy which requires a username and password.

I edited the /etc/bash.bashrc file to allow it to connect through the proxy.  However, I've noticed something odd.  I have to switch over as root in order to run apt-get update/upgrade/install, etc..  If I don't switch to root, it will not connect to the proxy, but try to connect directly to the repository.

So I have to be root and run apt-get update

I cannot do a "sudo apt-get update"

Using sudo, even while logged in as root, causes the apt-get to go directly to the repo vs. through the proxy.

Any ideas?

---

### Post by arrrghhh on 2010-07-07
[This](http://ubuntuforums.org/showpost.php?p=1262323&postcount=7) post may be a solution for you.  Not sure tho, exporting to your .bashrc should've done it.  Did you export it to all the .bashrc's?  Perhaps you only did root's...

---

