---
title: "openssh"
date: 2012-09-15
forum: Server Platforms
---

### Post by ghs on 2012-09-15
Hi all,

My problem is I was having issues with my home server (ubuntu 12.04), so I restarted it. Then when i tried to use putty to remote in, the ssh service was deleted some how (probably from me, just dont remember doing it).  So I have tried uninstalling both openssh-client and server packages but the ssh/sshd services are still not there which means i cant run them. i have been looking for a way to fix this to no avail. I am new to the Ubuntu boxes but I am enjoying them:)

things i have tried 
Sudo apt-get remove openssh-server
sudo apt-get remove openssh-client
sudo apt-get remove ssh

sudo apt-get install openssh-client
sudo apt-get install openssh-server

sudo ps -erf | grep sshd- and showed the service wasnt running, checked /etc/init.d and neither of them are in there as well

im trying to avoid and entire new reinstall.


i have also tried re-installing it through webmin and looking to see if the services are there and their not

Thanks for the help

Regards.

---

### Post by Lars Noodén on 2012-09-15
openssh-server needs to be installed on the remote machine, the one you are trying to log in to.  If you have a console on that machine open, you can try checking the status of SSH to see if it is running.  

```

/etc/init.d/ssh status

```

You can also see what, if anything is installed on that machine.

```

dpkg --get-selections | grep ssh

```

---

