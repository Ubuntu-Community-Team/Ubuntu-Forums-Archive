---
title: "Which is better GUI for IP Tables. gufw or firestarter."
date: 2008-07-23
forum: Security
---

### Post by SSVegito888 on 2008-07-23
Which is better GUI for IP Tables. gufw or firestarter.




Thanks,

SSVegito888

---

### Post by hyper_ch on 2008-07-24
are you sure you need any at all?

---

### Post by SSVegito888 on 2008-07-24
I am planning on installing openssh on my computer and am going to enable port forwarding through modem so I can access the server from anywhere. 



Also, I would like to create a samba share to share files with Windows PCs.



As you can probably guess I am trying to transfer from Windows.

I know Linux is a lot more secure than Windows, but I just want to have the best protection I can get.


Thanks,

SSVegito888

---

### Post by hyper_ch on 2008-07-24
well, would you agree that a firewall normally is there to prohibit access? Then how would a firewall help running sshd when you close the port so you can't reach it?

---

### Post by SSVegito888 on 2008-07-24
I am not exactly sure what you mean, but I am going to open port on modem and add rule to allow ssh in firewall.


I am also planning on installing something to blackilst IPs from accessing ssh server.


Any advice?

---

### Post by cpetercarter on 2008-07-24
I think that you will find that Firestarter does what you want. There is always something comforting about a GUI that tells you that everything is OK!

---

### Post by Archmage on 2008-07-24
Please read varous Howtos before opening ssh to the internet. This is a huge risk and a lot of systems have been comprobmise, because they have a lack of security.

(Different ports, bans, limit IP-range, good passwrod, keys and so on.)

---

### Post by SSVegito888 on 2008-07-24
Thanks for all of the help hyper_ch, cpetercarter, Archmage.




Also. Archmage, can you recommend any how-tos for Openssh.


Cpetercarter, I may need a little help configuring firestarter.

When I first started firestarter, a wizard came up.  The first thing I did was to allow DHCP because I have DSL.  The next step is where I need help:

Internet connection setup.  I am planning on installing a wireless network.  Also, I may want to tunnel over SSH from my notebook computer with putty to my Desktop (Will Be running Openssh) to the internet. Do I need to enable internet connection sharing to do this?


Thanks,

SSVegito888

---

### Post by hyper_ch on 2008-07-24
> **Archmage said:**
> Please read varous Howtos before opening ssh to the internet. This is a huge risk and a lot of systems have been comprobmise, because they have a lack of security.

Rather because of weak usernames/passwords and not trying to prevent brute-force.

Well, what do you need a firewall for? Basically to limit access to certain services. So either you close a service completely with a firewall - which is sort of contradictory if you intend to run a ssh server and want to remotely login - or you do limit ips either by allowing only specific ones or banning undesired ones.

As for samba, IMHO, it would be sufficient to deny the router's IP. Then your lan should be protected. Regarding SSH you actually do want to have access from outside so closing it with a firewall is not what you desire. If the password is strong then it is sufficient IMHO to just install an auto-ban service like denyhosts or ban2fail.

Security is an ongoing process and just installing a firewall (because you need to do that on other OSes) without knowing why doesn't protect you at all.

---

### Post by SSVegito888 on 2008-07-24
OK thanks for the help.



Are their any programs that will autoblock an IP if it tries brutefore attacks or if someone fails authentication so many times (Such as 3)?


Thanks,

SSVegito888

---

### Post by hyper_ch on 2008-07-24
there are, I even mentioned two of them

Modifying iptables maybe usefull in some cases but it is definitively not usefull in all cases. Just the expression "I need to have a firewall to be safe" is completely wrong. It's much better to understand your needs and act accordingly ;)

---

### Post by SSVegito888 on 2008-07-24
OK, I wasn't exactly sure if would they would autoblock or if I would have to manually go into program and add IP addresses to block.


Also, where can I find good how-to guides to setup openssh?



Thanks,

SSVegito888

---

### Post by hyper_ch on 2008-07-24
```

sudo apt-get install openssh-server denyhosts

```

that's it... after 3 unsuccessful tries to login from one IP that IP will get auto-banned to the /etc/hosts.deny file.

you can modify denyhosts to set higher limits (like 5 or 10 unsuccessfull logins) or expire the bans after a certain time or not just block the IPs for SSH but for all services...

---

### Post by kevdog on 2008-07-24
iptables can do this limitation directly if you want through the limit extension (you need to write the rule write).

As mentioned above, 2 other options are denyhosts and fail2ban which set up time limits.  Both work fundamentally different.  I believe denyhosts works through modification of the /etc/hosts file (or a derivative), whereas fail2ban works through iptables or the firewall.

---

### Post by ChumleyEX on 2008-07-24
I've been using fail2ban for quite awhile now and it works great with ssh, but I can't get it to work too well with proftp. Fail2ban is supposed to work with most of the net services you would use. Like http, ftp, mail, etc, so it's certainly worth looking into.

---

### Post by hyper_ch on 2008-07-24
denyhosts can be easily configured to ban an ip from all services.

---

### Post by SSVegito888 on 2008-07-24
I am trying to configure firestarter and need a little help.


I have installed firestarter and have run it for the first time.

A wizard pops up.  For the first option I enabled DHCP because I have DSL.

The next screen asks if I want to enable Internet Connection Sharing.

This is one of the places I need help. I am planning on installing a wifi network. I am also planning on using the openssh server on my desktop.  I would like to be able to tunnel from my notebook computer (inside network). through my desktop's openssh server (inside network) to internet.  So I was wondering, to do all of this, do I need to enable Internet Connection Sharing on firewall on Desktop with the Openssh Server.


Thanks,

SSVegito888

---

### Post by kevdog on 2008-07-24
ICS is only needed if you have two wireless cards or wired cards or simply two nics and you want to directly connect one computer to another (either wired or wirelessly).  I'm not sure of your setup but to use ICS you need two NICS.  Do you have this?

---

### Post by SSVegito888 on 2008-07-24
I have a wireless nic on my notebook and a wired nic on my desktop, so I guess I don't need to enable this feature.



But I am planning on getting a wireless router with built in ethernet ports.


I am still not sure if I need this feature or not.  But I am leaning more towards no.


Thanks,

SSVegito888

---

### Post by kevdog on 2008-07-24
You do not need this feature.  The wireless router uses iptables (possibly) depending on the configuration -- ie dd-wrt or openwrt.

---

