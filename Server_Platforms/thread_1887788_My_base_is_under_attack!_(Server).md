---
title: "My base is under attack! (Server)"
date: 2011-11-27
forum: Server Platforms
---

### Post by dmattox10 on 2011-11-27
I have three ubuntu servers on my LAN, one of which uses dyndns to resolve to a domain, allowing me to serve pages from home (development more than anything). All three servers have very tight security. The exposed server is attacked every few hours on port 22, sshd. The logs have the IP's of every attack, as do the blacklist. My server is safe, but every time an attack takes place, my WAN traffic slows to dial-up speeds. I get disconnected from netflix/xbox live/web browsing stops working until I reboot my modem and router. I need to leave ssh available for myself from remote locations. PLEASE ANY SUGGESTIONS!!

---

### Post by arrrghhh on 2011-11-27
Well for one, put SSH on a different port.

Two, make sure password auth is disabled, keys only (you didn't mention this, hopefully it already applies).

Other than that... I'm not sure.  I've never noticed my 'net slowing from attacks, but perhaps you're getting far more than I am...?

---

### Post by Dangertux on 2011-11-27
> **dmattox10 said:**
> I have three ubuntu servers on my LAN, one of which uses dyndns to resolve to a domain, allowing me to serve pages from home (development more than anything). All three servers have very tight security. The exposed server is attacked every few hours on port 22, sshd. The logs have the IP's of every attack, as do the blacklist. My server is safe, but every time an attack takes place, my WAN traffic slows to dial-up speeds. I get disconnected from netflix/xbox live/web browsing stops working until I reboot my modem and router. I need to leave ssh available for myself from remote locations. PLEASE ANY SUGGESTIONS!!
 

Changing the port will definitely help -- as most of these attacks are automated, if they don't see port 22 they will just move on. Don't use port 2222 either, some of the tools that perform these attacks have become quite clever, use something random.

Not really sure why it's slowing you down so much, are you sure that's the cause?

---

### Post by docbop on 2011-11-27
like said previously this shouldn't be slowing you down, do you have mail server on this box???    SPAMmer could be using your mail server???

---

### Post by dmattox10 on 2011-11-27
Wow... I love this forum, beyond the quick helpful replies, I get taken to school every time! I have no idea how to use keys. I'll google it. There is no mail server running, but here is the /etc/hosts.deny file, I've only been using this server for 6 days, all of these blacklisted IP's are from this week, and as I said, it effectively halts my WAN traffic, all LAN operations continue, and logging into the server and viewing the file everytime I get kicked off xbox live, there is a new IP in hosts.deny

```

# /etc/hosts.deny: list of hosts that are _not_ allowed to access the system. 
#                  See the manual pages hosts_access(5) and hosts_options(5). 
# 
# Example:    ALL: some.host.name, .some.domain 
#             ALL EXCEPT in.fingerd: other.host.name, .other.domain 
# 
# If you're going to protect the portmapper use the name "portmap" for the 
# daemon name. Remember that you can only use the keyword "ALL" and IP 
# addresses (NOT host or domain names) for the portmapper, as well as for 
# rpc.mountd (the NFS mount daemon). See portmap(8) and rpc.mountd(8) 
# for further information. 
# 
# The PARANOID wildcard matches any host whose name does not match its 
# address. 
# 
# You may wish to enable this to ensure any programs that don't 
# validate looked up hostnames still leave understandable logs. In past 
# versions of Debian this has been the default. 
# ALL: PARANOID  
sshd: 60.18.93.11 
sshd: 94.228.222.152
sshd: 116.125.126.12
sshd: 94.75.209.44 
sshd: 81.169.143.225 
sshd: 189.52.165.130 
sshd: 180.153.127.111 
sshd: 195.220.161.7 
sshd: 61.55.190.39 
sshd: 91.205.189.27 
sshd: 10.0.0.102 
sshd: 121.127.231.251 
sshd: 125.88.75.199
sshd: 61.190.30.18 
sshd: 58.221.216.190 
sshd: 184.173.124.90 
sshd: 109.235.254.106 
sshd: 208.109.94.237 
sshd: 94.73.161.210 
sshd: 46.231.114.242 
sshd: 64.46.39.34 
sshd: 121.10.140.215 
sshd: 85.114.140.73
sshd: 199.68.196.167 
sshd: 211.224.108.50 
sshd: 202.131.124.10 
sshd: 59.42.249.53
sshd: 211.151.57.196 
sshd: 112.78.1.97 
sshd: 94.75.204.203 
sshd: 110.45.147.214 
sshd: 94.75.215.26 
sshd: 91.205.189.15 
sshd: 61.191.39.19 
sshd: 79.172.14.99 
sshd: 188.187.250.19 
sshd: 184.106.207.60 
sshd: 66.232.140.121 

```

edit... I now use private keys, passwords are disabled. So, my last questions, if I allow the new port I want to use through ufw, and change ssh to expect that port, do I do anything different on my laptop to connect ssh? Is there anywhere on my laptop that I type in the new port?

---

### Post by Doug S on 2011-11-28
I guess I would have a different approach with regard to the original posting. With certainty, and before making changes that might only significantly reduce the frequency of requiring it without eliminating it, I would want to first identify the root cause of the need to reboot the modem and router. To make the investigation and debugging easier, I might even try increase the frequency of the problem.
 
As all of the other reply posters have already stated and suggested: I have never seen an SSH attack that would come within even a couple of orders of magnitude of using a significant portion of my WAN bandwidth. I am not saying it is not so, I am just suggesting too investigate further rather than assume it to be so. I would use tcpdump or wireshark to capture packets so as to observe what is going on during one of these events.
 
I am not familiar with methods for what appears to be some dynamic hosts.deny list. Might there be some network disruption associated with this list update process? Where the list update was caused by the, possibly low bandwidth, SSH port 22 attack.
 
To answer your actual question: yes, there should be a way to specify port from your LapTop. I use PuTTY from my windows LapTop, on which there is a box for port. If you are using the ssh command from a linux terminal window then I think the -p option is used (check the man pages).

---

### Post by spynappels on 2011-11-28
As said above, I'd be very surprised if the SSH attempts are managing to saturate your connection, not impossible, but unlikely.

Check other vectors too, such as how many hits your website is taking when this happens (DoS) or activity on any other public facing service.

---

### Post by a2j on 2011-11-28
get fail2ban working

---

### Post by Dangertux on 2011-11-28
> **a2j said:**
> get fail2ban working

For the time being I would shy away from fail2ban in favor of denyhosts -- if you're dealing with a denial of service condition fail2ban can amplify that. iptables conntrack gets saturated fairly easily, as opposed to the simple tcp wrappers that denyhosts uses.

---

### Post by Habitual on 2011-11-28
Change port.
Secure ssh service 
install fail2ban

all good suggestions.
Server Security is NEVER "complete" or "done". It is an on-going process.

---

### Post by sandyd on 2011-11-28
Use Ossec.

An initial configuration of ossec will automatically block IPs after a certain number of ssh passwd failures.

---

### Post by kleverbear on 2011-11-29
> **sandyd said:**
> Use Ossec.

An initial configuration of ossec will automatically block IPs after a certain number of ssh passwd failures.

Can you elaborate more on this please.

---

### Post by Dangertux on 2011-11-29
OSSec is covered here [http://ubuntuforums.org/showthread.php?t=1477662](http://ubuntuforums.org/showthread.php?t=1477662) with other HID applications.

---

### Post by dmattox10 on 2011-12-03
Changing the authentication and port has stopped the attacks, the list of denied hosts has not grown (on any service) since I made the suggested changes. With the problem solved, I again assert that some kind of brute force was going on, aimed at ssh. Now, however, occasionally I am unable to ssh into the server (connection refused), but it comes and goes, and I can still use the root prompt in webmin... This problem is solved!

---

