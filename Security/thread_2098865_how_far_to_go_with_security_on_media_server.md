---
title: "how far to go with security on media server"
date: 2012-12-27
forum: Security
---

### Post by Dmaxx67 on 2012-12-27
Guys I just built a media server with Ubuntu 12.04 64 bit. It sits behind my router ===> gig switch ===> Server. Only use laptop with ssh and RSA keys with password to talk to it since it is headless. I went crazy and followed this page,[http://www.thefanclub.co.za/how-to/how-secure-ubuntu-1204-lts-server-part-1-basics](http://www.thefanclub.co.za/how-to/how-secure-ubuntu-1204-lts-server-part-1-basics) for my last build but basically long story short i want to see what everyone actually does to secure their home servers. I am basically only using it to serve media to 4 local media centers over the gig switch. It does see the internet for security updates. 
Just want the guys that have been through this and know what is good and what is overkill for my situation.
Also i am only running  NFS for my file serving needs.

---

### Post by chadk5utc on 2012-12-28
> **Dmaxx67 said:**
> Guys I just built a media server with Ubuntu 12.04 64 bit. It sits behind my router ===> gig switch ===> Server. Only use laptop with ssh and RSA keys with password to talk to it since it is headless. I went crazy and followed this page,[http://www.thefanclub.co.za/how-to/how-secure-ubuntu-1204-lts-server-part-1-basics](http://www.thefanclub.co.za/how-to/how-secure-ubuntu-1204-lts-server-part-1-basics) for my last build but basically long story short i want to see what everyone actually does to secure their home servers. I am basically only using it to serve media to 4 local media centers over the gig switch. It does see the internet for security updates. 
Just want the guys that have been through this and know what is good and what is overkill for my situation.
Also i am only running  NFS for my file serving needs.

I wouldnt consider it overkill, I personally have key-based ssh login changed the default port22 to a much higher random unused port and set incoming/outgoing firewall allowing only whats needed. Logwatch set to email me reports and webalizer for other stats as its public facing. Also installed fail2ban to assist blocking some attacks. Im sure I could do more but (knock on wood) have no trouble, despite China and a few others trying lol...

---

### Post by mr-woof on 2012-12-28
As long as you haven't forwarded any ports to the unit or have upnp enabled on your router, no traffic from the internet should be able to reach it.

---

### Post by Dmaxx67 on 2012-12-28
I have SSH ports forwarded to it since I use a different port number. No upnp. Anyone else have a media server that see the internet?

---

### Post by mr-woof on 2012-12-28
If it's local to your lan, why have ssh forwarded to it if you won't be accessing it remotely?

---

### Post by CharlesA on 2012-12-28
Changing the port on SSH only reduces log noise due to attacks from bots probing port 22.

If you aren't running things like Apache, or BIND and the machine is not directly accessible from the internet, you don't really need to worry about 90% of those things.

The way I have my server set up is to only allow two users shell access via SSH - via keys only, not passwords and only allow connections to SSH from certain IP addresses. That helps prevent "log clutter" from bots trying to bruteforce your box.

As mr-woof brought up, if you are only accessing the machine locally, there is no need to forward ports.

---

### Post by Dmaxx67 on 2012-12-28
OK ill take care of that when I get home. Appreciate the help.  So basically I need to enable and configure ufw. Delete my port forward and just for a bit of overkill setup fail2ban. 
On my SSH I am using RSA KEYS but it also ask for a password. Should I disable the password?

---

### Post by Lars Noodén on 2012-12-28
You keys should all use strong pass phrases, but the server itself should not allow password logins, at least not from the net at large.  [PasswordAuthentication in sshd_config](http://manpages.ubuntu.com/manpages/precise/en/man5/sshd_config.5.html) should be set to 'no'  You can use the 'Match' directive to allow passwords from the LAN if you want.  

It's also important to set 'PermitRootLogin' to 'no' also.

---

### Post by TheFu on 2012-12-28
> **Dmaxx67 said:**
> OK ill take care of that when I get home. Appreciate the help.  So basically I need to enable and configure ufw. Delete my port forward and just for a bit of overkill setup fail2ban. 
On my SSH I am using RSA KEYS but it also ask for a password. Should I disable the password?

Actually, with **fail2ban **and listening on a high poirt (at the router), I think your public-facing ssh is just fine.  Internally, all my servers ssh listen on 22, but the router listens on random, high ports and translates those connections. Much easier that way.

As for internal security, using ssh and NFS does help. Just be certain to limit all connections to only the subnet.  Security needs to be layered, so that if 1 part fails, another layer of protection is still working.  I would make the NFS shares read-only to prevent little hands from deleting all your content.  You are probably already doing that.

---

### Post by CharlesA on 2012-12-28
> **Lars Noodén said:**
> You keys should all use strong pass phrases, but the server itself should not allow password logins, at least not from the net at large.  [PasswordAuthentication in sshd_config](http://manpages.ubuntu.com/manpages/precise/en/man5/sshd_config.5.html) should be set to 'no'  You can use the 'Match' directive to allow passwords from the LAN if you want.  

It's also important to set 'PermitRootLogin' to 'no' also.

Indeed. The match directive is quite handy.

---

### Post by cariboo on 2012-12-28
Before getting to silly about security on your local network, check what services are connected to what ports, and ip addresses, they decide what type of security you need. Key-based ssh access and nfs restricted to your local subnet, are about all you need.

to check what services are connected where, use the following command:

```
sudo watch netstat -anlp
```

check the screenshot of the above command, on my home server, that has no connections forwarded to the internet. the only foreign ip address, is the system I'm using to access the server.

---

### Post by Dmaxx67 on 2012-12-28
Great info guys. Gonna get to work on this once the family goes to bed. Gonna have to research this match directive. I'm assuming its done router side? Ive got a Cisco m20 running ddwrt. Ill check the netstat also. 
On my nfs do I need set my hosts allow file and hosts deny? Basically only set what machines need access through the hosts allow and also export configuration file.

---

### Post by CharlesA on 2012-12-28
> **Dmaxx67 said:**
> Great info guys. Gonna get to work on this once the family goes to bed. Gonna have to research this match directive. I'm assuming its done router side? Ive got a Cisco m20 running ddwrt. Ill check the netstat also. 
On my nfs do I need set my hosts allow file and hosts deny? Basically only set what machines need access through the hosts allow and also export configuration file.

the match directive is a part of ssh and is configured in /etc/ssh/sshd_config

[http://prefetch.net/blog/index.php/2006/09/05/limiting-access-to-openssh-directives/](http://prefetch.net/blog/index.php/2006/09/05/limiting-access-to-openssh-directives/)

---

### Post by Dmaxx67 on 2012-12-28
Appreciate that cuts my research time down. 
Does samba add anything.to security flaws? I have one windows 7 machine and can't get it and.nfs to play nicely.

---

### Post by Lars Noodén on 2012-12-28
> **Dmaxx67 said:**
> Great info guys. Gonna get to work on this once the family goes to bed. Gonna have to research this match directive.

The Match directive is explained in detail in the manual page for sshd_config.

You would use it something like this:

```

PasswordAuthentication no
Match address 192.168.100.0/24
        PasswordAuthentication yes

```

---

### Post by CharlesA on 2012-12-28
> **Dmaxx67 said:**
> Appreciate that cuts my research time down. 
Does samba add anything.to security flaws? I have one windows 7 machine and can't get it and.nfs to play nicely.

I haven't run into any problems with it, but it is a good idea to only use it locally and not give it access to/from the internet.

> **Lars Noodén said:**
> The Match directive is explained in detail in the manual page for sshd_config.

You would use it something like this:

```

PasswordAuthentication no
Match address 192.168.100.0/24
        PasswordAuthentication yes

```

Nice example. I just set something like that up so I can connect with a limited user for tunneling purposes.

---

### Post by Dmaxx67 on 2012-12-29
Do i need apparmor enabled on this server.

---

### Post by TheFu on 2012-12-30
> **Dmaxx67 said:**
> Do i need apparmor enabled on this server.

Need?  No.

Is it a good idea?  Perhaps.

Do I use it?  Not directly.  If it gets in the way, even on an internet facing computer, I disable and purge it from the system.

---

