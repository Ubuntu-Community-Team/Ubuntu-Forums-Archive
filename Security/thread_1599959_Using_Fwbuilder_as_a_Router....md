---
title: "Using Fwbuilder as a Router?..."
date: 2010-10-18
forum: Security
---

### Post by VcDeveloper on 2010-10-18
I have a ubuntu 9.10 VM (running kvm) that accept incomming web connection from both the internet and LAN.  The internet comes through a 2wire router with only port 80 open.  I have three other ubuntu VM's (Web server, MySQL server & Postfix server).  All VM's sits on top of a ubuntu 10.04 LTS and I have one other computer a WIndows Vista Ultimate.  This is my total LAN setup.

I'm using 1 NIC for all tracffic and the VM's are bridged.  I want to use fwbuilder to direct all traffic to the VM's (Web server, MySQL server & Postfix server),  ufw is disabled (not using).  I've read this post **[ ufw doesn't open ports]("http://ubuntuforums.org/showthread.php?t=1525510&highlight=fwbuilder&page=2")  ** because I was hoping someone had solved the ssh connection error I'm also getting when trying to install the firewall.

I like the interface because it's very easy to use.  Just cannot get past the ssh error.  This part doesn't make any sense to me when I'm running the apt on the same computer.  So why would I need to login!  I don't have the sshd installed.  I'm assuming correctly this is why I'm getting the connection error.

Is there any why around this ssh login or I don't have choice and fwbuilder just requires it?

---

### Post by cariboo on 2010-10-18
For your ssh problem, have you tried:

```
sudo ufw allow 22
```

or

```
sudo ufw allow ssh
```

---

### Post by VcDeveloper on 2010-10-18
> **cariboo907 said:**
> For your ssh problem, have you tried:

```
sudo ufw allow 22
```or

```
sudo ufw allow ssh
```

I don't have ufw enabled nor the sshd installed.  Just the ssh client and I'm running fwbuilder on the same VM Router server.  Do I have to run fwbuilder on my main server just to get this to work?

---

### Post by cariboo on 2010-10-19
Just to cover all the bases, the ssh client is installed by default. Do you have openssh-server installed on your vm?

---

### Post by VcDeveloper on 2010-10-20
No, I didn't have the sshd installed, but I went on and installed it and put fwbuilder on my main server.  And everything is working now.  Kinda like it there too.

.....but need help routing http connections to my web server.  Lots to reading to do, but hoping someone here may already successfully done this already and can share rule and nat entries.

---

### Post by VcDeveloper on 2010-10-20
Will I think I found a solution to my routing.  That is, I will use fwbuilder as my firewall and guidedog as my router.  What do you think?  I don't think fwbuilder is naturally setup for routing packets.  It's document sofar are kinda confusing to me now.  Just have to keep playing around with it until I master the whole thing.

---

