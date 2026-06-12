---
title: "Can't SSH into virtual server"
date: 2011-12-09
forum: Server Platforms
---

### Post by MrChudley on 2011-12-09
Hi all, I am new to linux and just got this virtual server set up. I'm not sure what exactly has happened, but I get the following error message:

ssh: connect to host at [ip address] port 22: Connection refused

Has anybody got any suggestions? I can still get access through the serial console on the hosts site, or through virtualmin. This is pretty frustrating though.

Thanks in advance :)

---

### Post by Habitual on 2011-12-09
Things that might keep you out are...
Is sshd started? 
Do you have an SSH key? 
Firewall rules
incorrect IP or other DNS-related issue.

The provider/host/reseller should have sent out an email with instructions for access to your server.

Does it have a Control Panel like cPanel/WHM or Virtuozzo?

---

### Post by jonobr on 2011-12-09
if you get into your remote machine and are able to open a terminal type
```
sudo tcpdump -vvv -i any port 22
```

Do your ssh magic.

If you see a packet in the output, it means its most likely hitting it. If you don't see anything then your not getting there.

Mostly likely though sounds like ssh is not installed?

A few things to check,

On the server

```
 telnet 127.0.0.1 22
```

This should give output showing the ssh and openssh version installed.

type
```
netstat -a | grep ssh
``` it should show its listening for ssh requests
When you first ssh and run the above command again, you should see another entry showing connection is established and the remote device.

or
```
sudo apt-get install openssh-server
```

If it says already the latest , its installed
If its not it will tell you which packages are going to be installed , how much room and should it proceed (y/n)

---

