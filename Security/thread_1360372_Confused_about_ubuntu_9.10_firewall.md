---
title: "Confused about ubuntu 9.10 firewall"
date: 2009-12-20
forum: Security
---

### Post by hatewindows on 2009-12-20
Hello all and happy holidays--I need a simply answer am i safe surfing the internet with a fresh install of ubuntu 9.10 running firefox? I would like to know if any firewall is on for protection or do i need another program installed? I was told that i'm safe from the install-Thanks for any help..

---

### Post by teward on 2009-12-20
Now now, I didn't say you were safe the moment you install ubuntu.  You have to configure the firewalls first.  Thats what Firestarter does (NOTE TO ALL: Reference [this thread]("http://ubuntuforums.org/showthread.php?t=1360347")), it configures the iptables.  If you don't do that, it won't work.  You can also reconfigure iptables manually (see [this]("https://help.ubuntu.com/community/IptablesHowTo")), but Firestarter does it and makes it easier.

---

### Post by hatewindows on 2009-12-20
So-firestarter will block only what i tell it to block or does it work blocking right after install?

---

### Post by rookcifer on 2009-12-20
You don't need a firewall if you haven't installed any servers.  In other words, if you are using Ubuntu pretty much as it came off the liveCD, then you don't have to do anything.  The only thing to keep in mind is not to install .debs from unknown sources.  Always use the package repositories.

---

### Post by hatewindows on 2009-12-20
Then i'm safe!  Cool thank you!!!!

---

### Post by euler_fan on 2009-12-20
> **hatewindows said:**
> So-firestarter will block only what i tell it to block or does it work blocking right after install?

Okay: firestarter's default policy is to deny all inbound connection attempts and to allow all outbound connections. You can change this from within its menus.

