---
title: "how to ssh my server from outside my office where USB modems are not recognized on Li"
date: 2011-07-23
forum: Server Platforms
---

### Post by jamesbon on 2011-07-23
I want to SSH to my server which is some where on the internet.I am currently not in my office and the internet access I have is via a Windows machine in a home environment.The Ubuntu latptop does not recognizes the USB modem at home envrionment.I do not want to use Windows and putty.I prefer using Ubuntu only. As I have many aliases and other commands on my ubuntu machine only. But the sad part is my Ubuntu 10.04 does not recognizes the USB modem. The modem is

056cx9000
I have tried using many things like usb-modeswitch etc on the Ubuntu machine at home and all of such methods have failed. I had asked this question: [http://ubuntuforums.org/showthread.php?p=11076473#post11076473](http://ubuntuforums.org/showthread.php?p=11076473#post11076473)
bit but since all such permutations have failed so I need to give this Ubuntu laptop access to internet via a proxy which I did using Windows.

SO I gave my Ubuntu laptop the internet via this windows machine by a software known as ccproxy.

I am simply not able to understand like we use apt-get behind the proxy by specifying export http_proxy=http://IP:port, can something similar be done for SSH?

I have internet access at my home via a windows proxy. What do I need to do in order to be able to SSH to my server which is on the internet? The proxy software I am using on windows server is ccproxy and that is a Windows machine. I use Ubuntu and my server where I have to SSH is also a Ubuntu server.


I am currently trying to reach my Linux server from my home where the Ubuntu does not recognizes my USB modem and there is no IT manager in my home that sits on my head. Since my modem is recognized only by Windows in my home I gave internet access to the Ubuntu machine using a software known as ccproxy.

Can I ssh into my server in above setup.What can be the correct way to do so?

---

### Post by clrg on 2011-07-23
What happens when you try to establish a SSH connection? Show me the output. Preferably with "-vvv".

---

### Post by jamesbon on 2011-07-23
```
 ssh root@myserver.com -vvv
OpenSSH_5.3p1 Debian-3ubuntu5, OpenSSL 0.9.8k 25 Mar 2009
debug1: Reading configuration data /etc/ssh/ssh_config
debug1: Applying options for *
debug2: ssh_connect: needpriv 0
ssh: Could not resolve hostname myserver.com: Name or service not known

```

That is the output as you wanted.I was Googling and came across some thing known as Corkscrew.The situation which I am describing is some thing similar to [http://lindesk.com/2007/04/using-ssh-over-a-proxy/](http://lindesk.com/2007/04/using-ssh-over-a-proxy/)

---

