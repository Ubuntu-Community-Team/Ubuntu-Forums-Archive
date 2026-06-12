---
title: "Apache starting before Network is up"
date: 2010-11-16
forum: Server Platforms
---

### Post by Wasca on 2010-11-16
Hi Guys

I've just completed a new 10.04.1 LTS 64bit server LAMP install. I've also add a sub interface to eth0 called eth0:1

When I start my server Apache is not starting and I'm seeing this error in my /var/log/boot.log file

```
fsck from util-linux-ng 2.17.2
fsck from util-linux-ng 2.17.2
/dev/mapper/apoch-root: clean, 91882/4669440 files, 688111/18654208 blocks
/dev/sda1: clean, 211/124496 files, 48619/248832 blocks
 * Starting AppArmor profiles       ^[[80G
^[[74G[ OK ]
 * Starting web server apache2       ^[[80G (99)Cannot assign requested address: make_sock: could not bind to address 203.xxx.xxx.xxx:80
no listening sockets available, shutting down
Unable to open logs

^[[74G[^[[31mfail^[[39;49m]
```

I've sanitised the log, but essentially it appears that the sub interface was not up before apache tried to use it.

I can confirm that the interface does come up once the boot process is complete.

```
eth0      Link encap:Ethernet  HWaddr 00:14:22:7c:4e:2b  
          inet addr:203.xxx.xxx.xxx  Bcast:203.xxx.xxx.xxx  Mask:255.255.255.224
          inet6 addr: fe80::214:22ff:fe7c:4e2b/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:166 errors:0 dropped:0 overruns:0 frame:0
          TX packets:88 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:19138 (19.1 KB)  TX bytes:20015 (20.0 KB)
          Interrupt:16 

eth0:1    Link encap:Ethernet  HWaddr 00:14:22:7c:4e:2b  
          inet addr:203.xxx.xxx.xxx  Bcast:203.xxx.xxx.xxx  Mask:255.255.255.224
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          Interrupt:16 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
```

As a crude fix I included a "sleep 5" command in the /etc/init.d/apache start up script at the "start" case

```
case $1 in
        start)
                log_daemon_msg "Starting web server" "apache2"
                sleep 5
                if $APACHE2CTL start; then
                        if check_htcacheclean ; then
                                log_progress_msg htcacheclean
                                start_htcacheclean || log_end_msg 1
                        fi
                        log_end_msg 0 
                else
                        log_end_msg 1
                fi
        ;;
``` 

Once this sleep command is there the system boots up perfectly. What I'd like to know is why is Apache trying to start up before the network interfaces have come up?

If anyone could help resolve this it would be great, I really dont want to have to sleep that "start" case by 5 seconds just to get this to work.

Thanks

---

### Post by arrrghhh on 2010-11-16
I think it's because the interface in question is virtual. 

See [this post](http://ubuntuforums.org/showpost.php?p=8609993&postcount=10), or [this](http://ubuntuforums.org/showpost.php?p=9273002&postcount=12), or the [thread](http://ubuntuforums.org/showthread.php?t=1360974) for some ideas.  I know I saw some other posts floating around as well, just can't find them ATM.

---

### Post by Wasca on 2010-11-16
So can some one tell me how to make apache start after the network interfaces have loaded (especially the sub interfaces)

Thanks

---

### Post by Wasca on 2010-11-16
OK good news, I got this sorted out. To make sure that apache did not start untill my sub-interface was up I did a small edit in /etc/init/rc-sysinit.conf

I changed this line

```
start on filesystem and net-device-up IFACE=lo
```

To include my sub-interface

```
start on filesystem and net-device-up IFACE=lo and net-device-up IFACE=eth0:1
```

I tried just using eth0 but that did not work I had to specify my sub-interface.

I hope this helps someone else.

---

### Post by arrrghhh on 2010-11-17
> **Wasca said:**
> I tried just using eth0 but that did not work I had to specify my sub-interface.

I hope this helps someone else.

Glad to hear you got it sorted.  Please use the "Thread Tools" drop-down menu to mark the thread '[SOLVED]' ;)

---

