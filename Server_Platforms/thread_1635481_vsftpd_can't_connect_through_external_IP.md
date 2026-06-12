---
title: "vsftpd can't connect through external IP"
date: 2010-12-01
forum: Server Platforms
---

### Post by mordriel on 2010-12-01
Hi there.
I've been trying to get an FTP server running with vstfpd.  I've partially succeeded, in the way of being able to log in from either localhost or my router's IP address.  
     I have a free account set up with dyndns.com (and my IP is dynamic, so I have to update it whenever I turn my box on).  Well, I've realized through nmap and portscan, and the open port tool on dyndns's site (as well as through various clients like Filezilla) that port 21 isn't open (at least to the rest of the web).  Nor is 80.  After trying port forwarding through my router with no success, I tried plugging directly in through my modem.  It's a little Westell modem, and I have AT&T DSL.  I'm not sure if that's my issue or not.  However, whenever I try to connect from my external IP, my connection is always refused.  Same thing happens when I check the port through dyndns' port checker, both through the router or directly through the modem.  I can't find any instance of AT&T blocking port 21 (I thought that was used for FTP).  
     Has anybody else had issues like this?  
     I tried installing an Apache server to make sure I didn't just suck at messing with FTPs... same problems.
     Thanks! ^_^

---

