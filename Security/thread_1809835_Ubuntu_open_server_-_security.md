---
title: "Ubuntu open server - security"
date: 2011-07-22
forum: Security
---

### Post by cavemaneca on 2011-07-22
Hello there, I'm kinda new to Linux... really I've only had experience with it for a few months.

Anyway, I've recently been running a game server from my desktop, as well as a web page to accompany it.
I use the ports 80/8123(HTTP)/5900(VNC)/50500(GAME)/5839(ADMINISTRATION).

What's the best solution to protect my server from security threats? 

On a side note, I plan on adding a MySQL server later, but I want to keep it local only.

---

### Post by nevius on 2011-07-22
Don't use VNC. Administer the server via ssh. Use x11 forwarding if you need a GUI. Consider setting up a dedicated box as your game / http server. That way if the server is compromised it presumably won't contain any valuable data.

---

### Post by cavemaneca on 2011-07-22
Okay, that's nice to know, but what about security? I'm pretty sure by default if I just DMZ my computer it's gonna have poor security. What do I need to do to actually make it safer? Switching from VNC helps NOTHING if every other port is not secured, which I know don't know anything about on linux.

---

### Post by bodhi.zazen on 2011-07-22
If you are allowing public access , what is there to firewall ?

You need to secure each service, apache, VNC, and whatever game you are running.

---

### Post by Dangertux on 2011-07-22
As has been stated VNC really shouldn't be exposed, or even used IMO. There are many other alternatives X11 forwarding was given, and is a smart choice if you need a GUI.

I also agree that if you allow public access to a service a firewall is somewhat more irrelevant. (Granted it can still give you some benefit if configured properly)

Also what do you mean by every port being secured? This is a result of myths propegated by site's like Shields Up, don't get me wrong Steve Gibson has some good stuff to say particularly in the Windows world. However, those types of sites give the wrong impression to newer users.

A port isn't what is vulnerable, think of a port as a doorway. The service running there, the door. The hardening measures of the service the lock/security system on the door. 

Also don't get too hung up on that analogy it's still not even the best, because if there is no service running there, there is neither a door nor a doorway, not an empty portal into your computer as a doorway would be with no door.

Opened or Closed ports mean nothing by themselves.

---

### Post by bodhi.zazen on 2011-07-22
> **Dangertux said:**
> Also what do you mean by every port being secured? This is a result of myths propegated by site's like Shields Up, don't get me wrong Steve Gibson has some good stuff to say particularly in the Windows world. However, those types of sites give the wrong impression to newer users.

+100 

Worse , Steve's site does not use "proper" terminology or explain the difference between an open and closed port.

Proper - open, closed, reject

Steve - open, closed, stealth

There is no such thing as "stealth" , you are not somehow invisible because you drop all incoming packets.

Try it for yourself, 

```
sudo ufw disable
sudo iptables -X
sudo iptables -F
sudo iptables INPUT -j DROP
```

Now scan that box with nmap, you will still see it even all ports are "stealthed".

Worse connect to the internet with a browser like firefox and you light up like a Christmas tree. Connect to my server and I know who you are.

