---
title: "port 852 is open - why?"
date: 2006-07-10
forum: Server Platforms
---

### Post by venzen on 2006-07-10
Greetings the list,

I just scanned a new Dapper server with nmap and unexpectedly found port 852 open. Anyone know why? This is not a port I have ever dealt with, so I'm a little concerned here - already connected the server to the network to upgrade packages before configuring Tripwire (a big no-no, of course [-X ).

Please someone tell me this is a service port purposefully opened by Dapper! [-o<

---

### Post by harisund on 2006-07-10
Port 852? No idea.. 

but you could do a "sudo netstat -plant" and check what program is causing the port to be open,and to what machine that port is connected to if a connection has already been established. 

(Don't be surprised if it is connected to my machine .. could be a part of my plan to take over the world :D) )

---

### Post by RavenOfOdin on 2006-07-10
Try downloading chkrootkit and rkhunter.

---

### Post by venzen on 2006-07-10
thanks for your reply harisund.

netstat outputs the following:

> Active Internet connections (servers and established)
Proto Recv-Q Send-Q Local Address           Foreign Address         State       PID/Program name
tcp        0      0 0.0.0.0:111             0.0.0.0:*               LISTEN     3610/portmap
tcp        0      0 0.0.0.0:852             0.0.0.0:*               LISTEN     4062/rpc.statd
tcp        0      0 127.0.0.1:25            0.0.0.0:*               LISTEN     4007/master
tcp6       0      0 :::22                   :::*                    LISTEN     4033/sshd 

interesting. I've never seen statd operate on that port. :idea: it might be that nfs-kernel-server (which I installed) operates statd through this port.

I'll report any updates here.

---

### Post by venzen on 2006-07-10
> **RavenOfOdin said:**
> Try downloading chkrootkit and rkhunter.

Thanks, chkrootkit reports no infections, altho' this cocked my eyebrow:

> Checking `sniffer'... lo: not promisc and no packet sniffer sockets
eth0: PACKET SNIFFER(/sbin/dhclient3[3553])


what the... maybe this is only saying that dhclient is (rightfully) running... or does it?


```
kill rpc.statd
``` and restarting it moved it to listen on port 633

---

### Post by venzen on 2006-07-10
OK it seems I got excited too quickly - but therein lies the lesson:

The man page for rpc.statd states that statd (part of NFS) never listens on a specific port - instead it asks portmap for a random port. You can even assign it a port number by using the --port option.

If you check your own NFS server with ```
sudo netstat -plant
``` (thanks harisund) you'll get some arbitrary port for rpc.statd

Thanks for the responses guys - some healthy paranoia piques the sysadmin's senses! ;)

---

### Post by harisund on 2006-07-10
Wow! You learn something new everyday, don't you? I do :)

---

