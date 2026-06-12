---
title: "SSH not safe?"
date: 2023-01-31
forum: Security
---

### Post by janarea on 2023-01-31
Hi, 

I am a new beginner and my plan is to establish secure SSH and disable root login on my Ubunto server. 

I followed this video and I am able to SSH into the server: 
[https://www.youtube.com/watch?v=bYfQbr7vPag&t=189s](https://www.youtube.com/watch?v=bYfQbr7vPag&t=189s)

To my big surprice I also tried from another PC and was also able to SSH into the server even if the private key was not  on the other PC?? I was asked for the password and after entering it I was in.. I tought it was not possible without a private key on the other computer? 

What am I missing? 

Best regard, J

---

### Post by janarea on 2023-01-31
I figured it out :)  Had to change following: [COLOR=#232629][FONT=ui-monospace]PasswordAuthentication no[/FONT][/COLOR]

---

### Post by DuckHook on 2023-01-31
Welcome to the forums janarea.

As you managed to figure out by yourself, security is an involved process and forms a deep area of study in and of itself. SSH must default to initially allow passwords. Otherwise, it is all too easy for beginners to lock themselves out of their own servers. If that server is located remotely, this would be very bad news.

In my experience, every security measure requires further research, understanding and tweaking. All use cases are unique and must be customized to the user's particular needs. Among Window's many faults, one of the biggest is the way it has conditioned people into treating security as a fire&#8209;and&#8209;forget tactic.

You appear to be on the right course.

Good Luck and Happy Ubuntu&#8209;ing!

---

### Post by TheFu on 2023-01-31
> **janarea said:**
> Hi, 

I am a new beginner and my plan is to establish secure SSH and disable root login on my Ubunto server. 

I followed this video and I am able to SSH into the server: 
[https://www.youtube.com/watch?v=bYfQbr7vPag&t=189s](https://www.youtube.com/watch?v=bYfQbr7vPag&t=189s)

To my big surprice I also tried from another PC and was also able to SSH into the server even if the private key was not  on the other PC?? I was asked for the password and after entering it I was in.. I tought it was not possible without a private key on the other computer? 

What am I missing? 

Best regard, J

There are 2 parts to an ssh-key.  
a) The private key
b) The public key
 NEVER, EVER, EVER, share the private key.  Use ssh-copy-id to handle pushing the public key to other systems where you'd like to use it.

The stock Ubuntu Server install doesn't allow remote access to root. If you are using an install that does, it is a bastardized install, not the standard.

Security seldom has "yes/no" answers.  It is almost always a scale based on what it is you are trying to accomplish and who any attackers are.  In general, ssh without passwords, is security, provided a sufficiently complex key was generated AND the private key has remained secure.  If you pushed the private key to a VPS, it is no longer secure and you should delete it and the paired public key from any remote systems. Start over.

Generating and pushing keys that are strong enough for almost anyone is just 2 commands, both run on the client system:
```
   $ ssh-keygen -t ed25519
   $ ssh-copy-id -i ~/.ssh/id_ed25519.pub username@remote

```
While you can use 4K or 8K RSA keys to get what is likely equivalent security, ed25519 provide similar levels of security. Since 2017, I've not used RSA-based keys, unless the remote system didn't support ed25519.  The openssh project team does a good job in having overlapping encryption methods for multiple years so nobody gets stuck with a client that cannot talk to a server.  I suppose an sshd server from 2005 might be a problem, but it also has at least 5 other critical remote access bugs.

In my sshd_config files, I limit the subnets that can use passwords for ssh credentials. Any where else and only ssh-keys can be used to authenticate.

Even with that protection, I use fail2ban to prevent too many brute force attempts. It will create a firewall rule when the configured limit is reached.  Why allow remote attackers unlimited attempts.  
Additionally, I limit the allowed number of retries over each 1-5 minute period to prevent remote systems from hammering the sshd too. This is also something handled by your Linux host firewall.   

These techniques are well-known and used almost universally by experienced admins.  There are a few others, like port knocking.  Looking at my sshd logs, I decided that port knocking wasn't necessary.  I have bigger issues to work that are filling logs with failed attack attempts ... effectively hiding a few "golden BB" attempts in all the other log garbage.  Many of the remote attacks were handled by moving nearly all company webapps off the internet and only allowing access after a user has already connected and authenticated to our VPN first.

---

### Post by oygle on 2023-02-11
Is this still an issue if UFW has a rule for LAN/SSH traffic only for a specific IP on the LAN and using port 22 ?

---

### Post by DuckHook on 2023-02-12
> **oygle said:**
> Is this still an issue if UFW has a rule for LAN/SSH traffic only for a specific IP on the LAN and using port 22 ?
Any time that you can lock your system down to using only one IP, you are better off. Port 22 is the default port though, so that offers a (minor) exposure.

