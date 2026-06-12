---
title: "SSHD brute force failures in logs"
date: 2010-10-13
forum: Security
---

### Post by smeggs on 2010-10-13
Hey, I'm new here and am wondering just how secure my SSHD is because I'm getting a lot of what appears to be brute force password attempts from the same IP address. Here's a sample of the log file I viewed today:

```
Oct 13 13:26:43 klendathu sshd[5402]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=s15357532.onlinehome-server.com  user=root
Oct  13 13:26:45 klendathu sshd[5402]: Failed password for root from 74.208.105.220 port 56861 ssh2
Oct  13 13:26:45 klendathu sshd[5405]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=s15357532.onlinehome-server.com  user=root
Oct  13 13:26:47 klendathu sshd[5405]: Failed password for root from 74.208.105.220 port 57518 ssh2
Oct  13 13:26:47 klendathu sshd[5407]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=s15357532.onlinehome-server.com  user=root
Oct  13 13:26:50 klendathu sshd[5407]: Failed password for root from 74.208.105.220 port 57692 ssh2
```

There's a very long stream of these, trying different account names after root obviously failed. They all failed, but I'm hoping that my choice of settings for SSH are good enough. I'm using a port higher than 22, in fact out of the range of 1024. 

ServerKeyBits is 768, I don't allow root logins, Ubuntu's default settings concerning the root account are intact. I also only allow two users access. Now as far as brute force attacks are concerned, I know I'm good, it would take entirely too long to get in that way. I guess I'm more concerned with finding out who this is. When I nmapped the source IP address, I noticed it had some very common services associated with servers, including http. So, I checked and it appears to be a price quote site concerning airlines out of europe? Fun stuff.

Or Geneva International Airport. Cool.

---

### Post by smeggs on 2010-10-13
There's even more, I just found them. Here's an example:


```
Address 178.54.16.19 maps to unallocated.sta.synapse.net.ua, but this does not map back to the address - POSSIBLE BREAK-IN ATTEMPT!
```

```
Oct  3 17:39:20 klendathu sshd[9590]: reverse mapping checking getaddrinfo for unallocated.sta.synapse.net.ua [178.54.16.19] failed - POSSIBLE BREAK-IN ATTEMPT!
Oct  3 17:39:20 klendathu sshd[9590]: Invalid user ftp from 178.54.16.19
Oct  3 17:39:20 klendathu sshd[9590]: pam_unix(sshd:auth): check pass; user unknown
Oct  3 17:39:20 klendathu sshd[9590]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=178.54.16.19 
Oct  3 17:39:22 klendathu sshd[9590]: Failed password for invalid user ftp from 178.54.16.19 port 38473 ssh2
```

There's also a giant pile of these. I really need to check my logs more often.

---

### Post by CharlesA on 2010-10-13
You'll get those whenever ssh is allowed open access to the internet. They are just attacks that are run via scripts that scan a specific block of ip addresses for open ports.

It's good that you are looking at logs, but they can make you a bit paranoid tbh.

On one box I have exposed to the internet, the auth.log is a bit "full" of failed access attempts:

```
Oct 13 01:05:30 atlantis sshd[3017]: User root from 60.13.129.139 not allowed because not listed in AllowUsers
Oct 13 01:05:37 atlantis sshd[3021]: User root from 60.13.129.139 not allowed because not listed in AllowUsers
Oct 13 01:05:40 atlantis sshd[3023]: User root from 60.13.129.139 not allowed because not listed in AllowUsers
Oct 13 09:34:26 atlantis sshd[3291]: User root from 211.100.62.155 not allowed because not listed in AllowUsers
Oct 13 09:34:27 atlantis sshd[3294]: User root from 211.100.62.155 not allowed because not listed in AllowUsers
Oct 13 09:34:29 atlantis sshd[3296]: User root from 211.100.62.155 not allowed because not listed in AllowUsers
Oct 13 10:55:43 atlantis sshd[3304]: User root from 211.100.62.155 not allowed because not listed in AllowUsers
Oct 13 10:55:45 atlantis sshd[3307]: User root from 211.100.62.155 not allowed because not listed in AllowUsers
Oct 13 10:55:46 atlantis sshd[3310]: User root from 211.100.62.155 not allowed because not listed in AllowUsers
Oct 13 14:55:42 atlantis sshd[3332]: reverse mapping checking getaddrinfo for 222-237-78-139.tongkni.co.kr [222.237.78.139] failed - POSSIBLE BREAK-IN ATTEMPT!
Oct 13 14:55:42 atlantis sshd[3332]: User root from 222.237.78.139 not allowed because not listed in AllowUsers
Oct 13 14:55:43 atlantis sshd[3335]: reverse mapping checking getaddrinfo for 222-237-78-139.tongkni.co.kr [222.237.78.139] failed - POSSIBLE BREAK-IN ATTEMPT!
Oct 13 14:55:43 atlantis sshd[3335]: Invalid user teamspeak from 222.237.78.139
Oct 13 14:55:45 atlantis sshd[3337]: reverse mapping checking getaddrinfo for 222-237-78-139.tongkni.co.kr [222.237.78.139] failed - POSSIBLE BREAK-IN ATTEMPT!
Oct 13 14:55:45 atlantis sshd[3337]: User root from 222.237.78.139 not allowed because not listed in AllowUsers
```

