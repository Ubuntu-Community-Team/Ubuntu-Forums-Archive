---
title: "Allow NFS through firewall in Ubuntu Servers"
date: 2010-06-11
forum: Server Platforms
---

### Post by Thyagaraj on 2010-06-11
How to allow NFS through firewall(iptables) in ubuntu servers
I've firewall configured on my server and i've recently configured the NFS server & client. I could mount the shared directory on my server from my client only if i disable the firewall(ufw disable), if i enable  i couldn't. I also tried allowing the ports on firewall(ufw 32771, 111 and 2049) but no use.

Plz... need help!

---

### Post by arrrghhh on 2010-06-11
Are you connecting over the WAN?  I have a UFW statement that allows anything that's local to my server.  Perhaps this is a 'security loophole', but if a hacker is on my local network I've got bigger issues :P

But, I believe NFS uses port 111 and 2049, tcp and udp.  There's others, but I think that's all you need to open...

---

### Post by Thyagaraj on 2010-06-17
Having allowed the ports 2049, 111 i couldn't mount until i disable firewall.

Plz... more suggestions..

---

### Post by arrrghhh on 2010-06-17
Like I said there's more ports, but it's not recommended piping NFS over the WAN!!

---

