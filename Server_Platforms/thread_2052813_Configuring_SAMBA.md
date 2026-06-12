---
title: "Configuring SAMBA"
date: 2012-09-04
forum: Server Platforms
---

### Post by Orgil on 2012-09-04
Hi all,

environment variable:
Server version: Ubuntu 12.04.1 LTS \n \l
Samba version: 3.6.3
Network workstation: XP (only).

I'm fairly new to Linux and have installed Samba on my Ubuntu server.
I used this article to help me configure the server:
[http://www.samba.org/samba/docs/using_samba/ch04.html](http://www.samba.org/samba/docs/using_samba/ch04.html)

I have configured it to be a DC and was able to add workstations to it, but only on my computer I was able to connect with no errors, and the domain profile was created correctly on my XP machine.

I did set up me to be the User with rights to add computers to domain.

On all other workstation, the domain profile was not created (there is a TEMP profile the users are using) and I get an error that the profile was not created because of "insufficient rights".

on the smb.conf file I used this to create the machine account:
"add machine script = sudo /usr/sbin/useradd -N -g machines -c Machine -d /var/lib/samba -s /bin/false %u"

on the Linux machine, in the "[profile]" folder, I got one directory named %u and under it, I got the machine name i was logged on to when adding it to the domain.
I guess that there are rights issue that needs to be dealt and also, the %u in "add machine" line needs to be changed.

Appropriated any help I can get,

Eitan

---