Anyway, the "reverse mapping" message means that that hostname didn't resolve to a known ip address using a reverse dns lookup.

As long as the attempts fail you are ok.

Also: How have you secured SSH? Are you allowing password logins or using only keys?

---

### Post by FuturePilot on 2010-10-14
1. Use keys, disable password auth completely.
2. Use denyhosts or fail2ban.

---

### Post by rookcifer on 2010-10-14
> **FuturePilot said:**
> 1. **Use keys, disable password auth completely.**
2. Use denyhosts or fail2ban.

^^ This

---

### Post by smeggs on 2010-10-14
I've disabled password logins, I'm using only keys, and the keys are 2048 bits. Also, I only allow two accounts access to SSH.
 
 
Charles, I'm also noticing yours says "Not allowed because not in AllowHosts". Mine doesn't mention that, even though I have that enabled. Also, root logins aren't permitted, but the root attempts still say authentication failure. Is there something wrong?

---

### Post by CharlesA on 2010-10-14
Nah, that's fine. The root account exists, but it's not active, so it'll fail to authenticate.

I've got the "AllowedUsers" set in sshd_config, which is why it says it's not in AllowUsers

```
# If specified, login is allowed only for user names that match one of
# the patterns.  Only user names are valid; a numerical user ID is
# not recognized.
[COLOR="Navy"]AllowUsers charles[/COLOR]

```

---

### Post by Velnias on 2010-10-14
Sleep well - sshd, with only keys login, is pretty safe:

