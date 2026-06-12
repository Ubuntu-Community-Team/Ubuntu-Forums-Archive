---
title: "apt-get issues"
date: 2005-04-08
forum: Repositories &amp; Backports
---

### Post by didi on 2005-04-08
Hi Folks 

I installed Kubuntu and then installed gnome and started using gnome.

I get this error messages continously with apt-get update and it ask me to updat and so on and son

Reading package lists... Done
W: GPG error: [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security Release: Unknown error e xecuting gpgv
W: GPG error: [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hoary Release: Unknown error executin g gpgv
W: You may want to run apt-get update to correct these problems

Furtermore can u pls suggest an Integrated development tool for ubuntu for C++ and Java .

Many thanks in advance

didi

---

### Post by Moeru on 2005-04-08
[QUOTE=didi]Hi Folks 

I installed Kubuntu and then installed gnome and started using gnome.

I get this error messages continously with apt-get update and it ask me to updat and so on and son

Reading package lists... Done
W: GPG error: [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security Release: Unknown error e xecuting gpgv
W: GPG error: [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hoary Release: Unknown error executin g gpgv
W: You may want to run apt-get update to correct these problems

Furtermore can u pls suggest an Integrated development tool for ubuntu for C++ and Java .

Many thanks in advance

didi[/QUOTE]

When you run apt-get update, what happens? If I remember correctly, those are privacy key support (PGP).

---

### Post by didi on 2005-04-08
[QUOTE=Moeru]When you run apt-get update, what happens? If I remember correctly, those are privacy key support (PGP).[/QUOTE]

Hi Moeru

When I run apt-get update or apt-get -f update 

I get messages saying like updating and waiting for hearers etc.. and the end I get the same erronous messages . I tried apt-get updat with and without -f several times more than ten times and it is the same result always.

Do you think I should modify my repositeries or what do I need to do.

Cheers
did

---

### Post by Moeru on 2005-04-08
[QUOTE=didi]Hi Moeru

When I run apt-get update or apt-get -f update 

I get messages saying like updating and waiting for hearers etc.. and the end I get the same erronous messages . I tried apt-get updat with and without -f several times more than ten times and it is the same result always.

Do you think I should modify my repositeries or what do I need to do.

Cheers
did[/QUOTE]

Could possibly be a repository down. I get the same when updating due to people.debian.org havin issues tryin to install gnomebaker when its not even there  :?

---

### Post by p!=f on 2005-04-08
Maybe expired key. Should be fine soon.

---

