---
title: "sudo stopped working after samba smb edit, plus su - password also stopped working!"
date: 2011-05-09
forum: Server Platforms
---

### Post by Jesusminded03 on 2011-05-09
Hello all!

I am very new to Ubuntu server (11.04) and am hoping this is a simple fix.

I was editing the smb.conf in samba to allow for group access sharing folders. Before doing this I added the groups, added users, set the users passwords, etc. After adding folders in the smb.conf (I was following a tutorial), I exited the vi with wq and then restarted the virtual machine (VirtualBox). After the restart I went back to edit it again to correct a name mistake and the server would no longer accept my username, saying it was not in the sudoers file. Tried to use visudo to fix, but the machine would not take the root password. I'm assuming the root password is mine, being it is the one I enter during the install... Is that right? 

Any suggestions? I'd really like to avoid starting from scratch with a fresh install.

thanks a ton for your help!

---

### Post by sisco311 on 2011-05-09
Hi and welcome to the forums!

Sounds like you removed your user from the admin group. You can fix it from the recovery mode: [http://psychocats.net/ubuntu/fixsudo](http://psychocats.net/ubuntu/fixsudo)

The root account password is locked by default, hence you can't su to root. See: [uhelp]community/RootSudo[/uhelp]

---

