---
title: "Home directory permissions mysteriously change upon login/logout! Why?!"
date: 2013-06-22
forum: Server Platforms
---

### Post by trevorhanning on 2013-06-22
My server has multiple users, and I am the administrator.  I began to notice problems while connecting via SSH w/ RSA keys.  If I was logged into the server already (via a different window), the RSA key would be accepted.  If I was not logged in already, the key would be rejected.  As it turns out, this has to do with permissions on my /home/me/.ssh directory and my ~/.ssh/authorized_keys file.  **What boggles my mind is that when I'm logged in, the permissions are set up perfectly.  When I log out, my home directory permissions switch (*mysteriously, and automatically*) to 700.**  I verified this by logging in as another user and running ls -al /home while logging in/out as myself from another window

When I am *logged out*, the home directory permissions look like this: 

[FONT=courier new]drwxr-xr-x  3 root    root     4096 Jun 20 22:29 .ecryptfs
**drwx------**  6 trevor  trevor   4096 Jun 21 23:11 trevor[/FONT]

However, when I am *logged in* (whether it be on the machine itself, or via SSH), the permissions on my home directory mysteriously change to: 

[FONT=courier new]drwxr-xr-x  3 root    root     4096 Jun 20 22:29 .ecryptfs
**drwxr-xr-x**  6 trevor  trevor   4096 Jun 21 23:11 trevor[/FONT]

HOW DOES THIS HAPPEN??!!  *totally befuddled*

---

### Post by steeldriver on 2013-06-22
Hello and welcome to the forum

I don't use an encrypted home, so take this with a grain of salt but I think that when you do, your home directory is not actually decrypted and mounted into the filesystem until you login - so probably what you are seeing are the permissions of the empty mount point

If you want to use ssh with encrypted home dirs, then I think you will need to specify an alternative location for your authorized keys file so that it's readable *before* your home directory is decrypted, e.g. in /etc/ssh

```
/etc/ssh/trevor/authorized_keys
```

Then modify the sshd_config file 

```

#AuthorizedKeysFile     %h/.ssh/authorized_keys
AuthorizedKeysFile      /etc/ssh/%u/authorized_keys

```

Hope this helps

---

### Post by trevorhanning on 2013-06-22
Thanks for the reply steeldriver!  I haven't solved it yet, but I think your tip got me headed in the right direction.

---

### Post by trevorhanning on 2013-06-22
[https://help.ubuntu.com/community/EncryptedHome](https://help.ubuntu.com/community/EncryptedHome)

I think steeldriver hit the nail on the head (pun intended ;)  If anyone else has this issue, check out the "Caveats" section of the above page.

---

### Post by trevorhanning on 2013-06-22
See this too [https://bugs.launchpad.net/ubuntu/+source/openssh/+bug/362427](https://bugs.launchpad.net/ubuntu/+source/openssh/+bug/362427)

---

