---
title: "Create secure shell environment for users."
date: 2010-02-25
forum: Server Platforms
---

### Post by MontelEdwards on 2010-02-25
Hello,
I was planning on using my VPS to grant some of my friends shells. The problem though is that I don't want them doing crazy stuff on it, like using up all my RAM or disk space. I would like to limit them to a very small 25 mb disk space, and allow them only certain application in /usr/bin like python perl irssi screen etc. I do NOT want them to be able to cd out of their home directory. I really want this to be setup like the shell provider SHellium. I can setup the FTP and SSH stuff myself.

Thank you,
Montel

---

### Post by joberly on 2010-02-25
As far as quotas go, you can use the quota and quotatool packages to manage that. Click [here]("http://www.debian-administration.org/articles/47") for a guide (it's old, but other guides I've seen follow the same idea).

---

### Post by noway2 on 2010-02-25
It sounds like you may also want to chroot them to their home folder. This way their home folder IS the root of their file system.  I am not sure if this has implications regarding accessing system programs or not, but I am sure there is a way to do this.

---

### Post by bodhi.zazen on 2010-03-01
Sorry for the delayed response ....

This may be difficult for you to do as it depends on what you mean by VPS. If you are running the host , just give them their own VPS =)

With most VPS you will not be able to use tools such as apparmor or selinux.

You could look at rbash , but be warned, it is not difficult to break out of rbash. 

Another option would be Iron Bars :

[http://ibsh.sourceforge.net/](http://ibsh.sourceforge.net/)

+1 for using quota =)

---

