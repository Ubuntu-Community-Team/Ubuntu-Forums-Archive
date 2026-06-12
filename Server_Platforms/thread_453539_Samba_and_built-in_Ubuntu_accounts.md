---
title: "Samba and built-in Ubuntu accounts"
date: 2007-05-24
forum: Server Platforms
---

### Post by awarberg on 2007-05-24
The Samba server howto for feisty ([http://ubuntuguide.org/wiki/Ubuntu:Feisty#Samba_Server](http://ubuntuguide.org/wiki/Ubuntu:Feisty#Samba_Server)) explains how to setup samba and share user home folders. 

Every setup option starts with a reference to "How to add/edit/delete system users".

I have an account on my Windows XP machine and an account on my Ubuntu installation. The usernames and passwords are identical.

I would like to share the home folder of my Ubuntu user account on samba. 

But in order to do this, the ubuntu feisty guide asks me to create my credentials using smbpasswd -a my_username. 

Why?! I just wan't to share the home folder. My home folder is uniquely bound to my Ubuntu user account anyway - why not use the stored credentials of that account for samba authentication?

This feels plain silly. On Windows there exist only one set of credentials for a user and they are used throughout the system. Why is it necessary to create two accounts for the same user on Ubuntu, in order to get samba working?

Hopefully there is a workaround for this issue - but the guide does not mention it, if this is the case. I would appreciate if instructions for reusing linux account credentials with Samba could be given. Furthermore I suggest the writers of the guide update it to reflect this, obviously better, way to share home folders.

Best regards
Andreas

---

### Post by borahshadow on 2007-05-24
I think this is because samba uses encrypted passwords for network security and locally ubuntu does not need to 
I believe there is a way to keep the samba userdatabase synced with the unix database when I was configuring my server I never got that far before my boss(dad) decided against private shares but I think there is a way

---

