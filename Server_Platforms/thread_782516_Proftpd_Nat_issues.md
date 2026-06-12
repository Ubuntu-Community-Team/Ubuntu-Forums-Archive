---
title: "Proftpd Nat issues"
date: 2008-05-05
forum: Server Platforms
---

### Post by Bananas21ca on 2008-05-05
I currently have a server setup running multiple VM's. One of my clients is having a real hard time reaching the FTP server on his box.
Here is the setup.

I have the FTP server running on port 2000 and set the passive ports to 2001-2999. Since all the VM's are behind a NAT, I forwarded ports 2000-2999 through Iptables.
I can easily connect to the server from my home connection, however my client cannot connect in either Passive or Active mode.

Would my client being behind a NAT also cause problems with this configuration? If so is their any way to make it work?

Thanks in advance for any help.

---

### Post by windependence on 2008-05-05
Sounds like a firewall issue to me. Go to [www.canyouseeme.org](www.canyouseeme.org) and check to make sure your ports are open from the outside. Some ISPs block some weird ports also. If you don't see these ports as open, try dropping your firewall and check them again.

-Tim

---

### Post by smileypaul on 2008-05-05
I've had the same problem with a few of my clients FTP server's. If you use the terminal to ftp from the outside world, you'll see that it gets stuck at the PASV command. 

To be honest, i have tried many different things, and the only solution that consistenyl worked was to use FileZilla FTP client. For some unknown reason, i have NEVER had a problem connecting to any of my ProFtpd servers using this client..

All of the others are inconsistent..

Obviously the problem is, how do you explain to a client that this is the solution? ridiculous.

But give it a shot.

ps: you can look into masquerading the address, or also manually compiling the newer version of proftpd... although none of these worked for me. 

best of luck


edit:   Can he connect, but not list? Or just not connect at all?  

if he cannot connect at all, its a firewall issue. You can run a port scan from the outside world

```
 nmap -P0 -vvvv -p1999-2005 insert_ip_here 
```

---