Most of us don't have the luxury of just one IP. I often ssh into systems remotely from dynamic IP addresses that change from time to time, so highly restrictive firewalls won't work for me. TheFu mentions fail2ban for this reason.

Also, what do you mean by "Is this still an issue…"? If, by "this", you mean the OP's original problem about disabling passwords after defining keys, then I would say, "yes, it's still an issue". I don't believe in ever allowing passwords. Use keys at all times. Keys are a good habit. Passwords a bad one. We are creatures of habit, so always practice the good ones and refrain from the bad ones. However, if "this" means things like the hardened protocols, fail2ban and port knocking, then "no". Such ultra&#8209;hardening would be overkill in your case.

Make sure that your firewall is set up properly too. Just because you use UFW doesn't mean that it is configured properly. I've run into scenarios where a user has activated UFW, thought they were opening only a few ports, then found out that all ports were wide open *except* a few.

---

### Post by oygle on 2023-02-13
> **DuckHook said:**
> Any time that you can lock your system down to using only one IP, you are better off. Port 22 is the default port though, so that offers a (minor) exposure.

All the traffic is to be kept to the LAN only, so yes, just one IP.

> **DuckHook said:**
> Also, what do you mean by "Is this still an issue…"? If, by "this", you mean the OP's original problem about disabling passwords after defining keys, then I would say, "yes, it's still an issue". I don't believe in ever allowing passwords. Use keys at all times. Keys are a good habit. Passwords a bad one.

Okay thanks, I use passwords now, but will make the shift to keys.

> **DuckHook said:**
> Make sure that your firewall is set up properly too. Just because you use UFW doesn't mean that it is configured properly. I've run into scenarios where a user has activated UFW, thought they were opening only a few ports, then found out that all ports were wide open *except* a few.

Thanks for reminding me, I have:

```
sudo ufw status verbose
```

> Status: active
Logging: on (low)
Default: deny (incoming), allow (outgoing), deny (routed)
New profiles: skip

To                         Action      From
--                         ------      ----
22/tcp                     ALLOW IN    192.168.20.3              
3702/udp (wsdd)            ALLOW IN    Anywhere                  
5357/tcp (wsdd)            ALLOW IN    Anywhere                  
137,138/udp (Samba)        ALLOW IN    Anywhere                  
139,445/tcp (Samba)        ALLOW IN    Anywhere                  
3702/udp (wsdd (v6))       ALLOW IN    Anywhere (v6)             
5357/tcp (wsdd (v6))       ALLOW IN    Anywhere (v6)             
137,138/udp (Samba (v6))   ALLOW IN    Anywhere (v6)             
139,445/tcp (Samba (v6))   ALLOW IN    Anywhere (v6)


and only need any ALLOW for 192.168.20.3, so will have to change that now.

..Later .. have added some rules and deleted some

```
sudo ufw allow from 192.168.20.3 to any app Samba
sudo ufw allow from 192.168.20.3 to any app wsdd
```

I know how to delete the bottom 4 rules, but how do I add for the "V6" types ?

```
sudo ufw status verbose
```

> Status: active
Logging: on (low)
Default: deny (incoming), allow (outgoing), deny (routed)
New profiles: skip

To                         Action      From
--                         ------      ----
22/tcp                     ALLOW IN    192.168.20.3              
137,138/udp (Samba)        ALLOW IN    192.168.20.3              
139,445/tcp (Samba)        ALLOW IN    192.168.20.3              
3702/udp (wsdd)            ALLOW IN    192.168.20.3              
5357/tcp (wsdd)            ALLOW IN    192.168.20.3              
3702/udp (wsdd (v6))       ALLOW IN    Anywhere (v6)             
5357/tcp (wsdd (v6))       ALLOW IN    Anywhere (v6)             
137,138/udp (Samba (v6))   ALLOW IN    Anywhere (v6)             
139,445/tcp (Samba (v6))   ALLOW IN    Anywhere (v6)

---

### Post by oygle on 2023-02-13
Have done some searching to find out what the "V6" means and no definite answers, so just keeping it simple for now.

```
sudo ufw status verbose
```

> Status: active
Logging: on (low)
Default: deny (incoming), allow (outgoing), deny (routed)
New profiles: skip

To                         Action      From
--                         ------      ----
22/tcp                     ALLOW IN    192.168.20.3              
137,138/udp (Samba)        ALLOW IN    192.168.20.3              
139,445/tcp (Samba)        ALLOW IN    192.168.20.3              
3702/udp (wsdd)            ALLOW IN    192.168.20.3              
5357/tcp (wsdd)            ALLOW IN    192.168.20.3 

---

### Post by DuckHook on 2023-02-13
v6 refers to IPv6. Very involved topic. [Wikipedia provides a good overview]("https://en.wikipedia.org/wiki/IPv6"), but you now probably know exactly what it is anyway.

---

