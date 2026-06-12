---
title: "Ubuntu Server 12.04 SSH problem"
date: 2012-07-02
forum: Server Platforms
---

### Post by frog44 on 2012-07-02
I have just installed Ubuntu 12.04 server for a second time and struck the same problem twice. I cannot Putty the server unless I stop ssh and put it into debug mode. Otherwise I get 'network error - connection timed out'. With ssh in debug mode (-d -d -d) all is well and I can log in from my Windows 7 PC. Any ideas from anyone?

---

### Post by jumpyjester on 2012-07-02
Hi Frog44,

with my limited knowledge it may be that because of the reinstall you may need to check/clear the known_hosts file on the ubuntu server.

this may help.

let me know if it does or you need me to go in to more detail.

John

---

### Post by frog44 on 2012-07-02
Thanks John, but the plot thickens. Known_hosts does not exist. in [email]root@myserver:~/.ssh[/email] I've only got id_rsa and id_rsa.pub

Frank

---

### Post by darkod on 2012-07-02
Have you tried checking with netstat if the ssh service is running correctly? I forgot the options you need to use right now, but if you don't know them I can google it.

---

### Post by jumpyjester on 2012-07-02
hmmmmm, need to ask the silly question then. I assume when you did the install, did you select openssh server as a server type or have you installed the packages manually?

---

### Post by darkod on 2012-07-02
Another silly question, there is no firewall blocking you, right? But I guess if that was the issue, the debug mode would get blocked by the firewall too.

Worst case, you could try purging openssh-server and reinstalling. Just the package, not the server.

---

### Post by frog44 on 2012-07-02
How installed? Used the 'perfect server' guide and yes ssh is definitely running. But I'm still left with this:
ssh running: no connection
ssh -d -d -d running: all is well

---

### Post by darkod on 2012-07-02
What is the output of:
```
netstat -lnptu
```

---

### Post by jumpyjester on 2012-07-02
a good way to test frog is to ssh the other way round as in from the server to the windows PC. as for install try apt-get install openssh-server

---

### Post by frog44 on 2012-07-02
Great hint Darko - you can tell I'm new to this ;-)
The IP4 address for port 22 is set to 0:0:0:0 and I'm guessing it should by my server IP. Tried debug mode again, but that also states 'Server listening on 0.0.0.0 port 22 and now I cannot Putty in debug mode either. Something flakey somewhere?

---

### Post by frog44 on 2012-07-02
I'm going for the re-install.....

---

### Post by jumpyjester on 2012-07-02
apt-get remove openssh-server

---

### Post by darkod on 2012-07-02
The 0.0.0.0 should be fine, it only means that it's listening on all interfaces, in case there are more than one.

Don't forget to purge the package completely, in case there is some error in the config files. Something like:
```
sudo apt-get remove --purge openssh-server
sudo apt-get install openssh-server
```

---

### Post by frog44 on 2012-07-02
A re-install fixed the problem, but I'll never know why I got this problem twice after a 'standard install'.

Thanks for the quick help!

Frank

---

