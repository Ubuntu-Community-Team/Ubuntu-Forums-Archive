---
title: "Backuppc and 11.04"
date: 2011-04-29
forum: Server Platforms
---

### Post by random_id on 2011-04-29
I just updated my home server and everything works great...except Backuppc.

For some reason, it fails to backup anything because it can't ping anything.  This includes the backups to itself.
I made sure there isn't any firewall issue, but I am at a loss.
Does anyone have any suggestions?

Thanks

---

### Post by random_id on 2011-04-30
I got a little closer.  I was able to successfully ping and backup files from the local server using the tar commands that worked prior to my 11.04 upgrade.  I found that I needed to change the default ping command to;

```
ping -c 1 $host
```

Now I can ping everything, and the Tar backups work as before.

I still cannont get my Windows machines to backup with rsyncd.  I figure that something has changed with rsync during the 11.04 upgrade, but I can't figure it out.

---

### Post by random_id on 2011-04-30
OK, I got it...but I don't understand it.
I had the DHCP flag turned on for the Windows machines.  Once I turned it off, everything started working.  I don't know why and I am slightly concerned about what will happen when new IPs are assigned, but at least it is working now.

---

### Post by smithberry on 2011-04-30
Thanks for that - changing the ping command worked for me although I can't see why - in config.pl the ping path  was /bin/ping which seems right. Still, important thing for now is that backups are working.

---

### Post by chitowner2 on 2011-07-24
I'd like to follow on to this thread- if it's not too old to get noticed. I think my situation is related. 

I recently set up a new machine to act as server for backupPC, using rsync over ssh to backup a few other machines.

Problem is, as alluded to previously in this thread, sometimes a simple reboot will cause a machine to come up with a new IP, eg 192.168.1.?? and then the public/private keys won't work, so backups fail.

I am not a wiz at this stuff. I have enough dangerous knowledge to follow a recipe (most of the time.  ;) ) so what I want to ask is: Is there a way to assign an ID to each machine that will remain independent of it's IP and allow backupPC to ignore the actual IP in favor of some permanent ID?

Thanks!
CT
:popcorn:

---

### Post by mamboze on 2011-08-21
@chitowner2   I just noticed your post today. I had just setup a ssh network and the IP changes on the laptop were breaking the connection. 

Anyhow, after hunting around a bit I came across this method for setting the IP address as static. This worked OK on my laptop. 

open this file /etc/network/interfaces

and change the 5th line below in the code to 
iface eth0 inet static
(the eth0 setting is for my machine, others may vary)
so:

```
auto lo
iface lo inet loopback
* assigning a static IP address 31/07/11
auto eth0
iface eth0 inet static
address 192.168.1.2
netmask 255.255.252.0
network 192.168.1.0
broadcast 192.168.1.255
gateway 192.168.1.1
```

Hope this helps :D

---

