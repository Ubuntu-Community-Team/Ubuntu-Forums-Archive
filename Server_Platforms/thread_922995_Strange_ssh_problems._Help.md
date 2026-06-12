---
title: "Strange ssh problems. Help"
date: 2008-09-17
forum: Server Platforms
---

### Post by sonicgg on 2008-09-17
I am using ubnuntu8.04, network is DSL, and i am using a router. I want to ssh to my home machine from office, so I config a ssh server on port 22, and mapping router's port 22 to ubuntu machine. The strange thing is I can not ssh into my machine externally in most time, but sometimes I can. in most time ,i got the following error: 

ssh -v mymachine

OpenSSH_4.7p1 Debian-8ubuntu1.2, OpenSSL 0.9.8g 19 Oct 2007
debug1: Reading configuration data /etc/ssh/ssh_config
debug1: Applying options for *
debug1: Connecting to ******* [124.254.***] port 22.
debug1: Connection established.
debug1: identity file /home/**/.ssh/identity type -1
debug1: identity file /home/**/.ssh/id_rsa type -1
debug1: identity file /home/**/.ssh/id_dsa type -1

then ssh client hangs.

does anyone have any experience about what's going on?

---

### Post by azadpanchi on 2008-09-26
Did you look at /var/log/messages for any errors related to SSH.  I would do that.

You are trying to see where the problem maybe, since SSH is hanging you are probably able to reach your computer.  Try to see if there are any network issues just in case, 100 count ping to your computer at home should help.

Also trying changing the SSH port to something else to see if the problem recreates itself.

---