### Post by oygle on 2023-02-13
> **DuckHook said:**
> v6 refers to IPv6. Very involved topic. [Wikipedia provides a good overview]("https://en.wikipedia.org/wiki/IPv6"), but you now probably know exactly what it is anyway.

Thanks, it seems I don't need it, as the Samba sharing works fine without the firewall rules for "V6". An interesting tests at [https://ipv6-test.samba.org/](https://ipv6-test.samba.org/) and [https://test-ipv6.com/](https://test-ipv6.com/)

---

### Post by DuckHook on 2023-02-13
I'm waiting for the security gurus to jump in here, but a properly configured firewall will also have restrictions on outgoing packets. A word of caution: while this hardens your install even more, it does have a tendency to break your system because we all tend to be more permissive in our outgoing behaviour. For example, you might install an app in the future that uses a high port, forget that your firewall is hardened against outgoing packets and spend hours of frustration trying to figure out why your new app "doesn't work". This happened to me recently on a KODI install. The upside is that a rogue app that tries to call back to mothership won't be able to do so either.

Re: IPv6

If you don't use it at all, then you should turn it off entirely. The problem with ignoring firewall rules for IPv6 is that devices may automatically resort to it if you don't set those rules. More and more IoT devices are using only IPv6 addresses. If that happens, then you will have a hole in your firewall that you are not even aware of.

---

### Post by oygle on 2023-02-13
> **DuckHook said:**
> I'm waiting for the security gurus to jump in here, but a properly configured firewall will also have restrictions on outgoing packets.

The rules are now down to only IP specific

```
sudo ufw status verbose
```

> Status: active
Logging: on (low)
Default: deny (incoming), allow (outgoing), deny (routed)
New profiles: skip

To                         Action      From
--                         ------      ----
137,138/udp (Samba)        ALLOW IN    192.168.20.3              
139,445/tcp (Samba)        ALLOW IN    192.168.20.3              
3702/udp (wsdd)            ALLOW IN    192.168.20.3              
5357/tcp (wsdd)            ALLOW IN    192.168.20.3

I removed the "V6" rules.

> **DuckHook said:**
> Re: IPv6

If you don't use it at all, then you should turn it off entirely. The problem with ignoring firewall rules for IPv6 is that devices may automatically resort to it if you don't set those rules. More and more IoT devices are using only IPv6 addresses. If that happens, then you will have a hole in your firewall that you are not even aware of.

It looks like it is disabled for me. I used [https://www.golinuxcloud.com/linux-check-ipv6-enabled/](https://www.golinuxcloud.com/linux-check-ipv6-enabled/) , then

```
cat /sys/module/ipv6/parameters/disable
```

> 0

Found an IPV6 test at [https://ipv6-test.samba.org/](https://ipv6-test.samba.org/) , which also mentions another test at [https://test-ipv6.com/](https://test-ipv6.com/)

---

### Post by DuckHook on 2023-02-13
[LIST=1]
[*]Your IPv6 is enabled. That's what the 0 (zero) signifies.
[*]You have opened those four ports for incoming traffic. All other incoming is denied. But all outgoing is still allowed. Hence, a rogue app can still phone home since it will be initiating an outgoing connection.
[*]It's your decision whether you want to deny outgoing. If you do, then you need to open specific ports if you want your computer to work (just like you did for incoming). However, determining which outgoing ports to open is more complicated than determining for incoming. It requires a deep dive into what services you are running and what ports they use. Often, the information is obscure and hard to uncover because devs assume the default state where all outgoing ports are open, so most don't bother to document their port use very well.
[/LIST]

---

### Post by oygle on 2023-02-13
> **DuckHook said:**
> Your IPv6 is enabled. That's what the 0 (zero) signifies.

Oh yes, you are correct, thanks.

> **DuckHook said:**
> You have opened those four ports for incoming traffic. All other incoming is denied. But all outgoing is still allowed. Hence, a rogue app can still phone home since it will be initiating an outgoing connection.

On the surface, all I use any connection for is Claws-mail, beyond Compare and Firefox. Meaning that is all that is installed that is traffic "out". There is a samba server but that is for LAN use only.

> **DuckHook said:**
> It's your decision whether you want to deny outgoing. If you do, then you need to open specific ports if you want your computer to work (just like you did for incoming). However, determining which outgoing ports to open is more complicated than determining for incoming. It requires a deep dive into what services you are running and what ports they use. Often, the information is obscure and hard to uncover because devs assume the default state where all outgoing ports are open, so most don't bother to document their port use very well.


Yes, I just did a quick port test of the ones listening only

```
sudo lsof -i -P -n | grep LISTEN
```

and there were systemd-resolve, cupsd, python3/wsdd, dnsmasq/libvirt-dnsmasq, kdeconnect, smbd. Some had 2 entries, one for IPv4 and one for IPv6

---

