---
title: "samba domain controller + vista printing problems"
date: 2008-09-26
forum: Server Platforms
---

### Post by argail1980 on 2008-09-26
Hi folks,

I have a Gutsy Samba+LDAP Domain controller running (used this HOWTO: [http://ubuntuforums.org/showthread.php?t=640760]("http://ubuntuforums.org/showthread.php?t=640760")). The workstations (Window$ Vista x64) are in seperate buildings, i.e. a few of them in building one and some in building two. The server is in building one. Now these buildings have different subnets what was not a problem when getting the workstations to auth versus my domain controller. 

The problem is, that the workstations in 2 cannot access the printers via samba. Most of the workstations in 1 can.
There are two kinds of errors, each occuring depending on when I try to install the printers (maybe Vista is sensitive to the moon phase or so). One time Vista says: "Could not connect, error 0x000006f7", the next time it asks me for the driver file and when i specify the location, where it is, Vista says something like "Driver not suitable..blah..".

I googled this first error and there are a few hits where they say I had to recompile samba (I'm not keen on that). But then, why do the Vista workstations is the other Subnet work.

VLAN is not an option because I'm not responsible for the LAN and the switches.

Any hints where I could look for the error? Like always, precise error messages would be helpful, but it's Windows...

Any help would be great

Ubuntu Gutsy server
Vista Business

---

### Post by argail1980 on 2008-09-29
bump

---

