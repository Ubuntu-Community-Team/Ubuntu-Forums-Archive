---
title: "SSH fails but Apache and Samba work"
date: 2007-08-25
forum: Server Platforms
---

### Post by revford on 2007-08-25
Hello, I'm new to Ubuntu and just setting up some things I need on the home network, the server, Holly, is running Feisty and I need Apache, Samba and SSH on it.

Apache and Samba work fine, all the machines that come onto the LAN can connect fine, Windows, Mac, Slack and Ubuntu.

The problem has come now I'm trying to get SSH logins working.

From Holly I can ssh into localhost with:

```


gav@holly:~$ ssh localhost


```

This works fine, but when I use another machine, it just times out, like so:

```


gav@bluemidget:~$ ssh holly
ssh: connect to host holly port 22: Connection timed out


```

I'm not sure if it's important but Holly connects to the router via a cable, the other machines connect via wifi.

Holly has a static IP, the others are configured by DHCP.

In the logs, local SSH logins are listed in auth.log, the failed attempts to connect remotely are not.

Syslog tells me that an attempt to connect to port 22 has been made, but I'm not sure what it's trying to tell me about it:

```


Aug 25 12:24:08 holly kernel: [107089.928290] Inbound IN=eth1 OUT= MAC=00:80:ad:41:26:a8:00:1a:73:60:80:6f:08:00 SRC=192.168.1.102 DST=192.168.1.30 LEN=60 TOS=0x00 PREC=0x00 TTL=64 ID=7610 DF PROTO=TCP SPT=40133 DPT=22 WINDOW=5840 RES=0x00 SYN URGP=0 


```

I can see the IP addresses, ports and MAC addresses of the machine involved, but I can't see why it's not working.

I hope someone can help me out with this, I had this all running for years under Slackware so I'm guessing it's some strange config option I'm not aware of in Ubuntu.

---

### Post by southernman on 2007-08-25
try ssh [email]hollyusername@holly.static.ip.addr[/email]ess

That should work if you've not modified the config file and you have openssh-server installed on the box your logging into.

---

### Post by revford on 2007-08-25
Cheers for the help so far.  I get the same thing if I address is with the IP address or the hostname:

```


gav@bluemidget:~$ ssh gav@192.168.1.30
ssh: connect to host 192.168.1.30 port 22: Connection timed out


```


I've not messed with the sshd config files at all.  Just installed it.

Where would I check firewall settings, to see if I've monkeyed about with something like that?

It's the only other thing I can think of.

---

### Post by southernman on 2007-08-25
Weird. It'll be something really simply and make us both feel less than stellar when it slaps us in the face!

It's acting like two things could be wrong to me:
1- You only have ssh installed on the server and not openssh-server
2- You fiddled with the /etc/ssh/sshd_config file and set the login timeout to low

To list your fiewall rules do "iptables -L" It should be empty unless you specifically added any rules to it.

Would you mind posting your /etc/ssh/sshd_config file?

---

### Post by revford on 2007-08-25
Ah ha!  I think we've found the problem.

SSHd is installed and running, I did it the Ubuntu way using aptitude and not from source.

The problem seems to be firewalling, I don't remember messing with it and iptables -L threw a mass of rules back at me.

Is there a quick and painless way to reset the iptables rules?  restoring a config file from another Feisty install maybe?

---

### Post by southernman on 2007-08-25
I am not totally hip on iptables my friend so I can only offer this link:

[https://help.ubuntu.com/community/IptablesHowTo]("https://help.ubuntu.com/community/IptablesHowTo")

Hope that helps.

---

### Post by revford on 2007-08-25
Many thanks, I'll go read up on iptables.

Cheers!

---

### Post by revford on 2007-08-25
All sorted now, thanks again.

---

### Post by southernman on 2007-08-25
> **revford said:**
> All sorted now, thanks again.
That's great! Glad to have helped somehow. :)

---

