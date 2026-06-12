---
title: "Monitor OpenSSH server with Snort?"
date: 2008-06-19
forum: Security
---

### Post by mvavrik on 2008-06-19
I'm running an SSH server for encrypted communications when connecting to my desktop remotely.  

I have set SSH to operate on a non-standard port (*22002*) and was wondering whether anyone has, or considers it important, to set up Snort IDS to monitor port 22002 (*SSH server*) for attacks. 

If so, are there any special flags you like to run with Snort or preferential way to set up the Snort config file?


Thanks!

---

### Post by whoop on 2008-06-19
As far as I could tell there is no ssh rule in the default ubuntu snort install. Maybe this is because monitoring ssh can be cpu intensive. I have however added a snort rule to monitor my ssh traffic, and cpu usage is allright.

```

alert tcp $EXTERNAL_NET any -> $HOME_NET 22002 (msg:"SSH incoming"; flow:stateless; flags:S+; sid:100006927; rev:1;)

```

The rule is not very informative yet, maybe there are ones out there that better suit your needs. But it tells me if someone is fiddling around with my ssh port.

---

### Post by eldragon on 2008-06-19
fail2ban monitors auth logs for failed authentications and bans ips accordingly.


quite handy and easy to setup.

---

### Post by mvavrik on 2008-06-19
> alert tcp $EXTERNAL_NET any -> $HOME_NET 22002 (msg:"SSH incoming"; flow:stateless; flags:S+; sid:100006927; rev:1;)

OK, so as long as you have your "HOME_NET" defined in the conf file, this will alert you based on *any* activity over the desired port, which in this case is 22002?  I suppose I would be most interested in multiple failed authentications.

> fail2ban monitors auth logs for failed authentications and bans ips accordingly

I'll look into this utility before I start asking you questions about functionality and being able to specify which logs to monitor, etc.  Thanks!!

---

### Post by gaten on 2008-06-19
I would suggest a couple of things to limit the attack vectors on your ssh server.

1) Disable password authentication and only use public key auth (eliminates brute force password attacks)
2) Disable **TCPKeepAlive** and use **ClientAliveInterval** instead to prevent TCP Spoofing attacks
3) Use the **AllowUsers** option 
4) Set **MaxAUthTries** to something like 2, this could frustrate attacks (although they are probably using scripts, so they probably won't care or notice).

I know that wasn't really your question, but I though I would throw it out there and see if it helped. Hope it did :)

---

### Post by mvavrik on 2008-06-19
> **gaten said:**
> I would suggest a couple of things to limit the attack vectors on your ssh server.

1) Disable password authentication and only use public key auth (eliminates brute force password attacks)
2) Disable **TCPKeepAlive** and use **ClientAliveInterval** instead to prevent TCP Spoofing attacks
3) Use the **AllowUsers** option 
4) Set **MaxAUthTries** to something like 2, this could frustrate attacks (although they are probably using scripts, so they probably won't care or notice).

I know that wasn't really your question, but I though I would throw it out there and see if it helped. Hope it did :)


No, that's great to know. I am using password authentication and haven't even given a thought to public keys as it is just me (hopefully ;) ) using the SSH server.  I suppose there's another thread for that. 

I have also been looking at this guide
[https://help.ubuntu.com/community/AdvancedOpenSSH]("https://help.ubuntu.com/community/AdvancedOpenSSH")

Thanks!

---

### Post by firsttimeuser on 2008-06-19
In my option, if you want to know who ssh into your box, you can just do it via watching ssh logs.

Maybe install syslog-ng to forward the ssh connectivity info to some log box remotely. 

> **whoop said:**
> 
```

alert tcp $EXTERNAL_NET any -> $HOME_NET 22002 (msg:"SSH incoming"; flow:stateless; flags:S+; sid:100006927; rev:1;)

```
.

---

### Post by kevdog on 2008-06-19
You could also implement the iptables to limit traffic on port 22 (or whatever port) to like 5 tries per hour -- limit command.  Of course this entails the extra step of setting up the firewall (but shouldn't take too long).

---

### Post by mvavrik on 2008-06-19
I'll run through these ideas.  Thanks a lot for the input.

---

### Post by mvavrik on 2008-06-20
> **kevdog said:**
> You could also implement the iptables to limit traffic on port 22 (or whatever port) to like 5 tries per hour -- limit command.  Of course this entails the extra step of setting up the firewall (but shouldn't take too long).

I think that setting up iptables is a bit much for my needs right now.  I'm looking for something to monitor SSH authentication for numerous failed attempts.  From what I understand, Snort can log this but is there a way to be alerted without sifting through the logs manually?

I think I'm asking a lot, but an ideal solution would be an IDS logging failed authentications working in conjunction with a log monitor to alert me of any failed authentications.

Mabye BASE (Basic Analysis and Security Engine)could be set up to send alerts?  I haven't installed it but from what I understand, it provides a front-end for reading Snort logs.  

Thanks.

---

### Post by cincout on 2008-09-08
As far as I'm aware snort is unable to detect failed authentications due to the fact all traffic is encrypted so it is unable to check the content of any packets. Snort is only able to alert on for example any connections to the port or excessive connection attempts depending on the rules you've set up.

The best way would be to use software that monitors the auth.log file for failed authentications.

---

### Post by jerome1232 on 2008-09-08
I definitely think fail2ban or denyhosts would be the ideal solution, I use denyhosts, everytime it blocks an ip it sends mail to one of my users, I have postfix/dovecot setup so I can check the system mail using any imap email client.

```
From nobody@localhost Mon Sep 08 06:47:15 2008
Envelope-to: root@localhost
Delivery-date: Mon, 08 Sep 2008 06:47:15 -0700
From: DenyHosts <nobody@localhost>
To: root@localhost
Subject: DenyHosts Report
Date: Mon, 08 Sep 2008 06:47:15 -0700

Added the following hosts to /etc/hosts.deny:

218.36.42.221 (218-36-42-221.rev.krline.net)

----------------------------------------------------------------------
```

---

