---
title: "dhcp server with heavy network load"
date: 2008-01-23
forum: Server Platforms
---

### Post by cdenley on 2008-01-23
I recently installed dhcp3-server on my 1gbps lamp server to provide addresses for windows xp clients. Today, I was transferring large files from an old 100mbps server to my lamp server using rsync. Whenever there is an rsync transfer in progress, the client machine can't renew it's IP address.  /var/log/messages shows it occasionally gives a dhcp offer. SSH terminals are slow, but usable. Apache seems to work fine. I tried to download and install a package during the transfer, and apt-get hung for about a minute. Why did this happen, and how could I prevent this from happening in the future?

---

### Post by HermanAB on 2008-01-23
Rsync is likely using all available bandwidth on ethernet.  Check the rsync man page, it has a bandwidth throttle capablity so you can limit the amount it can use.

Cheers,

Herman

---

### Post by cdenley on 2008-01-23
I had considered that, but how is that possible if the server it is copying from is 100mbps, and the dhcp server is 1gbps? There should be plenty of bandwidth left over for dhcp. Apache doesn't even run slow, and that would use more bandwidth than dhcp. I just tried testing it, but I can't recreate the original problem anymore. Thanks for the tip about bandwidth throttling, though. Since I'm not having the problem anymore, I guess I will forget about it unless it pops up again.

---

### Post by cdenley on 2008-02-01
I just noticed this problem happening again. It apparently has nothing to do with networking. It happened while using rsync to copy from one local directory to another. Apparently, it has to do with disk i/o. It seems to happen every time I run the same rsync command. While the command is running, I can write to the hard drive fine. The command "cat /var/lib/dhcp3/dhcpd.leases" only has a delay of about 1-2 seconds. "top" shows that the CPU and memory is not being used up. I have a raid-10 array on a 3ware Inc 9550SX controller. The 3dm2 web interface doesn't show any problems.

---

### Post by PinkFloyd102489 on 2008-02-01
Well you also have to think. If you have a 100Mb connection going to a 1Gb machine, the peak speed is going to be 100Mb.

---

### Post by cdenley on 2008-02-01
> 
Well you also have to think. If you have a 100Mb connection going to a 1Gb machine, the peak speed is going to be 100Mb.


Exactly. The peak speed of the rsync transfer was 100mbps. There was a 1gbps connection between the dhcp client and server. The rsync transfer could not have been consuming all the bandwidth needed for the dhcp renewal. Anyway, as I pointed out in my last post, the network usage is irrelevant since the problem occurs when copying files locally.

---

### Post by cdenley on 2008-02-04
The problem goes away if I have write caching enabled. I disable it, start a long rsync copy from and to the raid array, then a dhcp renew fails. I enable it again, dhcp reply succeeds with no delay. This definitely has to do with the disk I/O. I would prefer to have write caching disabled, but I need the server to work reliably, and I'm not sure what other processes disk writing may be interfering with.

---

