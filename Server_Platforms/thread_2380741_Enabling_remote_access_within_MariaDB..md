---
title: "Enabling remote access within MariaDB."
date: 2017-12-21
forum: Server Platforms
---

### Post by timothylegg on 2017-12-21
Hello,

I'm dealing with a problem that I've been battling over the past 8 days.  While I was out to lunch, the problem fixed itself and I don't know why.  Maybe somebody can give some feedback with what exactly happened so I can prevent a relapse.

I posted in the Networking sub-forum a few days ago regarding not being able to communicate with MariaDB from an external machine.  The server exists as a virtual machine under a VMWare product.  I had believed that 3306 was being blocked either by the network or the VMWare host, but lacked a method to genuinely prove where the fault was.

This morning, Dec 12, I had an epiphany.  I remembered a tool called netcat and seeing a blog posting ages back about using it to create an improvised chat client across a WAN.

For example, one machine could run:

```
nc -l 3306
``` (that is 'l' as in 'el') and another machine runs ```
nc {IP address} 3306
``` Text can be transmitted and echo on the other machine upon the application of a carriage return.  Provided your network is configured to route this port traffic and your firewall is open, this will work.  I cannot emphasize enough how useful this tool was for me.

I decided that this would be a really cool low-level test.  I shut down MariaDB (which was no easy task since a number of likely shutdown methods didn't work, including rm -rf /etc/mysql and rebooting the machine to force it to barf; it didn't.  mysqladmin was the key tool for the task once I untarred the config files back to /etc/mysql/).  I used netcat and verified that port 3306 was in fact open and not being blocked.  At this point, I knew for sure that this was a problem within the configuration of MariaDB.

I went home for lunch and installed MariaDB on a spare Ubuntu laptop and quickly discovered I was able to configure it for external connections.  I caried this machine to work expecting to compare configuration files, line by line, but TAMO (Then A Miracle Occurs).  I verified the symptoms on my VM and discovered that MariaDB is now visible to external machines on 3306.

I restarted the machine twice today, mutliple times yesterday, to assure fresh, clean starts and leave nothing to chance.  The most recent config file change within the /etc/mysql/ tree is 8:23 on Dec 11 (that's yesterday morning).  Nothing changed.  It was fixed by the mere testing of the port 3306 with netcat.  This is akin to buying a screwdriver and pointing it at the christmas tree like a magic wand and fixing that one burned out lightbulb that shut down the whole damn string.  I am not particularly well-skilled in reproducible magic performances, in fact, I'll admit I'm terrible at it.  I would rather understand what on earth changed.  Computers are by ideological definition reproducible and predictable machines, so how did this happen?

CC to The Journal of Irreproducible Results for peer review.

---

### Post by howefield on 2017-12-21
Thread moved to the "*Server Platforms*" forum.

---

### Post by LHammonds on 2017-12-22
Maybe you had modified MariaDB config incorrectly, reloaded MariaDB and it broke the system.  Then fixed the config but didn't restart the database.

It quite concerned that you were not able to "stop the database" correctly in order to free up the 3306 port.

```
sudo service mysql stop
```

The above command is all you should need to issue in order to shutdown the database service.

VMware typically does not "block" traffic by default and is usually not a suspect with network traffic issues...especially if they are intermittent unless the NIC on your server is going bad (but I have not seen this in all my many years...e.g. it would be rare).   I have seen ports in switches go bad so if you suspect hardware, try plugging into a different port and then use a different network cable if that made no difference.

When installing MariaDB on a clean install of Ubuntu Server, it should not have anything blocking port 3306 since the software firewall is not enabled by default.  But you can check iptables/ufw rules very quickly if you suspect it is enabled.

The next layer is MariaDB itself.  When you define user access, you specify at what level the user can connect to the database by saying they can only connect locally on the server directly, or from a specific machine or from anywhere.  See my [usage examples]("http://hammondslegacy.com/forum/viewtopic.php?f=40&t=225#p544") as a reference.

LHammonds

---

