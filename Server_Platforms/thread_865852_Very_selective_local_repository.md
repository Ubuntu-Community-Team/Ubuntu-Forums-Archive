---
title: "Very selective local repository"
date: 2008-07-21
forum: Server Platforms
---

### Post by Aessa on 2008-07-21
I have a PC which is not on our network and should stay off if possible. It runs kubuntu feisty at the moment, and all works well.

What I want to do now is get some basic things going on it, like the simple "apt-get install build-essential"... There are so many dependencies (not even thinking about GIMP yet), installing them manually is not worth the effort.

Is there a way of creating a local repository (not using apt-mirror for a full mirror) with all the packages I want to install and their automatically calculated dependencies? I want to drop this repo then onto a CD and install it on the new PC. Our server runs ubuntu-server so I was hoping there is something available to at least spew out the list of dependencies. Can apt-get do this?

---

