---
title: "updating a website with rsync"
date: 2007-01-13
forum: Server Platforms
---

### Post by tr333 on 2007-01-13
i'm having problems trying to keep a website updated on an ubuntu-server using rsync...

i have started the rsync daemon by editing /etc/default/rsync, and that seems to be working fine.  i am using 'rsync -avr src user@server:/var/www/' to update the website directory, but i'm getting 'Permission denied' errors.  how can i get the server to run as root when updating the website directory (i have the chroot option in /etc/rsyncd.conf set to true)?

would it be easier to chown the /var/www/ directory to my user on the server, or is that a security risk?

---

### Post by MJN on 2007-01-14
Are you using 'root' as the <user>?

---

### Post by tr333 on 2007-01-14
i'm using my account name since root is disabled by default on ubuntu, and i don't want to enable it.

---

### Post by MJN on 2007-01-14
Then you'll proably have to adjust the folder/file permissions to be writable by your user.

Perhaps someone might be abke to come up with a more elaborate workaround however short of running as root I can't help but feel if there was such a solution then this would be a security vulnerability itself.

I use rsync running over SSH (i.e. not daemonised) to backup entire machines every night - this of course requires full root access at both ends however any security threat is mitigated by using key authentication and setting SSHD to only allow the rsync command to be executed if it is root logging in.

Mathew

---

### Post by tr333 on 2007-01-14
thanks.  ill give that a try when i get home from work.
i'm just a bit wary of accidentally doing 'rm -rf cgi-bin/' or something similar...

---

### Post by MJN on 2007-01-15
I know what you mean. However, that's all part of the fun! ;)

---

### Post by tr333 on 2007-01-15
thanks for the help with this :D 

it seems to work fine after taking ownership of /var/www/ with my account.  it doesnt really matter if it gets deleted anyway, since i can just rsync it again.

---

