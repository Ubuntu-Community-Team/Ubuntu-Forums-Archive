---
title: "how to close user into /home/user?"
date: 2008-01-09
forum: Server Platforms
---

### Post by danifodor on 2008-01-09
Hi,

I have an ubuntu server (7.10) and would like to provide (ssh and sftp) access to some of my friends but want to avoid that they can browse the content of my files. I would like to make a "guest" user that is closed in the /home/guest directory, that is, those, who log in see only this directory.

Is it to make with chroot? Could anyone provide me a step-by-step documentation? 

Thank you

Daniel

---

### Post by frafu on 2008-01-09
Hello,

As the Accessibility forum is intended to discuss software related to disabilities, I am moving this thread to a more appropriate forum. 

Have a nice day. 

Francesco

---

### Post by k_grdn on 2008-01-09
Hi,

This may be what you need:

[http://wiki.linuxquestions.orrdg/wiki/OpenSSH_chrooting](http://wiki.linuxquestions.orrdg/wiki/OpenSSH_chrooting)

Used the same patch a few years back, worked well, may be worth checking out jailkit too.

Regards,

k_grdn

---

### Post by danifodor on 2008-01-10
Thanks for your answer!

What is the difference between this patch and "chroot" command?

Cheers

Daniel

---

### Post by k_grdn on 2008-01-10
Hi,

Chroot is for the running process and its children, if you wish to be able to confine users to a root using ssh you need to apply the patch.

Recently came across this article:

[http://www.cyberciti.biz/tips/rhel-centos-linux-install-configure-rssh-shell.html]("http://www.cyberciti.biz/tips/rhel-centos-linux-install-configure-rssh-shell.html")

Regards,

k_grdn

---

### Post by jeffus_il on 2008-01-10
Read this:
[http://paradigma.pt/~gngs/sshjail/]("http://paradigma.pt/%7Egngs/sshjail/")

About creating an OpenSSh jail, i.e. limiting the user to a directory.

This is similar to the previous post, we posted together.

---

### Post by danifodor on 2008-01-10
Thank you guys for the replies! Now I have something to start with. 

Best wishes

Daniel

---

