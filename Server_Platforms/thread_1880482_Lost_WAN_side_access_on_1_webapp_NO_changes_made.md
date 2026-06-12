---
title: "Lost WAN side access on 1 webapp NO changes made"
date: 2011-11-13
forum: Server Platforms
---

### Post by kleverbear on 2011-11-13
So im not able to reach my webapp SubSsonic from the WAN side anymore, im posting here to see if anyone can help. This issue suddenly appeared and it would happen at random. I decided to restart the deamon and same issue. I also restarted the server and it made it worse. After the server restart i was not able to reach SS with my domain name and port from WAN or internally, but via internal ip with port it does resolve correct. I thought it might be a firewall issue but no go, i disabled and restarted disabled and still no connection from WAN side. Ive taken my router off and with the server firewall disabled direct connect to mdm still not reachable. My mdm does not have any filters on it its a plain bridge. I do have 3 other server side web apps that I use and all are reachable on their ports with domain. Apache is runing and is reachable. My router is manually configured to port forward and trigger to my SS port 4040. I am at a loss on this as i'm not familiar with jetty server to t-shoot that. Any help is appreciated.  :D 

**System info:**

Operating system	Ubuntu Linux 10.04.3
Version	4.5 (build 2384)
Server	jetty-6.1.x, java 1.6.0_20, Linux (58.8 MB / 120.0 MB)
Kernel and CPU	Linux 2.6.32-35-server on x86_64
Processor information	Intel(R) Atom(TM) CPU 330 @ 1.60GHz, 4 cores :?: 

After a restart and trying to connect this is all tha logs show.
```
[2011-11-11 16:21:05,526] INFO DaoHelper - Checking database schema.
[2011-11-11 16:21:06,988] INFO DaoHelper - Done checking database schema.
[2011-11-11 16:21:07,912] INFO SearchService - Automatic index creation scheduled to run every 1 day(s), starting at Sat Nov 12 03:00:00 PST 2011
[2011-11-11 16:21:08,260] INFO PodcastService - Automatic Podcast update scheduled to run every 24 hour(s), starting at Fri Nov 11 16:26:08 PST 2011
[2011-11-11 16:21:14,100] WARN NetworkService - No UPnP router found.
```

And just to be sure heres the out put SubSonic conf  /etc/default/subsonic
```
SUBSONIC_ARGS="--max-memory=720 --port=4040"
```

Thanks in advance.


I forgot i did confirm the server is listening to the port, it shows it only listening to ip6???? 
```
sm1:~$ netstat -l
Active Internet connections (only servers)
Proto Recv-Q Send-Q Local Address           Foreign Address         State      
     
tcp6       0      0 [::]:4040               [::]:*                  LISTEN     
```

I double checked the NIC conf and its still correct, every other service on that server is reachable just not SS. No Bios changes or updates, I have no OS updates, but there was an update on java. Server can ping its self and i cant still ping it from LAN or WAN and via VPN.

---

### Post by volkswagner on 2011-11-13
I think you hit the nail on the head with "tcp6".

If you are not using ipv6 for anything, you can simply [disable it globally in Grub2]("http://www.webupd8.org/2009/11/how-to-disable-ipv6-in-ubuntu-910.html").  This may help diagnose if ipv6 is the issue.


```
GRUB_CMDLINE_LINUX="ipv6.disable=1"
```

---

### Post by kleverbear on 2011-11-14
> **volkswagner said:**
> I think you hit the nail on the head with "tcp6".

If you are not using ipv6 for anything, you can simply [disable it globally in Grub2]("http://www.webupd8.org/2009/11/how-to-disable-ipv6-in-ubuntu-910.html").  This may help diagnose if ipv6 is the issue.


```
GRUB_CMDLINE_LINUX="ipv6.disable=1"
```

Thanks i thought so too, but today the service is reachable, i did nothing that i thought would cause it work. What prompted me to check when i logged in my server advise me i had a zombie process, now i had turned off the service the previous day and forgot to re-enable. Once i checked my running process i noticed it was back up running. I checked again to the listening ports and to my surprise no tcp 4040 but tcp6 4040 still listening and i cant figure this out :confused: Im hoping the dev will respond to my post on his forums.



UPDATE: issue disappeared on its own...bewildered still

---

