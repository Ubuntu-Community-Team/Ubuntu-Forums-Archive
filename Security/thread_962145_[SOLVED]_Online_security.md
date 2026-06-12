---
title: "[SOLVED] Online security"
date: 2008-10-29
forum: Security
---

### Post by shiningkenmonster on 2008-10-29
I'm just wondering. I've read somewhere is that all you need to do is to just update the security software on ubuntu and you are just fine.

but how about the ubuntu firewall? I think i've read somewhere that the firewall is off by default.

btw, how do you run a proxy server on a ubuntu laptop?

---

### Post by drakeman007 on 2008-10-29
> **shiningkenmonster said:**
> I'm just wondering. I've read somewhere is that all you need to do is to just update the security software on ubuntu and you are just fine.

but how about the ubuntu firewall? I think i've read somewhere that the firewall is off by default.

btw, how do you run a proxy on a ubuntu laptop?

```

sudo ufw enable
```
to run uncomplicated firewall...

---

### Post by bodhi.zazen on 2008-10-29
Start with these threads :

[Ubuntu Security - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=510812") 

[[all variants] Intrusion Detection - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=919472") 


And what do you mean by a proxy exactly ?

---

### Post by shiningkenmonster on 2008-10-30
sorry, i had to re-edited that. and i've meant a proxy server.

is there a way to run an encrypted SSL wifi connection while surfing on a ubuntu laptop? free or paid.

btw, i have heard of an SSH. (Secure Shell) back in the year of 1997, when I had chatting buddies back in the EFnet, IRCnet, DALnet days.  but I have never done research and never had appiled in using it. How do you run a Secure Shell account? or is it the same as running an encrypted wifi connection?

---

### Post by hyper_ch on 2008-10-30
are you sure you need the firewall at all?

---

### Post by Gamma746 on 2008-10-30
> **shiningkenmonster said:**
> is there a way to run an encrypted SSL wifi connection while surfing on a ubuntu laptop? free or paid.

I'd suggest Tor.  See [https://help.ubuntu.com/community/TOR](https://help.ubuntu.com/community/TOR) for instructions.

---

### Post by kevdog on 2008-10-31
What do you want to do with SSH?  You can create encrypted point-to-point tunnels (with wired or wireless), however its not a substitute for wireless.

---

### Post by shiningkenmonster on 2008-10-31
Well, I want an encrypted connection because i will be using a laptop on public wifi connection.  From variety of different places too. Majority of time more public connections are unsecure. Sometimes it is usually not safe to surf or email certain things in public. I want my information to be kept private.

either way, without one. I would want to run on a proxy if I am using a peer to peer share program such as Limewire, eMule, etc.

I don't know if you notice. but when i've used Windows in the past and if you download something while using the p2p program. On windows,  if you open the command prompt. type in netstat or netstat -a 

You can see all the direct IP address that are connected with you. And those users who are uploading or downloading from you. - They directly have your IP addresses too. and Yes, people have done things to the system files. .. And routers/software firewalls don't help too. Cause you have to give permission to use the program. So it goes through the firewall. But i'm not sure if linux is more safer.

I would rather be safe use a proxy with a different IP address to be safe.

how do you run on a proxy on a ubuntu laptop?

---

### Post by kevdog on 2008-10-31
You can use something like squid for the proxy server.  How about you just get the secure tunnel setup first.

There are two ways to accomplish this:

1. Use ssh and tunnel your connections
2. Use a VPN - a product such as OpenVPN (all traffic goes through the tunnel)

SSH is easier, OpenVPN is more comprehensive.  You can also do both.

Here is a tutorial for the ssh method using tunneling firefox as an example:
[http://ubuntuforums.org/showthread.php?t=723025](http://ubuntuforums.org/showthread.php?t=723025)

---

