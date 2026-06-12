---
title: "Help adding new host to Nagios"
date: 2006-08-28
forum: Server Platforms
---

### Post by chrisfay on 2006-08-28
I am trying to add a pc on my home network as a new host to Nagios. I am currently monitoring Localhost using the basic configuration using 'minimal.cfg' instead of splitting the files until I have a better understanding of the software. 

The problem is, when I add a new host and hostgroup it does not monitor the new host but rather Localhost. The software shows the new host and all services but the output is identical for both Localhost and the new host I create.  

What part of the host directive is used to specify the physical location of a new host? I created a zone in bind for my internal network which works fine; i tried using both the hostname and LAN IP of my new host to no avail. 

What am I missing?

---

### Post by chrisfay on 2006-08-28
So it looks like Nagios requires some extra configuration in order to monitor host services remotely. I know its possible becuase we use Nagios to monitor a ton of remote machines at work. This was in an article I just read:

> Nagios has some useful plugins for monitoring host state, but most of them only operate on a local system. To run them against remote systems, you need to use either the NRPE plugin (extra setup) or the check_by_ssh plugin (setup, shell access, protocol overhead) to execute the same plugins remotely.

I was curious if anyone has done something similar. I have never configured snmp and not sure how I would go about installing that on my Ubuntu local machine. 

Anyone?

---

