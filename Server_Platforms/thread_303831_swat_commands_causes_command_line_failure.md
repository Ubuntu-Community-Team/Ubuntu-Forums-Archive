---
title: "swat commands causes command line failure"
date: 2006-11-20
forum: Server Platforms
---

### Post by peter@kkvs on 2006-11-20
If a swat command is issued at the command line then the computer hangs and nothing else can be entered. return will space down without the prompt but any commands entered do not work.
Have to ctrl-alt-delete to restart server
example commands
sudo swat -P  or
sudo swat -s /etc/samba/smb.conf

installed ubuntu server 6.06.1 with samba, smbclient, smbfs, openssh, netkit-inetd and swat.

I can use swat from remote hosts, I can access root page as well as user page but cannot restrict user page because I cannot enter the commands.

Additonal problem - some users can access swat but some cannot. those that cannot can login to samba and see there shares and they show up ok when pdbedit -Lv user is issued, but swat does not recognise them  ?  any clues

---

