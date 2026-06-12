---
title: "Problem installing Gitolite on Ubuntu"
date: 2012-07-17
forum: Server Platforms
---

### Post by RogerI on 2012-07-17
I have what I would call a "vanilla" install on Ubuntu Server 12.04 (downloaded and installed on the 15th) on Hyper-V.
All seems well with Ubuntu. Synthetic NIC is great. No issues detected.
My plan is to use it as a central GIT repository using Gitolite.
I have SSh correctly installed (at least I think it is because I can "ssh [email]myaccount@mydomain.com[/email]".
The key was generated on my Mac in Terminal and copied up. That worked fine.

My problem is that when I attempt to install Gitolite I get the following error:

[INDENT]***No adminkey given - not setting up gitolite.***[/INDENT]

These are the commands I used to perform the install:
[INDENT]
sudo apt-get install git-core
sudo apt-get install gitolite
[/INDENT]

I've also tried this:
[INDENT]
sudo apt-get install git-core
sudo adduser \
    --system \
    --shell /bin/bash \
    --gecos 'git version control' \
    --group \
    --disabled-password \
    --home /home/git \
    git
sudo apt-get install gitolite
[/INDENT]
...same result

Some version info:
Git core: 1:1.7.9.5-1
Gitolite: 2.2-1
Ubuntu: 12.04

Any ideas?

---

### Post by RogerI on 2012-07-18
Appreciate it if anyone could confirm that Gitolite is compatible with Ubuntu Server 12.04LTS?

Has anyone installed it successfully or am I en route to a dead end?

---

### Post by peskydonut on 2012-07-25
I was able to install it fine following [these instructions]("http://www.countableset.ch/blog/blog/2012/04/29/ubuntu-12-dot-04-installing-gitolite-and-gitweb/"), **with one exception**: instead of putting my public key into /tmp, I placed it into ~/git (on the server) and ran  ```
cd ~git; gl-setup mykey.pub
``` > **RogerI said:**
> I have what I would call a "vanilla" install on Ubuntu Server 12.04 (downloaded and installed on the 15th) on Hyper-V.
All seems well with Ubuntu. Synthetic NIC is great. No issues detected.
My plan is to use it as a central GIT repository using Gitolite.
I have SSh correctly installed (at least I think it is because I can "ssh [EMAIL="myaccount@mydomain.com"]myaccount@mydomain.com[/EMAIL]".
The key was generated on my Mac in Terminal and copied up. That worked fine.

My problem is that when I attempt to install Gitolite I get the following error:[INDENT]***No adminkey given - not setting up gitolite.***[/INDENT]These are the commands I used to perform the install:[INDENT]
sudo apt-get install git-core
sudo apt-get install gitolite
[/INDENT]I've also tried this:[INDENT]
sudo apt-get install git-core
sudo adduser \
    --system \
    --shell /bin/bash \
    --gecos 'git version control' \
    --group \
    --disabled-password \
    --home /home/git \
    git
sudo apt-get install gitolite
[/INDENT]...same result

Some version info:
Git core: 1:1.7.9.5-1
Gitolite: 2.2-1
Ubuntu: 12.04

Any ideas?

---

