---
title: "Something is trying to connect to inra.ir"
date: 2010-02-10
forum: Security
---

### Post by ErikShreve on 2010-02-10
I'm using OpenDNS and got a notice that a malware hosting site had been blocked. The sites are all variations of inra.ir. I've used wireshark to confirm that the requests are coming from my machine, which is running 9.10. 

I've only been running linux for a few months, so I'm a bit lost as how to proceed on tracking down what is sending these requests out.

I've been reading through some of the stickies, but they seem mostly geared toward prevention, not toward diagnosing a potential problem.

Thank you for your help.

Erik

---

### Post by styxcoverbnd on 2010-02-10
Are you running some type of server software on your machine like samba, ssh, ftp? If you are can you look in your auth log (/var/log/auth.log) and see if anything looks unusual

Can you also open up a terminal and run this command to see if any programs are listening and what ports the are listening on

```
sudo netstat -tulnp 
```

---

### Post by ErikShreve on 2010-02-10
styxcoverbnd, thank you for the suggestions.

I'm not (knowingly) running any server software. The auth.log doesn't have anything that looks unusual. However, there are several entries for CRON that I haven't investigated yet.

Using lsof (and using netstat, as recommended by styxcoverbnd), I can see that mono has an open port when I'm running KeePass. Mono does not have a port open when running TomBoy or F-Spot. I've been doing some googling but haven't come up with any reasons why KeePass would open a port to listen on.

Here is the output of netstat:

```
sudo netstat -tulnp
Active Internet connections (only servers)
Proto Recv-Q Send-Q Local Address           Foreign Address         State       PID/Program name
tcp        0      0 127.0.0.1:43201         0.0.0.0:*               LISTEN      442/mono        
tcp        0      0 0.0.0.0:36678           0.0.0.0:*               LISTEN      1029/rpc.statd  
tcp        0      0 0.0.0.0:56361           0.0.0.0:*               LISTEN      -               
tcp        0      0 0.0.0.0:111             0.0.0.0:*               LISTEN      827/portmap     
tcp        0      0 127.0.0.1:7634          0.0.0.0:*               LISTEN      1250/hddtemp    
tcp        0      0 127.0.0.1:631           0.0.0.0:*               LISTEN      1462/cupsd      
tcp        0      0 127.0.0.1:25            0.0.0.0:*               LISTEN      14094/exim4     
tcp6       0      0 ::1:631                 :::*                    LISTEN      1462/cupsd      
udp        0      0 0.0.0.0:51773           0.0.0.0:*                           1029/rpc.statd  
udp        0      0 0.0.0.0:68              0.0.0.0:*                           1016/dhclient   
udp        0      0 0.0.0.0:53210           0.0.0.0:*                           -               
udp        0      0 0.0.0.0:5353            0.0.0.0:*                           880/avahi-daemon: r
udp        0      0 0.0.0.0:111             0.0.0.0:*                           827/portmap     
udp        0      0 0.0.0.0:55677           0.0.0.0:*                           880/avahi-daemon: r
udp        0      0 0.0.0.0:781             0.0.0.0:*                           1029/rpc.statd  

```

I'm not sure if any of those open ports should be a concern or not.

I just installed exim - installed when rkhunter was. rkhunter -c found a few items:

```

Warning: The file '/usr/sbin/unhide' exists on the system, but it is not present in the rkhunter.dat file.
Warning: The file '/usr/sbin/unhide-linux26' exists on the system, but it is not present in the rkhunter.dat file.

[10:03:45] Performing filesystem checks
[10:03:45] Info: Starting test name 'filesystem'
[10:03:45] Info: SCAN_MODE_DEV set to 'THOROUGH'
[10:03:46]   Checking /dev for suspicious file types         [ Warning ]
[10:03:46] Warning: Suspicious file types found in /dev:
[10:03:46]          /dev/shm/pulse-shm-3980750389: data
[10:03:46]          /dev/shm/pulse-shm-4142629559: data
[10:03:46]          /dev/shm/mono.9037: data
[10:03:46]          /dev/shm/pulse-shm-2122405511: data
[10:03:46]          /dev/shm/pulse-shm-974545630: data
[10:03:46]          /dev/shm/pulse-shm-2649592517: data
[10:03:46]          /dev/shm/mono.1978: data
[10:03:47]          /dev/shm/pulse-shm-13234652: data
[10:03:47]          /dev/shm/pulse-shm-922295506: AmigaOS bitmap font
[10:03:47]          /dev/shm/pulse-shm-3952461984: data
[10:03:47]   Checking for hidden files and directories       [ Warning ]
[10:03:47] Warning: Hidden directory found: /etc/.java
[10:03:47] Warning: Hidden directory found: /dev/.udev
[10:03:47] Warning: Hidden directory found: /dev/.initramfs

```


Thank you again for any help.

Erik

---

### Post by ErikShreve on 2010-02-10
Mystery solved. A website I was visiting included a link to inra.ir. Firefox was running dns requests on all links. Which I had thought about, but I wasn't aware Firefox had a DNS cache. The cache was keeping an OpenDNS warning from appearing again when I (earlier) tried re-visiting pages in the past to recreate the warning.

Thanks for your reply styxcoverbnd.

Erik

---

