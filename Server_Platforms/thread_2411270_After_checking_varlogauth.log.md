---
title: "After checking /var/log/auth.log"
date: 2019-01-28
forum: Server Platforms
---

### Post by lowergroundfloor on 2019-01-28
I went to log into my server this morning VNC and was met with "Connection failed - too many security failures". I had to ssh to the server, kill vnc and start it again in order to let myself in. 

When I got in... the terminal with the program I was running had disappeared which is terrifying. It reinforces the fear that somebody has breached the server.

Having typed "/var/log/auth.log" into the terminal, logs only go back 8 hours unfortunately. It appears that my server has constantly been receiving log in attempts. 

1) This is perhaps what has triggered VNC into locking me out. But why all of a sudden is VNC acting up? Is normal to have so many log in attempts? Are they usually so disruptive?

2) If its not normal, I was tinkering several days ago and allowed http on firewall. Is this likely to be why this has occurred?

3) How the hell could these windows disappeared? If there was an error or even a DDoS, I would expect the script to stop but the terminal to remain. It's as if there was a reboot - how can I check when the last reboot was? 

Granted I'm only beginner. If you could recommend whatever steps that are most sensible in this situation. I can't really gauge the extent of the security risk at the moment. 

Kind regards,
J

---

### Post by TheFu on 2019-01-28
Don't allow vnc/rdp over the internet.  Only allow it from localhost and use an ssh-tunnel to gain local access.

Or better, learn to manage the systems using ssh only.

Also, for ssh security, use fail2ban to block constant brute force attacks. It is also easy to change the default port that ssh uses to something weird - say 61922.  Anything high will keep the logs much cleaner.  Do both - change the default port and install/configure fail2ban.

And don't allow VNC or RDP connections from the internet. Please.

---

### Post by 1clue on 2019-01-28
+1 for ssh-only, for a lot of reasons.

Servers have no use for a GUI. It's a lot of extra software on a system which will never need that software. 
Most servers these days are a VM, which means all that extra disk space and RAM can be used for other VMs.
Software (all software) has bugs. Some of those bugs are security issues. Less software means less possible security holes.
Every remote desktop style protocol takes a huge amount of bandwidth when compared to a stream of encrypted text like you have with ssh.

---

### Post by 1clue on 2019-01-28
About ports open on the Internet.

RDP and VNC can be secured but aren't always secured. They get a LOT of attention from automated software on the Internet which tries to break in. As they are not needed, you should not even have the software available on your server.

SSH also gets a lot of attention from that automated software, and you will certainly get a ton of people trying to brute force your system (guessing users and passwords) from all over the world. 

fail2ban helps reduce the number of tries a remote system can try per minute, but really is just a tool to slow down the attacks, not secure you from them. Good passwords are critical, and prevent root login from remote terminal always.

Changing the port (obfuscation) does actually reduce the automated attacks in the logs, but once somebody figures out you have a port open for anything up high, they will probe it and very possibly do so from many remote hosts, so you're back to brute force techniques. Don't rely on obfuscation to be your entire security plan. You STILL need to have a secure system no matter what. Many organizations refuse to obfuscate simply because it gives a false sense of security, making people think they are not at risk.

---

### Post by TheFu on 2019-01-28
+1 on obfuscation not being security, but the difference between 10,000 attempts a day and zero make it worth the hassle.

Using passwords over the internet for ssh is a problem.  We don't allow password authentication outside our admin LANs subnet. Blocking all passwords except for specific subnets is configurable in the sshd_config.  For example:
```
PasswordAuthentication no
Match Address 172.22.22.0/24,172.21.22.0/24
      PasswordAuthentication yes

```

---

### Post by 1clue on 2019-01-29
A lot of the brute force attacks you get in the logs are coordinated. This is a direct result of fail2ban IMO. Fail2ban keeps track of who's trying and if you try too often from the same source it blocks that IP. So the better black hat guys will attack from multiple IPs. 

When you change the port you will see much less traffic in auth.log but once you're discovered you will likely see many IP addresses probing all at once, and the number will likely grow as time passes. So you're no more secure for obfuscating. And changing the port yet again is nothing, because now they know that you obfuscated once and they will scan again for some other high port.

TheFu's suggestion of limiting the source address makes sense if that's possible, but in my case the people logging in are coming from home, and don't always have the same IP or even the same block. Complicated even further by sometimes working from a coffee shop or another company's network. 

I recommend requiring a key for login without a VPN, or better yet just don't allow ssh without a VPN.

---

