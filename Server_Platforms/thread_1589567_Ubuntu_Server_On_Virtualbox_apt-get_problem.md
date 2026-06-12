---
title: "Ubuntu Server On Virtualbox apt-get problem"
date: 2010-10-06
forum: Server Platforms
---

### Post by danhotrod on 2010-10-06
Hello,
I have just installed Ubuntu Server 7.10 On Virtualbox, when i try to install a package it says:

server1a@serv1a:~# sudo apt-get install phpmyadmin
Reading package lists... Done
Building dependency tree
Reading state information... Done
E: Couldn't find package phpmyadmin

Or when i try to apt-get update it says 'Reading Package Lists... Done' , it doesn't say anything else, but i did try to edit the /etc/apt/source.list file and uncomment the  commented out lines but nothing happened, just the same 'Reading Package Lists...Done'

Any help with this problem would be greatly appreciated.
cheers,
danhotrod

---

### Post by druhboruch on 2010-10-06
The name of the file is sources.list not source.list.
Is it possible that you renamed it?

---

### Post by snowpine on 2010-10-06
All support for the 7.10 release has ended. The software repositories are gone. I recommend a fresh reinstall of the current release (10.04).

---

