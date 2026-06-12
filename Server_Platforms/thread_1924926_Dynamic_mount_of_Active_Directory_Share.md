---
title: "Dynamic mount of Active Directory Share"
date: 2012-02-13
forum: Server Platforms
---

### Post by ronw69 on 2012-02-13
I have many Ubuntu clients they log on to a Active directory network with Likewise. All of these clients could have any of 100 different users log on to them at any time. I need to map the users AD share automatically on the desktop or in GVFS places. I have tried using the gvfs-mount command but it calls for entering the users name and password. I have thought of creating a bash file and using the mount command with the USER global variable but I am not aware of a global variable for the password.

---

### Post by ronw69 on 2012-02-16
[COLOR=black][FONT=Verdana]I am redefining the question hoping that with this wording I will get an answer.[/FONT][/COLOR]
[COLOR=black][FONT=Verdana]I have many Ubuntu client computers they log on to a Active directory network with Likewise. All of these client computers could have any of 100 different users log on to them at any time. I am trying to have a connected share on the desktop or in GVFS places as soon as a new user logs, this share would be tied to their user name IE:(\\server\users\username). So in order to do this the authority given to the user at login from active directory should allow the login without having to re-login to the share. If there is no way to use this given authority then is there a way to capture the user name and password so that a BASH script could be written to automatically create this share?[/FONT][/COLOR]

---

### Post by ruffEdgz on 2012-02-16
I haven't used it for SAMBA shares before but have you heard of a service called 'autofs'. I used it with NFS based mounting from a linux server to a linux client but it looks like after reading the Ubuntu Community documentation on 'autofs' site: [https://help.ubuntu.com/community/Autofs](https://help.ubuntu.com/community/Autofs)

Best of luck.

---

### Post by koenn on 2012-02-16
you probably need to revise your samba-to-AD conf. 
In a case like this, samba shouldn't be using its own set of users, but use the AD accounts and authenticate them against your Domain COntroller(s). That fixes your user/password problem; I think likewise should be able to do it and the mechanism underneath it is also documented in the samba manuals.

Once you have that sorted out, you can look at the mounting issue. With authentication out of the way, a logon script or maybe autofs or something similar of should get you there.

---

