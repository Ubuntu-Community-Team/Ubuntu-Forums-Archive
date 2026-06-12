---
title: "Anybody know a guide to setup a user server"
date: 2015-12-17
forum: Server Platforms
---

### Post by leonardvb2 on 2015-12-17
hi guys , maybe a stupid question , but i want to setup a server where all the users are stored. the operating system (14.04 LTS) wil be running on normal machines , but the need to be able to read out the user data en settings from the server. this to create a system that it does not matter where or on witch machine they login on the net work , they always get the same user settings and apps available ..


maybe a guide somewhere or is this possible ? it would help a lot 

i am not looking for a thin client system , because the workstations will be running on there own cpu.


thanx and kind regards , leo

---

### Post by newbie-user on 2015-12-17
LDAP with roaming profiles. I use it in my network, although using OpenDirectory as the LDAP server

Stuff to get you started:
LDAP - [https://help.ubuntu.com/lts/serverguide/openldap-server.html]("https://help.ubuntu.com/lts/serverguide/openldap-server.html")
NFS - [https://help.ubuntu.com/14.04/serverguide/network-file-system.html]("https://help.ubuntu.com/14.04/serverguide/network-file-system.html")

---

