---
title: "Need help getting gitweb to work with gitolite"
date: 2010-10-17
forum: Server Platforms
---

### Post by K. Hendrik on 2010-10-17
Hi,
I've been trying for the last week to get gitolite and gitweb running on my ubuntu 10.04.1 Server (with Apache and OpenSSH selected on install).
gitolite is working fine i installed it from the git and created a user git which has all the repos lying in his home directory.
I've been trying various guides to setup the gitweb interface but they never seemed very clean nor did they support configuriong access rights for gitweb in the gitolite.conf
Also i would like to enable the daemon too and configure its rights in the gitolite config. (haven't looked into that because i need the gitweb first)

essentialli what i want to do is programm with some people with different rights on a projekt (gitolite) and publish it's status when its ready on the web (gitweb) and also give a quick download possibility (git-daemon)

I hope some one knows a clean way to do it.

THX a lot K. Hendrik

---

### Post by K. Hendrik on 2010-10-24
SOLVED:
what has to be changed:
add www-data to group git
change permissions on /home/git/repositories to r for group
change permissions on /home/git/projects.list to r for group
edit /home/git/.gitolite.rc to do the same for new repos.

could have be done at install when asked to modify .gitolite.rc then everything would have worked from the start

---