There is another couple of firewall config managers in the repos. All are good and have various quirks. However firestarter is a good one for the home user (as opposed to fwbuilder which is really for someone who has some idea of what they're doing).

---

### Post by teward on 2009-12-20
i agree with euler_fan.  Firestarter's a good firewall for your needs.

Even though I run an SSH server for my own use only off of my laptop, it doesnt run on a standard port, so the firewall helps to track unwanted connection attempts at the standard ssh/sftp ports on my computer.

---

### Post by bodhi.zazen on 2009-12-20
> **TrekCaptainUSA said:**
> Now now, I didn't say you were safe the moment you install ubuntu.  You have to configure the firewalls first.  Thats what Firestarter does (NOTE TO ALL: Reference [this thread]("http://ubuntuforums.org/showthread.php?t=1360347")), it configures the iptables.  If you don't do that, it won't work.  You can also reconfigure iptables manually (see [this]("https://help.ubuntu.com/community/IptablesHowTo")), but Firestarter does it and makes it easier.

If you are new to Ubuntu I suggest you start with this thread :

[Ubuntu Security - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=510812") 

In terms of a firewall, what is it you are trying to accomplish ? The OP specifically stated a default Ubuntu installation. 

By default, there are no significant servers listening for connections, so configuring the firewall any further will NOT add to security.

Furthermore, the default firewall is netfilter, which is configured by iptables. Iptables is not so new user friendly, so there are a number of configuration tools. The default tool in Ubuntu is UFW.

So, before you install firestarter, start with the default applications.

[http://blog.bodhizazen.net/linux/firewall-ubuntu-gufw/](http://blog.bodhizazen.net/linux/firewall-ubuntu-gufw/)

[http://blog.bodhizazen.net/linux/firewall-ubuntu-desktops/](http://blog.bodhizazen.net/linux/firewall-ubuntu-desktops/)

Frutermore, to give you a more specific answer we need more information.

What is your network architecture, do you use a router or direct connection to the internet ? Do you intend to run any servers or file sharing (torrents) ?

---

### Post by lovinglinux on 2009-12-21
> **hatewindows said:**
> Hello all and happy holidays--I need a simply answer am i safe surfing the internet with a fresh install of ubuntu 9.10 running firefox? I would like to know if any firewall is on for protection or do i need another program installed? I was told that i'm safe from the install-Thanks for any help..

A firewall won't protect your browsing activities, since Firefox does not accept remote connections (it's not a server), only generate connections requested by you.

> **hatewindows said:**
> So-firestarter will block only what i tell it to block or does it work blocking right after install?

Keep in mind that Firestarter is just a firewall manager, that allows you to create rules for the real firewall. You don't need firestarter to be running to be protected, once you configured it properly.

> **rookcifer said:**
> You don't need a firewall if you haven't installed any servers.  In other words, if you are using Ubuntu pretty much as it came off the liveCD, then you don't have to do anything.  The only thing to keep in mind is not to install .debs from unknown sources.  Always use the package repositories.

I agree. Most of the time, a firewall will be useless. If you don't have any servers running, then all incoming unrequested connections will be rejected, even without a firewall or with firewall rules that allow all traffic. On the other hand, if you have a server running, then the firewall is useful only if you want to allow certain machines to connect to the server while blocking others. For example to limit access only to machines on your local network. But if you want for example to use p2p applications, then the firewall is useless, because you will need to allow incoming unrequested connections anyway.

Additionally, if you use a router, the firewall is redundant.

> **TrekCaptainUSA said:**
> i agree with euler_fan.  Firestarter's a good firewall for your needs.

Even though I run an SSH server for my own use only off of my laptop, it doesnt run on a standard port, so the firewall helps to track unwanted connection attempts at the standard ssh/sftp ports on my computer.

I disagree. Just make a google search for firestater and you will find lots of threads with issues. The recommended firewall manager these days is gufw, which is easier than Firestarter, less buggy and better maintained (some people say Firestarter is not even maintained anymore). Besides, running Firestarter to monitor connection attempts is just a waste of time and a security risk, since Firestarter needs administrative privileges to run.

If you want to protect your ssh server, use encryption keys for authentication instead of passwords, disable password authentication, disable root access, configure an alternative port as you did and configure your router to accept connections only from your remote machine (if possible). If that is not enough, you can monitor the authentication logs. Monitoring connection attempts blocked by the firewall is waste of time. They are blocked. What you need to be concerned are successful authentications and that won't show in the Firestarter logs.

EDIT: I need to start typing faster or reduce my texts. I was beaten by the ubuntu security guru by 17 minutes :) Anyway, I think my post add some useful stuff too.

---

### Post by cariboo on 2009-12-21
Just to add to what lovinglinux said, Firestarter is no longer maintained by the origional author. The Debian maintainer adds bug fixes for each new release, but that is about it. There haven't been any new features added since 2005.

---

### Post by hatewindows on 2009-12-21
Well you all explained it to me 100% and I thank all of you!! Happy holidays!!!!!!  :):popcorn:

---

### Post by q.dinar on 2009-12-22
hello.
i use iptables.
i now have made /etc/iptables directory and several files in it: iptables.txt , iptables0.txt , iptables-ekiga.txt, iptables-transmissionbt.txt, iptables-network.txt.
i connect them this way: sudo iptables-restore < /etc/iptables/iptables-transmissionbt.txt (hm now i used sudo iptables-restore /etc/iptables/iptables-transmissionbt.txt - also works). iptables0.txt is iptables.txt without line/rule about mss which is needed only while adsl is connected, i have written that in /etc/network/interfaces:
```
auto lo
iface lo inet loopback

auto dsl-provider
iface dsl-provider inet ppp
pre-up /sbin/ifconfig eth1 up # line maintained by pppoeconf
pre-up iptables-restore < /etc/iptables/iptables0.txt
provider dsl-provider

auto eth0
iface eth0 inet manual

auto eth1
iface eth1 inet manual
```

that loads iptables automatically while ppp starts hm.. now i think what happen if ppp does not start, can be computer accessed from some provider's internal network? but, well, ppp started also automatically at my computer.

iptables.txt that i use now:
```
# Generated by iptables-save v1.4.0 on Tue Aug 11 10:43:20 2009
*nat
:PREROUTING ACCEPT [1767631:412242649]
:POSTROUTING ACCEPT [19660:1190746]
:OUTPUT ACCEPT [19702:1207381]
COMMIT
# Completed on Tue Aug 11 10:43:20 2009
# Generated by iptables-save v1.4.0 on Tue Aug 11 10:43:20 2009
*mangle
:PREROUTING ACCEPT [2540861:1028882700]
:INPUT ACCEPT [1012684:695407431]
:FORWARD ACCEPT [0:0]
:OUTPUT ACCEPT [806279:577537293]
:POSTROUTING ACCEPT [805932:577414903]
-A FORWARD -o ppp0 -p tcp -m tcp --tcp-flags SYN,RST SYN -m tcpmss --mss 1400:1536 -j TCPMSS --clamp-mss-to-pmtu 
COMMIT
# Completed on Tue Aug 11 10:43:20 2009
# Generated by iptables-save v1.4.0 on Tue Aug 11 10:43:20 2009
*filter
:INPUT ACCEPT [0:0]
:FORWARD ACCEPT [0:0]
:OUTPUT ACCEPT [0:0]
-A INPUT -i lo -j ACCEPT 
-A INPUT -m state --state RELATED,ESTABLISHED -j ACCEPT 
-A INPUT -j DROP 
-A FORWARD -j DROP 
-A OUTPUT -o lo -j ACCEPT 
-A OUTPUT -m state --state RELATED,ESTABLISHED -j ACCEPT 
#dns
-A OUTPUT -p udp -m udp --dport 53 -j ACCEPT 
#https
-A OUTPUT -p tcp -m tcp --dport 443 -j ACCEPT 
#http
-A OUTPUT -p tcp -m tcp --dport 80 -j ACCEPT 
#icq
-A OUTPUT -p tcp -m tcp --dport 5190 -j ACCEPT 
#freenode irc
-A OUTPUT -p tcp -m tcp --dport 8001 -j ACCEPT 
#irc
-A OUTPUT -p tcp -m tcp --dport 6667 -j ACCEPT 
#msn
-A OUTPUT -p tcp -m tcp --dport 1863 -j ACCEPT 
-A OUTPUT -j DROP 
COMMIT
# Completed on Tue Aug 11 10:43:20 2009
```
but i do not know exactly whether 8001 port is needed now.

---