[http://www.openssh.com/users.html](http://www.openssh.com/users.html)

---

### Post by smeggs on 2010-10-14
> **CharlesA said:**
> Nah, that's fine. The root account exists, but it's not active, so it'll fail to authenticate.
 
I've got the "AllowedUsers" set in sshd_config, which is why it says it's not in AllowUsers
 
```
# If specified, login is allowed only for user names that match one of
# the patterns.  Only user names are valid; a numerical user ID is
# not recognized.
[COLOR=navy]AllowUsers charles[/COLOR]

```
 
 
I've got this enabled as well, that's why I ask.

---

### Post by CharlesA on 2010-10-14
Hrm. Do you have the root account enabled, or is it still locked?

I commented out that option in sshd_config and it didn't record anything in auth.log. With it enabled it showed something. *shrugs*

---

### Post by HermanAB on 2010-10-15
Howdy,

Edit /etc/ssh/sshd_config and change Port 22 to  Port 5555 or some such and restart sshd.  Then the script kiddies won't find you.

---

### Post by MechaMechanism on 2010-10-15
Changing port 22 to another port does nothing for security.  Crackers nowadays can use scripts that run in parallel to check a wide range of ports for SSH.  If your vulnerable on 22 then your vulnerable on all other ports as well.  Frankly if your changing SSH port from 22 to another, for increased security, then your security has already failed.  At best it simply reduces log clutter and thats not a good enough reason to change ports.

Use keys for best security.  Use RSA with a key strength of 8192, the additional time required to generate a new key is worth it as the subsequent use of key imposes very little overhead on modern machines.

---

### Post by perspectoff on 2010-10-15
> **MechaMechanism said:**
> Changing port 22 to another port does nothing for security.  Crackers nowadays can use scripts that run in parallel to check a wide range of ports for SSH.  If your vulnerable on 22 then your vulnerable on all other ports as well.  Frankly if your changing SSH port from 22 to another, for increased security, then your security has already failed.  At best it simply reduces log clutter and thats not a good enough reason to change ports.

Use keys for best security.  Use RSA with a key strength of 8192, the additional time required to generate a new key is worth it as the subsequent use of key imposes very little overhead on modern machines.

True, which is why I recommend knockd to hide the ports. Only a specific sequence of port requests opens up the hidden SSH port.

A great tool.

---

### Post by perspectoff on 2010-10-15
> **MechaMechanism said:**
>   Frankly if your changing SSH port from 22 to another, for increased security, then your security has already failed.  At best it simply reduces log clutter and thats not a good enough reason to change ports.

Use keys for best security.  Use RSA with a key strength of 8192, the additional time required to generate a new key is worth it as the subsequent use of key imposes very little overhead on modern machines.

Nonsense. Changing the SSH port does not imply failed security.

Further, logs take time to write to and take up disk space. Anything that minimizes this is worthwhile.

This is a subtle DoS attack and slows the computer, albeit imperceptibly. In aggregate, though, such attacks can be substantial to slowing the efficiency of a server.

It takes a lot of effort for attackers to scan all the ports of every computer. It is inefficient, and while some do that, most attackers primarily scan the known standard ports in the name of speed (unless they have a specific attack goal).

I also advocate disallowing password SSH authentication and using only key-based authentication, merely because it is very difficult to crack multi-bit keys by brute force

---

### Post by MechaMechanism on 2010-10-15
> **perspectoff said:**
> It takes a lot of effort for attackers to scan all the ports of every computer.
Which is why I said " Crackers nowadays can use scripts that run in parallel to check a wide range of ports for SSH"

Meaning a script kiddie can use multiple compromised computers to split the port scanning among them.  some machines scan you at the lower range while other machines scan you at other ranges.  Hence the massive speed up in port scanning.  I'm not saying it happens a lot or hardly ever, I'm just saying parallel scanning will be very fast.  Unless I'm misunderstanding networking, if so correct me please.

---

### Post by Kinstonian on 2010-10-15
> **MechaMechanism said:**
> Which is why I said " Crackers nowadays can use scripts that run in parallel to check a wide range of ports for SSH"

Meaning a script kiddie can use multiple compromised computers to split the port scanning among them.  some machines scan you at the lower range while other machines scan you at other ranges.  Hence the massive speed up in port scanning.  I'm not saying it happens a lot or hardly ever, I'm just saying parallel scanning will be very fast.  Unless I'm misunderstanding networking, if so correct me please.

You're right in that distributed scans are lot faster, however as you suggested, it is also a lot more rare.  It's not uncommon for people to be bombarded with things like SSH password guessing attacks and then change the port and not have any for a very long time.

As long as you aren't relying on one security measure like changing the port, there isn't a problem with security through obscurity.  I'm willing to bet all the people who say security through obscurity is worthless wouldn't feel the same way if they were in a military vehicle that wasn't camouflaged during war.

---

### Post by bodhi.zazen on 2010-10-15
See also : 

[http://bodhizazen.net/Tutorials/ssh_security](http://bodhizazen.net/Tutorials/ssh_security)

---

### Post by CharlesA on 2010-10-15
Did some testing (root account is not enabled):

PermitRootLogin = yes and password authentication enabled:

```
Oct 15 16:43:21 luna sshd[754]: Failed password for root from 192.168.1.30 port 41103 ssh2
```

PermitRootLogin = no and password authentication enabled:

```
Oct 15 16:44:39 luna sshd[780]: Failed password for root from 192.168.1.30 port 41105 ssh2
```


PermitRootLogin = no and AllowUsers not allowing root and password authentication enabled:

```
Oct 15 16:49:31 luna sshd[914]: User root from atlantis.asgard.lcl not allowed because not listed in AllowUsers
Oct 15 16:49:31 luna sshd[914]: Failed none for invalid user root from 192.168.1.30 port 40763 ssh2
Oct 15 16:49:31 luna sshd[914]: Failed password for invalid user root from 192.168.1.30 port 40763 ssh2
```

PermitRootLogin = no and Allow users not allowing root and With key auth:

```
Oct 15 16:51:52 luna sshd[928]: User root from atlantis.asgard.lcl not allowed because not listed in AllowUsers
```

I found that if the user wasn't listed in AllowUsers or if it was commented out, nothing was written to the auth.log if you were using only keys. *shrug*

Using keys is the best way to go.

---

### Post by annoyingrob on 2010-10-15
I used to have some iptables rules set up where if someone tried to SSH into my server more than 3 times within a minute, it would ban the IP address for a period of time (like 10 minutes or an hour). I don't have them written down in front of me, but you can easily google it. It's like 2 rules, really simple to pull off. Cut down the logs huge. 

The only problem was if I was really overzealous at work with my connections, I would lock myself out :)

---

### Post by CharlesA on 2010-10-15
> **annoyingrob said:**
> I used to have some iptables rules set up where if someone tried to SSH into my server more than 3 times within a minute, it would ban the IP address for a period of time (like 10 minutes or an hour). I don't have them written down in front of me, but you can easily google it. It's like 2 rules, really simple to pull off. Cut down the logs huge. 

The only problem was if I was really overzealous at work with my connections, I would lock myself out :)

