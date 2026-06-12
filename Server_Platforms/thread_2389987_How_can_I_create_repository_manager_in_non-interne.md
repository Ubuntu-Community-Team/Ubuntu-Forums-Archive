---
title: "How can I create repository manager in non-internet-offline environment?"
date: 2018-04-24
forum: Server Platforms
---

### Post by balzwiferz on 2018-04-24
I would like to create a repository manager server for other ubuntu servers in private network without access to internet.
what is the best solution (synaptic/keryx/apt-offline/etc)?

---

### Post by LHammonds on 2018-04-24
My Google-Fu results:

[Personal repositories]("https://help.ubuntu.com/community/Repositories/Personal")
[How to create a local apt repository]("https://askubuntu.com/questions/170348/how-to-create-a-local-apt-repository")
[Setup local repository (mirror)]("https://www.tecmint.com/setup-local-repositories-in-ubuntu/") - Will require ~120 GB but will mimic official repository
[Local Ubuntu mirror]("https://www.howtoforge.com/local_debian_ubuntu_mirror") (HowToForge)
[Setup local repository Ubuntu]("https://www.maketecheasier.com/setup-local-repository-ubuntu/") (looks fishy but might have helpful info)

**EDIT:** Disclaimer - I have not done such a thing before.

LHammonds

---

### Post by Frogs Hair on 2018-04-24
Hello and Welcome

I would start with this [page ]("https://help.ubuntu.com/community/AptGet/Offline/Repository")and the links there in.

---

### Post by balzwiferz on 2018-04-24
I've seen most of the results that you sent,
but there are some ways.
what is the best way to create repository that other servers in the private network will update?

---

### Post by ju2wheels on 2018-04-27
Nexus repository instance running in Docker on the repository host. May take a bit of work to get the apt repo plugin working though but thats what I use at work.

---

