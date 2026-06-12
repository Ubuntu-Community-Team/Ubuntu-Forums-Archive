---
title: "Cannot sudo in LTSP client or use SSH"
date: 2016-05-13
forum: Server Platforms
---

### Post by clueo8 on 2016-05-13
I have an LTSP server running on Ubuntu 14.04.4 LTS, and I'm noticing an odd issue.  I have a user account specifically for the clients created on the server and it is a member of the sudo group (on the server).  Whenever I try to sudo within the client with that user, it prompts me for that users password.  I know what the password is because I use it to log into my fat client at startup.  The password never works, it just keeps prompting me for it again.  Is this a limitation of an LTSP thin client; can you run sudo within a thin client?  I enabled the root account within the client and was able to log into it once from a Ctrl+Alt+F1 TTY but I would really just like my normal user to be able to use sudo.  Within the server as well as the chroot, I have "%sudo	ALL=(ALL:ALL) ALL" in the /etc/sudoers file and as I mentioned, my user is a member of the sudo group on the server (as well as in the client; it must trickle down to the chroot automatically).

Also, I have sshd running on the client but it does not accept my password there either... I found that the ssh-keys were getting ripped out when the image was being built ([https://sourceforge.net/p/ltsp/mailman/ltsp-discuss/thread/51EC001A.50507@gmail.com/](https://sourceforge.net/p/ltsp/mailman/ltsp-discuss/thread/51EC001A.50507@gmail.com/)) so I re-generate those at startup as was recommended in that url... typing my password doesn't seem to work in these ltsp fat clients!  (FYI: PasswordAuthentication yes is configured in my chroot's sshd_config).  I was able to get into ssh using a id_rsa key but not with the password... It's almost as if typing in a password anywhere within the client outside of the login screen is not working.

---

