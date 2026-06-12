---
title: "Create new user with duplicated home?"
date: 2006-09-03
forum: Server Platforms
---

### Post by jalanbuntu on 2006-09-03
After reading some threads, I've the decided to install NFS+NIS to create active directory on my network. Some people say that it is easier than using LDAP. After installing, I found new problem. I want that for every new user that will be created later should has default home directory that duplicated from other user created before. Why I need this is because I want for every new user have same default dekstop background, menu setting, icon, and other profile, but not the default dekstop like after we install ubuntu on the first time. 
How can I create new user with duplicated home from old user?

---

### Post by mssever on 2006-09-03
When creating new local users, whatever is in /etc/skel is copied to their home directory. So, you'd set up a new user like you want it, then copy everything in their home dir (including dot files) to /etc/skel. Something like ```
sudo cp -aR .* * /etc/skel
``` should do the trick. What I don't know is whether this will work in an NIS environment.

---

### Post by jalanbuntu on 2006-09-03
Thanks... I'll try it out, wish that it also work on NIS environment

---

### Post by venzen on 2006-09-04
NIS is ok and with the advice above you will have new users' home directoies with the files from /etc/skel. Also check out 'man adduser' for more options when creating users.

As far as NIS vs. LDAP goes, I can assure you that setting up LDAP is not difficult at all - I also heard that it was a drag setting up LDAP but when my organisation needed centralised logins, passwords, addressbooks and host info I set up LDAP (with shared NFS /home directory) in 6 hours.

---

### Post by jalanbuntu on 2006-09-05
I've succesful to install NIS and NFS on my network. New user also has home directory copied from /etc/skel. But there are errors when accessing client computer using account stored on NIS server,

for example Sound card is error when I try to login at NIS+NFS client.When I click di volume control icon on the panel, it will say error
"No volume control GStreamer plugins and devices found."
Any explanation?

another error is when I plug the USB storage. It can't be read from client computer :(

Any explanation how to fix this? :(

---