[https://panopticlick.eff.org/](https://panopticlick.eff.org/)

---

### Post by cavemaneca on 2011-07-22
Okay, maybe I should write this out a little better.
By default, are all of the ports that use things like ftp and telnet and whatnot, secured so that they either reject or are closed?
Second, if I am using the port 5839 as a game specific application for administrating the game server, is it likely to pose a security threat?
Third, are the default settings in Ubuntu sufficient to block normal hacking attempts? Do I need to use a firewall or iptables or anything?

And last, while I will follow your recommendations for switching from VNC, for future reference, what is the issue with VNC and why should it be avoided? What is a situation where it is "safe" to use VNC?

---

### Post by Thewhistlingwind on 2011-07-22
> **Dangertux said:**
> 

A port isn't what is vulnerable, think of a port as a doorway. The service running there, the door. The hardening measures of the service the lock/security system on the door. 

Also don't get too hung up on that analogy it's still not even the best, because if there is no service running there, there is neither a door nor a doorway, not an empty portal into your computer as a doorway would be with no door.



I use the analogy of a wall socket, because as far as I can tell, thats the analogy that sockets are named after anyway.

---

### Post by bodhi.zazen on 2011-07-22
> **cavemaneca said:**
> Okay, maybe I should write this out a little better.
By default, are all of the ports that use things like ftp and telnet and whatnot, secured so that they either reject or are closed?

Depends on what you mean by "secured". By default there is no ftp server installed, so the port is closed.

If you install a ftp server, and do not start it, the port is still closed.

If you then start the server the port will be wide open, the default firewall rules allow all traffic.

The ftp server code is secure on the server, but anyone with a packet sniffer can read you login and password as ftp is an insecure protocol.

So you have to secure ftp, vsftp, firewall it, fail2ban, scp, sftp, etc ...

Bu default, home directories are open, is this secure ?

See: 

[https://wiki.ubuntu.com/SecurityTeam/Policies](https://wiki.ubuntu.com/SecurityTeam/Policies)
[https://wiki.ubuntu.com/SecurityTeam/FAQ](https://wiki.ubuntu.com/SecurityTeam/FAQ)
[https://wiki.ubuntu.com/ZeroConfPolicySpec](https://wiki.ubuntu.com/ZeroConfPolicySpec)

As well as the security sticky.

> Second, if I am using the port 5839 as a game specific application for administrating the game server, is it likely to pose a security threat?

I do not know, depends on the game and what security is built into it. If it is not in the Ubuntu repositories we do not support it here, you would have to ask the people who made the game.

Without any further details I am going to say yes it is a security risk.

> Third, are the default settings in Ubuntu sufficient to block normal hacking attempts? Do I need to use a firewall or iptables or anything?

Depends on how good the hacker is. Ubuntu OS are not invulnerable. The most common intrusions result from weak passwords and VNC servers.

> And last, while I will follow your recommendations for switching from VNC, for future reference, what is the issue with VNC and why should it be avoided? What is a situation where it is "safe" to use VNC?

VNC does not encrypt the network traffic, so, anyone with a packet sniffer can see your passwords and traffic. So when you log into the vnc server we can read your password.

---

### Post by cavemaneca on 2011-07-23
> VNC does not encrypt the network traffic, so, anyone with a packet sniffer can see your passwords and traffic. So when you log into the vnc server we can read your password.


That's understandable. I can see now why VNC would ONLY be used in a closed network...

So, essentially x11 can run similar to VNC, but with encrypted traffic?

---

### Post by bodhi.zazen on 2011-07-23
> **cavemaneca said:**
> That's understandable. I can see now why VNC would ONLY be used in a closed network...

So, essentially x11 can run similar to VNC, but with encrypted traffic?

No not x11vncserver , you need to tunnel your VNC over ssh or, better, use FreeNX (FreeNX is faster).

---

### Post by Dangertux on 2011-07-23
I haven't googled this yet because I am on my phone. But if someone has it handy they should link an article that explains the difference between server hardening and firewalling. 

But the short version is basically this. A firewall is essentially used to block unwanted connections. On a system running no services you will not want connections. Thus a firewall is a good solution. 

However when you run public services you have to have those services accepting connections. So you can't just block them with a firewall. This is where hardening comes in. Since to be accessible you service has to be exposed you want to limit what can happen. IE: you want to make sure that your passwords are not transmitted clear text, you want to ensure vulnerabilities in the services are patched, that services are properly confined with apparmor or selinux, that they are not vulnerable to brute force attacks, and there many other measures that can be taken. 

There are exceptions to the above concept ie: deep packet inspection firewalls. This is a more advanced topic and probably not something you're going to want to delve into right away.

---

