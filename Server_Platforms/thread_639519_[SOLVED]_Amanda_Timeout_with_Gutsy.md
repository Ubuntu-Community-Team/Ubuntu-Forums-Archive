---
title: "[SOLVED] Amanda Timeout with Gutsy"
date: 2007-12-13
forum: Server Platforms
---

### Post by wsmoser2004 on 2007-12-13
My school uses AMANDA to back up all computers on our science network, and I have one Ubuntu machine on the network that refuses to let AMANDA back it up.  Most of the machines around here are running Solaris 9/10, and the AMANDA server runs Solaris 9.  When I try to test the backup for the Ubuntu machine, I get

```

Amanda Backup Client Hosts Check
--------------------------------
WARNING: <client hostname>: selfcheck request failed: Host down?
Client check: 1 host checked in 30.011 seconds, 1 problem found

```

I followed this guide to get it set up on the client: [http://ubuntuforums.org/showthread.php?p=2470030](http://ubuntuforums.org/showthread.php?p=2470030).  I am running Gutsy, but I thought that it wouldn't make that much of a difference.

I then thought that maybe it was a problem between the versions of AMANDA on the Solaris machine and Ubuntu, so I set up another Ubuntu machine to be a "test" server.  I followed the same guide for the server, and that one says almost the same thing:

```

Amanda Backup Client Hosts Check
--------------------------------
WARNING: <client hostname>: selfcheck request failed: timeout waiting for ACK
Client check: 1 host checked in 30.011 seconds, 1 problem found

```

When I do a tcpdump on the client, this is what I see (raster is the client, matrix is the server):

```

tcpdump: verbose output suppressed, use -v or -vv for full protocol decode
listening on eth0, link-type EN10MB (Ethernet), capture size 96 bytes
09:58:59.890809 arp who-has raster tell matrix
09:58:59.890841 arp reply raster is-at 00:11:2f:c5:56:6f (oui Unknown)
09:58:59.890938 IP matrix.848 > raster.amanda: UDP, length 123
09:58:59.890996 IP raster > matrix: ICMP raster udp port amanda unreachable, length 159
09:59:04.889737 arp who-has matrix tell raster
09:59:04.889862 arp reply matrix is-at 00:40:2b:35:80:9a (oui Unknown)
09:59:09.887383 IP matrix.848 > raster.amanda: UDP, length 123
09:59:09.887434 IP raster > matrix: ICMP raster udp port amanda unreachable, length 159
09:59:19.887503 IP matrix.848 > raster.amanda: UDP, length 123
09:59:19.887558 IP raster > matrix: ICMP raster udp port amanda unreachable, length 159

10 packets captured
14 packets received by filter
0 packets dropped by kernel 

```

There also seem to be no debug logs in /tmp/amanda or /var/log/amanda.  I disabled the firewall on the client, so that shouldn't be interfering.

I'm at a loss...

---

### Post by k_grdn on 2007-12-13
Hi,

I've had problems previous with amanda on ubuntu, I found the best solution was to install the client from source.

Regards,

k_grdn

---

### Post by wsmoser2004 on 2007-12-13
I ended up fixing the problem.  I ran "/usr/sbin/xinetd -d" and it told me there was an error in a configuration file and then it bailed out.  After I fixed that it works great.  Thanks for the idea though.

---

### Post by thesheff17 on 2008-01-03
I'm receiving the same error with two brand new installs of Gusty.  Can you help me out with what you changed to make this work?  Thanks in advance.

---

### Post by wsmoser2004 on 2008-01-21
Sorry thesheff17, I wasn't subscribed to the thread any more.  I can try to help you out, although I'm far from an Amanda expert at this point.  

First, make sure that your firewalls are down.  That was my first problem...the firewall on my client machine was preventing any connections from the server.  

Next, do a 

```

netstat -a | grep amanda

```

You might get something like this:

```

udp        0      0 *:amanda                *:*

```

That will tell you if amanda is running (if you get nothing, it's not running).  If it IS running, this next part won't help you. :)  In my case, it was not.  So  next, what I did was manually start xinetd from the command line.  First, you'll want to stop it with

```

sudo /etc/init.d/xinetd stop

```

Then, do 

```

sudo /usr/sbin/xinetd -d

```

I don't know what normal output for that command is, but when I ran that it told me there were problems with the xinetd amanda configuration file  (/etc/xinetd.d/amanda).  In my case, I had a line in there that I thought would work, but apparently did not.  Then I just restarted and everything worked.

If you need anything else, let me know...I'll resubscribe to the thread. :)

---

