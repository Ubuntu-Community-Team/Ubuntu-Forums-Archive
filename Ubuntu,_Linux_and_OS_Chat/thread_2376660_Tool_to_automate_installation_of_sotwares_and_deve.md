---
title: "Tool to automate installation of sotwares and developement tools"
date: 2017-11-04
forum: Ubuntu, Linux and OS Chat
---

### Post by keysuke on 2017-11-04
Hello friend! I'm  a programmer and use ubuntu a quite long time and i always face the same issue: Software installation and configuration.
As a programmer i need some tools to work such as an IDE, apache, nodeJs (and other packages from node), dbms and other software like spotify and google chrome. I rarely use the current repository version for those apps, my usual steps are:
[LIST]
[*]search for the app i need
[*]add ppa
[*]update & install
[/LIST]
Every time that has a new ubuntu flavor i erase everything and install the new OS version, losing all my content. The only way is take a note of every app i have installed to install again in the new system.
Someone know any tool to automate this steps?
I'm looking for something that i can write a recipe code and ,in every system, install everything that the other system has with only a few commands. i'm thinking in something like docker comopose file or anything that works like package.json for npm.

thanks for any tips

---

### Post by ajgreeny on 2017-11-04
Have a look at ```
man dpkg
``` and search in that for **--get-selections** and **--set-selections** which may help you do what you want, though I have no idea how you would automate a search for and enabling of a PPA.

---

### Post by ian-weisser on 2017-11-04
Seems like a plain old shell script can easily do what the OP is asking for.

---

### Post by keysuke on 2017-11-04
> **ian-weisser said:**
> Seems like a plain old shell script can easily do what the OP is asking for.

Yeah, i think this might help too. But i'm looking for something more high level than simple shell scripts, i like the way npm install works. I wish i could write all dependecies i need and do a "dependecies install" so the software will download and install everything for me.

---

### Post by ian-weisser on 2017-11-05
> **keysuke said:**
> I wish i could write all dependecies i need and do a "dependecies install" so the software will download and install everything for me.

That's an excellent description of most package managers, including apt.

I'm not sure I understand the problem.
Ubuntu doesn't seem to have what you want (because you don't use the repositories).
Apt doesn't seem to do what you want.
Is that about it?

---

### Post by oldfred on 2017-11-06
from lovinglinux - use dpkg to list installed apps
[http://ubuntuforums.org/showpost.php?p=7157175&postcount=5](http://ubuntuforums.org/showpost.php?p=7157175&postcount=5)
[http://kevin.vanzonneveld.net/techblog/article/restore_packages_using_dselectupgrade/](http://kevin.vanzonneveld.net/techblog/article/restore_packages_using_dselectupgrade/)
From old install
dpkg --get-selections > ~/my-packages
From New install
sudo dpkg --set-selections < my-packages
sudo apt-get -y update
sudo apt-get dselect-upgrade
#IF you get this error:
dpkg: warning: package not in database
sudo apt-get install dselect
sudo dselect 
   -> Update
   -> Install 

As part of my backup I also export sources also. But if newer Ubuntu ppa may not have newer Ubuntu in list.

 But do not just import all sources as that can lead to issues of versions:
[http://askubuntu.com/questions/2038/backup-software-sources](http://askubuntu.com/questions/2038/backup-software-sources)
sudo cp /etc/apt/sources.list ~/sources.list.backup
Otherwise if you have added any PPAs or other sources, the tip will only reinstall Ubuntu files,

---

