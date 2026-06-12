---
title: "Firewall configuration"
date: 2009-04-30
forum: Security
---

### Post by Jonnox on 2009-04-30
Hi,

I need a firewall (software) that I can run to use white / black lists but I need to be able to configure it using scripts. I have taken a look into Firestarter but I can't seem to figure it out.

What I am doing essentially is having a script run at boot-up that will download a new black / white list and configure the firewall to use it. The script will be run as root but the firewall is for sub users to restrict access to websites.

Any ideas or pushes in the right direction would be greatly appreciated.

---

### Post by lovinglinux on 2009-04-30
[Moblock](http://moblock-deb.sourceforge.net/) can block sites by IP using blocklists. It also has custom scripts to load regular iptables commands. There is an optional gui, but everything can be done by command-line.

---

### Post by lovinglinux on 2009-04-30
BTW, Firestarter is not a firewall, it is an interface to create iptables rules, which is the real firewall. So Firestarter is basically a firewall manager and it's not recommended anymore.

---

### Post by bodhi.zazen on 2009-04-30
> **Jonnox said:**
> Hi,

I need a firewall (software) that I can run to use white / black lists but I need to be able to configure it using scripts. I have taken a look into Firestarter but I can't seem to figure it out.

What I am doing essentially is having a script run at boot-up that will download a new black / white list and configure the firewall to use it. The script will be run as root but the firewall is for sub users to restrict access to websites.

Any ideas or pushes in the right direction would be greatly appreciated.

Firestarter is depreciated and you should probably start by removing it.

The default firewall in Ubuntu is ufw, which is a command line tool.

You can use gufw if you want a gui.

From what you are describing, however, I think you should learn iptables.

[http://bodhizazen.net/Tutorials/iptables/](http://bodhizazen.net/Tutorials/iptables/)

---

### Post by Jonnox on 2009-05-01
Thank you for the prompt responces. I will look into both, I suppose I should learn IP tables anyways... Thanks again

---

