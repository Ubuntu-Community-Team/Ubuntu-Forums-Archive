---
title: "jailkit and ldap"
date: 2010-01-13
forum: Server Platforms
---

### Post by garretwp on 2010-01-13
I am trying to install jailkit onto a server that uses ldap to authenticate the users. I would like to jail a few users to their home directory and to only use ssh and a few other commands. I have tried using make_chroot_jail.sh and jailkit to accomplish this. The issue that I am running into is when the user logs into the server via ssh and then trying to issue the ssh command to get somewhere else, the ssh command complains about the user not existing and to go away. This is due to the user not being in the /etc/passwd file of the jail. I can easily solve this by adding that user to the jail's /etc/passwd file, but I do not want to do this manually. Is there a way to get ldap to work with the jails? Has anyone tried this? I am having a hard time finding any info regarding my situation. 

Thanks,

Garrett

---

