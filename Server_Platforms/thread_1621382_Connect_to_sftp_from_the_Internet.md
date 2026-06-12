---
title: "Connect to sftp from the Internet"
date: 2010-11-14
forum: Server Platforms
---

### Post by SpinningAround on 2010-11-14
I have a openSSH server, it works to connect to it within the local network but I can't connect to it from the Internet. What I would like to do is to connect to the server using filezilla client, simply by using username and password.

To make it secure from brute force attacks will I only allow connections from specific IP number. 

The following scenario:
I have a server with the static internal ip 192.168.1.5, port is 2222. My global ip is 10.4.5.6 and I would like to connect with filezilla client from ip 11.1.2.3. How do I connect?

UFW rule:
allow proto tcp from 11.1.2.3 to 10.4.5.6 port 2222

Portforward in the router:
port: 2222 (to) 10.4.5.6

Would that be the correct way?

---

### Post by NathanBC on 2010-11-19
What happens when you try to connect?  Nothing?  Or do you get a rejection?

If nothing then I suggest you use either tethereal or tcpdump to capture packets at the SSH server while you try to connect.  If you do not see any packets arrive at the server during the test then you need to look at the router configuration.  If you do see packets then make sure the source address in the packets is the one you are expecting.

---

