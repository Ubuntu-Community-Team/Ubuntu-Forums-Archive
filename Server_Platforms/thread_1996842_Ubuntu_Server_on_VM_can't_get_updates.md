---
title: "Ubuntu Server on VM can't get updates"
date: 2012-06-04
forum: Server Platforms
---

### Post by MrScott420 on 2012-06-04
Hello everyone, this is my first post and I did check to see if there were other similar posts beforehand.

I'm having difficulty in obtaining updates from an Ubuntu Server that I'm running in VirtualBox. I've bridged my host machine's wireless adapter and I pinged google through the server VM and I got a response. However, when logged in as root and typing the command "apt-get update" I get the following response:



Here is my sources.list file for further reference:



I hope someone can show me where I'm going wrong here.

Thanks in advance,
Scott

---

### Post by MrScott420 on 2012-06-04
Apologies, it seems I can't just copy and paste images straight into a message box, I've uploaded the relevant images

Scott

---

### Post by LHammonds on 2012-06-04
Looks like a DNS issue.

There is a slight difference in how Ubuntu 12 is setup for resolving DNS from earlier versions.

When you edit the network interface to assign a static IP, you also add a dns-nameserver entry there.

The error message says it cannot resolve gb.archive.ubuntu.com so if you try to ping gb.archive.ubuntu.com, you probably cannot resolve the DNS name to an IP address because of this.

Look on [this post]("http://ubuntuforums.org/showpost.php?p=11967553&postcount=3") under the "Initial Configuration" section for an example of the config file with DNS in it.

LHammonds

---

### Post by MrScott420 on 2012-06-04
Thanks for pointing me in the right direction!

I've resolved the DNS issue now and my Ubuntu Server is bang up to date. I did it by following the advice on this post: [http://askubuntu.com/questions/140688/upgraded-server-to-12-04-dns-no-longer-working](http://askubuntu.com/questions/140688/upgraded-server-to-12-04-dns-no-longer-working)

Hopefully should be able to get this server up and running with a client soon!

---

