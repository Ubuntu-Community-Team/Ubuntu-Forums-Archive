---
title: "Odd SSH issue."
date: 2009-04-10
forum: Server Platforms
---

### Post by KajiMaster on 2009-04-10
I was playing around with my IPTables the other day at work via Ssh and ended up locking myself out of my system for the day.  When I got home I loaded my previous IPTables config and was back in business.  I worked on other things on my server for the rest of the night with no issues.  I was able to SSH in on my LAN to my server with no problems.  I even had a friend SSH into my server from his house with no problems.
So this morning when I was getting ready for work I made sure my server was working by pinging yahoo.com just to ensure everything was right with the internet.  Of course it was fine.  When I got to work I was showing my co-workers the homepage I had made for my server: [www.bentillusions.com](www.bentillusions.com).  While I was telling them what I did a co-worker asked me if my server was down.  
Apparently he could not ssh into the server.  When he ssh's it gives the black screen that it does right before a Username: but never says Username.  After lagging for a moment it says "Server unexpectedly closed network connection".  At this point I'm pissed because I was just using it last night and was sure it was all in order.  Quickly thinking I tried sshing into my co-workers Linux server to test if SSH was disabled at work.  It wasn't disabled; I got in just fine.  So while I was in his shell account I tried sshing into MY server with no problems. 
My question is why can I not ssh into my server at work but ssh into it from a server that I sshed into at work?  This honestly does not sound like an IPTables issue.

---

### Post by BkkBonanza on 2009-04-10
Are you running a firewall script that would have added your ip to a deny list after your attempts the day before?

---

### Post by benanzo on 2009-04-10
I'm with BkkBonaza.

Check /etc/hosts.deny for your IP addr.

Sounds like you run something like DenyHosts to block IPs that appear to be 'brute-forcing' your sshd.

You can whitelist your IP by adding it to /etc/hosts.allow:

```

sshd: <ip_addr>

```
or
```

ALL: <ip_addr>

```

---

### Post by KajiMaster on 2009-04-11
I think you guys are so right.  I do have denyhosts running on my server.  Just before I checked my replies to this thread I saw that root had several e-mails.  Many of them where from denyhosts.  So many IP's are getting blocked and I am not sure what most of them belong to.  One of the ip's looked very familure perhaps this is my work IP.  I'll have to check on it Monday when I go back. 

Question:  If it does have my work IP on denyhost why can I check my website from work and FTP in?

Thanks for all the help!!
-Kaji

---

### Post by brian_p on 2009-04-11
> **KajiMaster said:**
> 

Question:  If it does have my work IP on denyhost why can I check my website from work and FTP in?

```
apt-cache show denyhosts
```

---

### Post by KajiMaster on 2009-04-13
Short and sweet Brian.  But very helpful.  I was able to pull up my list of denyed IPs and verify that the IP address i connect with for SSHD was blocked.

The next task it trying to get that IP off the list.  Every time I delete it from the list it finds a way back on their.  I'm going to search the form and web for this answer.  Thanks to all who helped me identify the problem!! This just saved me a good weeks worth of frustration.

---

### Post by KajiMaster on 2009-04-13
For the sake of closure.  I am able to ssh via my work IP now.  I had to turn off denyhosts and remove all the ips i didn't want blocked from the hosts.deny file.  Then create a file called allow-hosts in the WORK_DIR for denyhosts with the IP's i wanted to use.  Restarted DH and the issue is resolved.

---

