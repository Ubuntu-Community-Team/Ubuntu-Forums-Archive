---
title: "SSH connection using key then sudo in nautilus"
date: 2008-04-14
forum: Security Discussions
---

### Post by robaldred on 2008-04-14
Hi,
I work for a web design company, our servers have root ssh disabled, i access the servers via ssh using a key, my user has access to root using sudo.

Usually all files are editing using SVN but there are few old projects that are not and I need to be able to edit files on them projects.

The servers use plesk, so all projects have different owners, therefore to edit them I almost always need to sudo, is there anyway I can use nautilus to sudo on the remote machine so I can edit these files in komodo?

At the moment I have to ssh in a terminal, sudo then use vim to edit the files, which I would prefer not to do as my knowledge of vim is limited.

I have added 'sudo su -' to my bash profile, which works if i use a terminal but I understand nautilus doesn't directly ssh into the remote machine so the profile doesn't get run.

Appreciate anyone's input on this.
Cheers

Rob

---

### Post by The Cog on 2008-04-15
Howo about using **ssh -XC** to connect in text mode, then **gksudo nautilus**?
 It's a bit slow over ADSL but it works.

---

