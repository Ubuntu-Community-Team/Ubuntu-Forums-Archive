---
title: "[SOLVED] samba autologon"
date: 2008-10-13
forum: Server Platforms
---

### Post by NetSkay on 2008-10-13
hey guys...
i have a samba daemon running, and i have 2 user groups, admins and fileserverUsers, users that are part of admins have full priviliges to the file server... my SMB config file is setup properly as far as i know, i can logon, read/write/delete files based on user permission, everything is in tip-top shape, however im wondering, how come when i have a user on samba/linux, that user matches exactly to the user on my windows workstation, password and username wise, however i always have to logon first, where in windows 2003 file server, if my username on the workstation matches that of the users on the server, im not asked to logon...
the reason im asking is because ive setup Distributed File System with VPN for more centralized access, and if u access a share through DFS, there is no logon screen because shared folders are mapped like regular folder on DFS, so how can i automate this logon thing, make samba check windows account first, before asking for credentials...

EDIT: for some reason, i have this one user, whos primery group is admins, and i also have a user called admin as primery group admins, i can login with admin but not with the other username... why is that, i dont get denied access, but when i type username and pass in windows, the credential box re-appears back... whats up with that

thank you

---

