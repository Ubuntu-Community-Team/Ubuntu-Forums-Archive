---
title: "Samba server open to the internet?!"
date: 2009-08-28
forum: Security
---

### Post by xgm541 on 2009-08-28
So basically from my understanding of Samba, it can be used as a filesharing server solution for my home network, same as my previous OS, windows XP had been doing. The PC i have ubuntu installed is my media center for everyone in my house to be able to access music, videos, etc. 

I setup samba by having my drives auto mounted on startup, and shared. These drives are NTFS file format, if that is of any relevance. 

Rather than accessing my old windows xp network by browsing "Network" folder on my other PC's i simply typed in my network IP address of my media PC into file explorer and all the shared drives/printers showed up. This might be a little confusing so i will go into detail. 

Assume my media PC's network IP address is 192.168.1.5. I would open up My computer on any other computer connected to my router and type in "file://192.168.1.5" and all the shared content was displayed. 

I wanted a similar setup for samba. After setting it up, voilla, works flawlessly. However, a few days of running ubuntu I realized this caused a big security hole. My media center also runs a web server application using a no-ip domain. I typed into my file explorer, just for fun, the public IP of my media PC. So lets assume my media PC uses the IP "xmg541.no-ip.com". **Typing it into my computer as "file://xgm541.no-ip.com" accesses my files!**

So everyone on the internet who has my IP can access my shared folders/printers, edit them, delete them, etc. I cannot think of anything more unsecure. Can  someone point me in the right direction in finding out how to limit samba to only local connections? according to the samba help site:

> 

[LIST]
[*]Networking Section - use "hosts allow" and "hosts deny" 
[/LIST]

# hosts allow = 127.0.0.1 192.168.1.0/24
hostal allow = 127.0.0.1 192.168.1.1 192.168.1.2
hosts deny = 0.0.0.0/0
hosts deny 0.0.0.0/0 = all others.

This is suppposed to allow only my network to access the samba server.

First of all, my "Networking" section of smb.conf doesnt have a hosts allow section. I added it myself,
and then configured it to the following:


hosts allow = 127.0.0.1 192.168.1.0/255
hosts deny = 0.0.0.0/0

In other words, I want to be able to access my files from localhost, and any IP from 192.168.1.0 to 192.168.1.255

I then used the command "sudo /etc/init.d/samba reload" which is supposed to reload my configuration, but it doesnt work. I can still access my samba server from my public IP.




I am new to Ubuntu, however coming from windows XP acting as my media server, I am quite disappointed at what happened. I was in no way, shape or form aware that this would be the case. How do i fix it?

---

### Post by cdenley on 2009-08-28
"sudo /etc/init.d/samba reload" will reload the shares in smb.conf, not your global configuration.
```

sudo /etc/init.d/samba restart

```

---

### Post by trundlenut on 2009-08-28
have you tries accessing it from a computer that is outside your home network?
Also what is set in the way of port forwarding on your router?

---

### Post by movieman on 2009-08-28
> **xgm541 said:**
> I am new to Ubuntu, however coming from windows XP acting as my media server, I am quite disappointed at what happened. I was in no way, shape or form aware that this would be the case. How do i fix it?

I don't believe there's anything Ubuntu-specific here: if you put a Windows box on the Internet and allow access to the SMB service, then anyone can access it there too.

The solution, as you've seen, is not to allow remote (internet) access to the SMB ports regardless of what OS you're running. I strongly suspect that your firewall will already block those ports if you try to connect from a system that's outside your LAN... if not, you should configure it that way ASAP.

---

### Post by bodhi.zazen on 2009-08-28
I suggest you not use samba this way. Use ssh. If you install a ssh server you can mount a share with sshfs or from windows with winscp.

Be sure and secure your ssh server (ues keys, disable passwords, and configure iptables or use denyhosts or fail2ban).

---

### Post by cgb on 2009-08-28
If you can access the samba shares from outside your network you must either have the port open on your Router/Firewall or setup as DMZ.  You really should lock this down on your Router to make sure any unnecessary ports are not open.

**also noticed your host allow file should read as follows since its a class C network and /255 is an invalid option...

```
hosts allow = 127.0.0.1 192.168.1.0/24
```

---

### Post by pietjanjaap on 2009-08-29
In smb.conf file you can let only specific ip numbers connect, so fill this in.

Then install guarddog(firewall), here everything is not allowed after installing. There is a internet part, and a home part, you have to change what is allowed. 
For internet allow http, for samba allow home network(not for internet).
And for other programs you need, it is possible you to do more allow.

Then put on the samba map only permissions with a user name(s).

---

