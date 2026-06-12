---
title: "Server works only with IP"
date: 2012-06-12
forum: Server Platforms
---

### Post by computerfox on 2012-06-12
Hello all,

I had to rebuild my server and right now I'm just transferring the data back and trying to configure it again.  The problem is that when I try to get to it, it only works with the internal IP.  I can not access it with the domain name nor outside of my network.  I have a feeling it's a problem with my DNS, but all my DNS's point to the correct public IP.  I use webmin for management.

My host file looks like this:

```


127.0.0.1       localhost

# The following lines are desirable for IPv6 capable hosts
::1     ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
127.0.0.1       hosting.computerfoxdesign.com

```

Other information is also added as attachments.

Any idea what's going on?

-FOX

---

### Post by kennethconn on 2012-06-12
```
 
127.0.0.1       hosting.computerfoxdesign.com

```
 
That should be the LAN IP address 192.168.xxx.xxx - I can't see your attachments when replying, but you know what I'm getting at.

---

### Post by computerfox on 2012-06-12
thanks kenneth for the reply.  i tried changing it and cleared the cache in my browser, but it's still not working.

---

### Post by computerfox on 2012-06-12
I'm out of ideas.  I need some assistance with this one....

---

### Post by computerfox on 2012-06-12
okay, so i may have figured it out, at least the first problem.  i needed to add eth1.  now, all domains lead to the same directory

---

### Post by kennethconn on 2012-06-12
Did you restart networking once you change it?
What does your resolv.conf file show?
When you run hostname command on the server with the various switches, is the output as expected?
What machine are you trying to access it from - try local (server) access first using ping etc, then from another local machine?

---

### Post by computerfox on 2012-06-12
1- Yes, I believe so
2-

```

domain home
search home
nameserver 192.168.1.1

```

3- Yes
4-My domains are on a server so if i simply ping the other domain it will say yes because it does reach my server, but it doesn't give me the correct directory.

---

### Post by computerfox on 2012-06-12
In my virtual server, I forget to add the www for the domain so of course it would point to the default root.  the problem now is that it downloads something, instead of showing the site.  WTF?

---

### Post by computerfox on 2012-06-12
I have a feeling that this is due to the fact that I'm still trying to transfer the data back... I'll keep you posted.

---

### Post by computerfox on 2012-06-13
Okay, so everything seems to be working now, but I'm still transferring data over.  Does anyone have any suggestions on how to prevent long data transfers?  I was thinking about separating the OS and the actual data and then backing up the data hard drive once a month, but I'm out of hard drives and they're quite expensive now a days.  I think this would be a good move because even if I do have to ever rebuild in the future, I can simply remount the data hard drive and boom, the server is back online.

---