It's probably the same one I've been using:

```
# 10 minute lockout if trying to bruteforce
-A INPUT -p tcp --dport 22 -m state --state NEW -m recent --set --name  SSH --rsource
-A INPUT -m recent --update --seconds 600 --hitcount 4 --rttl --name SSH  --rsource -j DROP
-A INPUT -p tcp -m tcp --dport 22 -j ACCEPT

```

Throw it in a file and apply it with iptables-restore.

---

### Post by annoyingrob on 2010-10-15
Yup, that looks pretty similar to me!

---

### Post by msandoy on 2010-10-16
There are more than one reason for changing from the default port 22.
> **MechaMechanism said:**
> Changing port 22 to another port does nothing for security.  Crackers nowadays can use scripts that run in parallel to check a wide range of ports for SSH.  If your vulnerable on 22 then your vulnerable on all other ports as well.  Frankly if your changing SSH port from 22 to another, for increased security, then your security has already failed.  At best it simply reduces log clutter and thats not a good enough reason to change ports.

Use keys for best security.  Use RSA with a key strength of 8192, the additional time required to generate a new key is worth it as the subsequent use of key imposes very little overhead on modern machines.

I do not have more than a simple SHDSL line in to my house, but I have my server up with SSH. When I had it on port 22, there used to be heavy attacks on it, some of those bots are really stupid, even after they have been banned, they still continue attacking with hundreds of attempts per second.
Have you ever tried to do FPS gaming on a connection under attack? It's to say the least a frustrating experience.
Even surfing the nett is sloved down to a crawl during those attacks. My server has never been compromised, but after changing away from port 22, the time spent going trough logs, and frustration over slow connection has drastically reduced.

---

### Post by smeggs on 2010-10-20
> **CharlesA said:**
> Did some testing (root account is not enabled):

PermitRootLogin = yes and password authentication enabled:

```
Oct 15 16:43:21 luna sshd[754]: Failed password for root from 192.168.1.30 port 41103 ssh2
```PermitRootLogin = no and password authentication enabled:

```
Oct 15 16:44:39 luna sshd[780]: Failed password for root from 192.168.1.30 port 41105 ssh2
```
PermitRootLogin = no and AllowUsers not allowing root and password authentication enabled:

```
Oct 15 16:49:31 luna sshd[914]: User root from atlantis.asgard.lcl not allowed because not listed in AllowUsers
Oct 15 16:49:31 luna sshd[914]: Failed none for invalid user root from 192.168.1.30 port 40763 ssh2
Oct 15 16:49:31 luna sshd[914]: Failed password for invalid user root from 192.168.1.30 port 40763 ssh2
```PermitRootLogin = no and Allow users not allowing root and With key auth:

```
Oct 15 16:51:52 luna sshd[928]: User root from atlantis.asgard.lcl not allowed because not listed in AllowUsers
```I found that if the user wasn't listed in AllowUsers or if it was commented out, nothing was written to the auth.log if you were using only keys. *shrug*

Using keys is the best way to go.

Hey, that makes sense. Thanks for all of your replies, I'm a little more at ease and I've found some new ways to secure my SSHD. Thanks a lot everyone. :D

---

