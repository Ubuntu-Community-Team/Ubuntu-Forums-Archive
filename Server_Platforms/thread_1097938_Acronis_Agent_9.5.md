---
title: "Acronis Agent 9.5"
date: 2009-03-16
forum: Server Platforms
---

### Post by s0bda on 2009-03-16
There was a great tutorial earlier on this subject, which i followed to the letter but still can't get the agent to start/work.

All i need is the Agent installed and running on Ubuntu 8.10 server (no gui only cli) so i can back it up to an Acronis Server that's on a Windows Server.

Please help.
Thanx in advance.

Adam

---

### Post by s0bda on 2009-03-26
I figured it out.
For those of you who want to know:

Acrnonis just released an 'ubuntu_build' compiler to address issues with Acronis Agent running on Ubuntu 8.10

Just make sure to run apt-get update before running it or you will run into trouble with ubuntu_build not finding a specific file from a repository.

so all you need is:
apt-get update
ubuntu_build from Acronis website
AcronisTrueImageServerLinux and CD Key from Acronis 9.5 CD
(Just install agent and trueimage - not sure if the secure zone works...)

its a little buggy (acronis_scheduler) doesn't always run in the back ground so you might need to run service acronis_scheduler start   -    if that doesn't allow you to connect from Windows Acronis server, then simply just re-install the acronisagent from AcronisTrueImageServerLinux setup  (./AcronisTrueImageServerLinux)   takes only a few second to re-run it and seems to fix the problem.

Will give more details if anyone needs it.
BTW: the file level restore is not very good as it creates a folder called  Drive(C)  which screws with the ubuntu as bash compains ( is invalid.  Makes it difficult to clean up after the fact.

Anyone got a simple way to delete/remove  Drive(C) folder?  I managed to get rid of it before with rm -r   but in another restore test this stupid Drive(C) folder got droped on the root of the drive and now rm - r won't work for me.

---

