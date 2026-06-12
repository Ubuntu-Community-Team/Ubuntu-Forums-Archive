---
title: "I need help setting up ssh key based login."
date: 2010-09-26
forum: Server Platforms
---

### Post by MechaMechanism on 2010-09-26
Apparently with an encrypted home directory, one needs to log out and then back in.  Now it works.

EDIT: I think the problem is on my laptop.  The laptop uses the netbook remix and during install, it offered an encrypted option and I selected the encrypted option.  There seems to be some kind of documented problems.  Apparently the ~/.ssh is not available until you login, but you need ~/.ssh in order to log in.  See my problem?

I went through all of the Ubuntu help documents online and offline and I still don't understand.

I have 2 computers.

A netbook named sandworm, has ssh client and server installed.  I use the password gui manager in the menu to create an ssh key, I selected create key only because I'm using thumb drive to move keys around.  Sandworm has correct permissions I think.  I need to use sandworm to log onto another computer.  Sandworm will be the client.  Also sandworm has encrypted home directory, but I don't need to login to it from another machine.

A desktop computer named gorilla with ssh client and server installed.  Gorilla is the computer I want to log into via ssh.  I also created ssh key on this machine as well.

Gorilla sshd_config I set to AllowUsers nate because on gorilla my user account is nate.

Both of them have key based login only.  Where do I put the pub key and which machine.  Do I copy and paste pub key into authorized_keys?  I tried pasting the sandworm pub key into gorilla authorized_keys file, did not work and I tried in reverse.  What do I do on each machine.

---

