---
title: "Unable to connect via ssh after upgrade to Edgy from Dapper"
date: 2006-11-07
forum: Server Platforms
---

### Post by nate66s on 2006-11-07
I upgraded to Edgy form Dapper last week.  There were a few problems, but everything appears to be working now, except for sshd.  I had set up sshd on Dapper and had no problems connecting my machine.  After upgrading, however, I cannot connect to the machine at all.  A few notes:

[LIST]
[*]I get this error: ```
ssh: connect to host x.x.x.x port 22: No route to host
```
[*]sshd is definitely running (checked with ps ax | grep sshd)
[*]I can connect via ssh locally.
[*]There are no iptables rules that could be blocking traffic.  Output from iptables -L: ```
Chain INPUT (policy ACCEPT)
target     prot opt source               destination         

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination      
```
[*]Output from netstat -putan: ```
tcp        0      0 0.0.0.0:22              0.0.0.0:*               LISTEN     11044/sshd
```
[/LIST]

Any help would be very much appreciated.

---

### Post by nate66s on 2006-11-08
Anyone?  Perhaps I should submit this as a bug?

---

### Post by nixfaced on 2006-11-09
Just a thought -- double check and make sure your server's IP address is what you think it is, and that you've got basic connectivity from the server, and that you can connect to other services running on that machine from elsewhere on your LAN.  I realize it's probably a silly suggestion, but I've overlooked stuff like that before, and I only mention it because that info wasn't stated in your post.  

"No route to host" is what you get if the connecting machine literally can't find that IP on the LAN (for example, no response to arp requests).

---

### Post by nate66s on 2006-11-09
Thanks for the response.

I'm pretty confident about the IP address.  It's statically assigned via DHCP (I hope that makes sense :) ), along with its host name.  Prior to upgrading to Edgy, I was always able to connect using the host name or IP address -- now, neither work.  I meant to write in my original post that I wasn't able to ping the host, either.  I get "Destination Host Unreachable", as you might expect.

I CAN ssh out of that host to other hosts, as well as browse the web, get email, etc.

Aside from sshd, I know of no services to which I can connect.  I did, however, try arping, and that actually works.

I don't know much about iptables, but would an explicit rule to allow ssh connections possibly fix it?

---

### Post by nate66s on 2006-11-10
> **nixfaced said:**
> Just a thought -- double check and make sure your server's IP address is what you think it is, and that you've got basic connectivity from the server, and that you can connect to other services running on that machine from elsewhere on your LAN.  I realize it's probably a silly suggestion, but I've overlooked stuff like that before, and I only mention it because that info wasn't stated in your post.  

"No route to host" is what you get if the connecting machine literally can't find that IP on the LAN (for example, no response to arp requests).

Yup, I'm a knucklehead.  I had assumed the network hadn't changed, but I was wrong.  Apparently the net admin had changed a few things and I'm not getting the correct IP address anymore.  Hence, the connection problems.

Thanks again for the response.

---

### Post by razahel on 2006-11-28
same problem here answer found????

---

### Post by nate66s on 2006-11-28
The answer was in my previous post.  This was not a real problem, but my own mistake.  Once I tried connecting to the correct IP address, I had no problem at all.  Sorry I can't be of more help.

---

### Post by Miguel on 2006-12-15
Hi guys,

I have a similar ssh problem. I have a PC running Debian Etch running at University. It's also running sshd, as it is my access to the computer cluster that only accepts local logins. I have Ubuntu Edgy installed in my laptop. 

The thing is that if I try to ssh from my laptop to the server when I'm on my university, it works. When I'm at home, it doesn't. So the first thing it comes to mind is *He should allow ssh connections outside xxx.xxx.0.0*. Mmm no. One of the users can connect via ssh to that machine without issues from Cambridge (outside my Uni). Being suspicious, I fire putty on my father's laptop (Win XP) and, to my surprise, it connects beautifully to the debian machine. However, my ubuntu laptop won't:
```

$ ssh alias-of-debian-pc
ssh: connect to host debian.server.ip port 22: No route to host

```

Where alias-of-debian-pc is the alias defined in ~/.ssh/config, and has been tested locally. It is also curious that if I reboot into windows, putty ***will*** establish a successful session. If I issue a tracepath command, I get:
```

$ tracepath debian.server.ip/22
 1:  laptop.uni.static.ip (xxx.xxx.xxx.xxx)                        0.238ms pmtu 1500
 1:  no reply
 1:  laptop.uni.static.ip (xxx.xxx.xxx.xxx)                      2004.201ms !H
     Resume: pmtu 1500 

```

This is curious, because the tracing seems to fail at the first step... when trying to connect with my laptop's University IP (I hope this makes some sense). I was expecting something like home-ip -> home-router -> ISP-server -> Uni-server -> Debian-pc. 

If it isn't clear, please ask. Do you have any ideas? Suggestions? Every bit of help will be appreciated.

---

### Post by Miguel on 2006-12-15
Hi guys,

I just wanted to say that I've solved it. I just needed some more search results. The thing is I was pretty sure there was a conflict between my University setup (static IP, doman and host name, eth0) and my home setup (DHCP, shared wifi at home, eth1). Shutting down the interface related to the static IP did the trick:
```

sudo ifdown eth0

```

---

