---
title: "aptitude wanting to remove packages added with apt-get, why?"
date: 2011-01-06
forum: Server Platforms
---

### Post by mdlueck on 2011-01-06
Seems like always if I add a package with apt-get, next time I use aptitude to update packages on a server, the packages I added with apt-get are automatically marked for removal.

I must, in aptitude, "forget new packages" and "cancel pending actions" then update the package list, remark packages needing updating, THEN aptitude has forgotten it wanted to remove packages.

Why can aptitude and apt-get NOT get along!?!!? ggggrrrr!!!!

Currently I have 10.04 on all servers, thus where it still is a problem.

---

### Post by James78 on 2011-01-06
What programs did you install, what is it trying to remove? Example of the commands you enter/entered? Screenshot/photo perhaps? Need more information.

---

### Post by mdlueck on 2011-01-06
For example, I just updated one server to ooRexx 4.1, which is a non-Ubuntu package, downloaded from sourceforge. So I installed that via the command line:

dpkg -i ooRexx-4.1.0-ubuntu1004.i386.deb

Then today Ubuntu needed an update, so I went in aptitude to do that:

u
U
g

And I see the ooRexx package marked for removal.

Then I must mess around to reset its thinking as I described in my OP.

And yes, I see it was that I installed the package via dpkg and not apt-get in this particular case. So updated my subject line.

---

