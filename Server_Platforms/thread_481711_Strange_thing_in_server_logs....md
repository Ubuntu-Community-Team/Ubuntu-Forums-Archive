---
title: "Strange thing in server logs..."
date: 2007-06-22
forum: Server Platforms
---

### Post by Betelgeuse on 2007-06-22
Hi,

After using kubuntu &#305;n my desktop computer for 6 months, I've decided to swith one of my production servers to linux. I've started with the easiest one and I've installed Ubuntu server 6.06 LTS on it. My server machine now working better than it was working with windows 2000. it's a server co-located on a datacenter and running vmware-server to host my virtual web and mail servers. I'm running only bind9 dns service and vmware-server on it and all my other services are inside vmware virtual machines.
I'm connecting to my server via ssh from my office computer and I've changed the default port to a different one. I'm looking at /var/log/auth.log file to see anything happening to security, so far, it2s running for one week without serious issues.
But I've found this entries in auth.log file : are they serious or normal operation? Should I look at other log files ? anything you suggest for more security? That server is very critical for my bussiness, so it should run all the time without downtime. 
---------------
Jun 21 06:25:02 dns1 su[7875]: + ??? root:nobody
Jun 21 06:25:02 dns1 su[7875]: (pam_unix) session opened for user nobody by (uid=0)
Jun 21 06:25:02 dns1 su[7875]: (pam_unix) session closed for user nobody
Jun 21 06:25:02 dns1 su[7879]: + ??? root:nobody
Jun 21 06:25:02 dns1 su[7879]: (pam_unix) session opened for user nobody by (uid=0)
Jun 21 06:25:02 dns1 su[7879]: (pam_unix) session closed for user nobody
Jun 21 06:25:02 dns1 su[7881]: + ??? root:nobody
Jun 21 06:25:02 dns1 su[7881]: (pam_unix) session opened for user nobody by (uid=0)
Jun 21 06:25:56 dns1 su[7881]: (pam_unix) session closed for user nobody
Jun 22 06:25:02 dns1 su[4702]: + ??? root:nobody
Jun 22 06:25:02 dns1 su[4702]: (pam_unix) session opened for user nobody by (uid=0)
Jun 22 06:25:02 dns1 su[4702]: (pam_unix) session closed for user nobody
Jun 22 06:25:02 dns1 su[4704]: + ??? root:nobody
Jun 22 06:25:02 dns1 su[4704]: (pam_unix) session opened for user nobody by (uid=0)
Jun 22 06:25:02 dns1 su[4704]: (pam_unix) session closed for user nobody
Jun 22 06:25:02 dns1 su[4706]: + ??? root:nobody
Jun 22 06:25:02 dns1 su[4706]: (pam_unix) session opened for user nobody by (uid=0)
Jun 22 06:25:56 dns1 su[4706]: (pam_unix) session closed for user nobody 
-------------

---

### Post by PetePete on 2007-06-23
looks like its just cron doing sheduled tasks. normal.

---

### Post by Betelgeuse on 2007-06-23
Thanks... So, it seems my first linux server installation was a success... :p

I've changed the ssh port as suggested and I do not see ant brute force connection attempts. should I install any outher thing to make my server more secure?

and, I have bind9 running on that server and I've just copied the zone files from the previous windows 2000 server dnd service and they seem to be working. I need a simple dns zone file thay I copy and edit for my zones. can anyone send me a zone file with one A record, an MX record and a CNAME record so that I can use that as a template for my dns server? I do not feel comfortable using the zone files from windows 2000 server.

---

