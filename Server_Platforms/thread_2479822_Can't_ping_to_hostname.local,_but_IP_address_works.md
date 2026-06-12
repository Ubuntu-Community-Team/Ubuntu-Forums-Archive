---
title: "Can't ping to hostname.local, but IP address works"
date: 2022-10-09
forum: Server Platforms
---

### Post by japtar on 2022-10-09
Hello.  Dunno if this is the best place to ask this question, but I've recently installed Ubuntu 22.04.1 LTS server edition to my Mac Mini (I think it's circa 2012 model, very old) to hopefully host some home network services like NextCloud on Kubernetes.  I installed avahi-daemon yesterday, and was able to ping+ssh to the server at hostname.local, both via ethernet and wifi after installing bcmwl-kernel-source drivers.  Today, I'm unable to ping to hostname.local, and am currently using IP address instead, which is rather cumbersome.  I've searched online for some solutions without much avail, so I figured I'd ask here to tackle some potential solutions I may have missed in my search.

```
$ ping hostname.local
ping: hostname.local: Name or service not known
$ ping -c 3 10.0.0.170 
PING 10.0.0.170 (10.0.0.170) 56(84) bytes of data.
64 bytes from 10.0.0.170: icmp_seq=1 ttl=64 time=0.452 ms
64 bytes from 10.0.0.170: icmp_seq=2 ttl=64 time=0.357 ms
64 bytes from 10.0.0.170: icmp_seq=3 ttl=64 time=0.429 ms

--- 10.0.0.170 ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 2037ms
rtt min/avg/max/mdev = 0.357/0.412/0.452/0.040 ms
```

I dunno if this helps, but here's the avahi-daemon status:
```
$ sudo systemctl status avahi-daemon.service 
&#9679; avahi-daemon.service - Avahi mDNS/DNS-SD Stack
     Loaded: loaded (/lib/systemd/system/avahi-daemon.service; enabled; vendor preset: enabled)
     Active: active (running) since Sun 2022-10-09 03:48:58 UTC; 2s ago
TriggeredBy: &#9679; avahi-daemon.socket
   Main PID: 193153 (avahi-daemon)
     Status: "avahi-daemon 0.8 starting up."
      Tasks: 2 (limit: 4426)
     Memory: 832.0K
        CPU: 8ms
     CGroup: /system.slice/avahi-daemon.service
             &#9500;&#9472;193153 "avahi-daemon: running [hostname.local]"
             &#9492;&#9472;193154 "avahi-daemon: chroot helper"

Oct 09 03:48:58 hostname avahi-daemon[193153]: Successfully dropped remaining capabilities.
Oct 09 03:48:58 hostname avahi-daemon[193153]: No service file found in /etc/avahi/services.
Oct 09 03:48:58 hostname avahi-daemon[193153]: Joining mDNS multicast group on interface enp3s0f0.IPv6 with address 2601:249:8300:cc30::4ff1.
Oct 09 03:48:58 hostname avahi-daemon[193153]: New relevant interface enp3s0f0.IPv6 for mDNS.
Oct 09 03:48:58 hostname avahi-daemon[193153]: Joining mDNS multicast group on interface enp3s0f0.IPv4 with address 10.0.0.170.
Oct 09 03:48:58 hostname avahi-daemon[193153]: New relevant interface enp3s0f0.IPv4 for mDNS.
Oct 09 03:48:58 hostname avahi-daemon[193153]: Network interface enumeration completed.
Oct 09 03:48:58 hostname avahi-daemon[193153]: Registering new address record for 2601:249:8300:cc30::4ff1 on enp3s0f0.*.
Oct 09 03:48:58 hostname avahi-daemon[193153]: Registering new address record for 10.0.0.170 on enp3s0f0.IPv4.
Oct 09 03:48:59 hostname avahi-daemon[193153]: Server startup complete. Host name is hostname.local. Local service cookie is 66651886.
```

I did try editing /etc/avahi/avahi-daemon.conf:
```

[server]
use-ipv4=yes
use-ipv6=yes
allow-interfaces=enp3s0f0, wlp2s0
ratelimit-interval-usec=1000000
ratelimit-burst=1000

[wide-area]
enable-wide-area=yes

[publish]
publish-addresses=yes
publish-hinfo=no
publish-workstation=no

[reflector]

[rlimits]


```



I don't see avahi in netstat, which I'm not sure what that means:
```

$ netstat 
Active Internet connections (w/o servers)
Proto Recv-Q Send-Q Local Address           Foreign Address         State      
tcp        0      0 localhost:49674         localhost:9099          TIME_WAIT  
tcp        0      0 localhost:55944         localhost:19001         ESTABLISHED

tcp        0      0 hostname:36420        10.1.111.201:http-alt   TIME_WAIT  
tcp        0      0 hostname:35074        10.1.111.193:8000       TIME_WAIT  
tcp        0      0 localhost:35836         localhost:9099          TIME_WAIT  
tcp        0      0 hostname:40492        10.152.183.1:https      ESTABLISHED
tcp        0      0 hostname:57582        10.1.111.193:8000       ESTABLISHED
tcp        0      0 localhost:60220         localhost:9099          TIME_WAIT  
tcp        0      0 localhost:42660         localhost:9099          TIME_WAIT  
tcp        0      0 localhost:54596         localhost:9099          TIME_WAIT  
tcp        0      0 localhost:60208         localhost:9099          TIME_WAIT  
tcp        0      0 localhost:42676         localhost:9099          TIME_WAIT  
tcp        0      0 hostname:40456        10.152.183.1:https      ESTABLISHED
tcp        0      0 localhost:47928         localhost:9099          TIME_WAIT  
tcp        0    164 hostname:ssh          10.0.0.92:34076         ESTABLISHED
tcp        0      0 hostname:41170        10.152.183.181:https    ESTABLISHED
tcp        0      0 localhost:43154         localhost:9099          TIME_WAIT  
tcp        0      0 hostname:59192        10.1.111.201:8181       TIME_WAIT  
tcp        0      0 localhost:47920         localhost:9099          TIME_WAIT  
tcp        0      0 localhost:54594         localhost:9099          TIME_WAIT  
tcp        0      0 localhost:19001         localhost:55944         ESTABLISHED
tcp        0      0 localhost:40980         localhost:16443         ESTABLISHED
tcp        0      0 localhost:43168         localhost:9099          TIME_WAIT  
tcp        0      0 hostname:40446        10.152.183.1:https      ESTABLISHED
tcp        0      0 hostname:46220        10.1.111.201:8181       TIME_WAIT  
tcp        0      0 hostname:59232        10.152.183.181:https    ESTABLISHED
tcp        0      0 localhost:40972         localhost:16443         ESTABLISHED
tcp        0      0 localhost:40972         localhost:16443         ESTABLISHED
tcp6       0      0 hostname:16443        10.1.111.198:56934      ESTABLISHED
tcp6       0      0 hostname:16443        10.1.111.200:59272      ESTABLISHED
tcp6       0      0 hostname:16443        hostname:60130        ESTABLISHED
tcp6       0      0 hostname:16443        10.1.111.203:46234      ESTABLISHED
tcp6       0      0 hostname:16443        10.1.111.195:49638      ESTABLISHED
tcp6       0      0 ip6-localhost:45726     ip6-localhost:16443     ESTABLISHED
tcp6       0      0 ip6-localhost:16443     ip6-localhost:45726     ESTABLISHED
tcp6       0      0 localhost:16443         localhost:40980         ESTABLISHED
tcp6       0      0 hostname:16443        hostname:50753        ESTABLISHED
tcp6       0      0 hostname:16443        10.1.111.201:43348      ESTABLISHED
tcp6       0      0 localhost:16443         localhost:40972         ESTABLISHED
tcp6       0      0 hostname:16443        10.1.111.193:42800      ESTABLISHED
tcp6       0      0 hostname:10250        10.1.111.198:48616      ESTABLISHED
tcp6       0      0 hostname:16443        hostname:56562        ESTABLISHED
Active UNIX domain sockets (w/o servers)
Proto RefCnt Flags       Type       State         I-Node   Path
<snipping here, avahi doesn't appear in this list, either>

```



hosts looks...fine to me?
```
$ cat /etc/hosts
127.0.0.1 localhost
127.0.1.1 hostname

# The following lines are desirable for IPv6 capable hosts
::1     ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
```

---

### Post by The Cog on 2022-10-09
You can check if it's listening on the network - it uses UDP port 5353, and a seemingly random high port. e.g.:
```
$ sudo ss -lnup | cat
State  Recv-Q Send-Q                      Local Address:Port  Peer Address:PortProcess                                   
UNCONN 0      0                           127.0.0.53%lo:53         0.0.0.0:*    users:(("systemd-resolve",pid=754,fd=13))
UNCONN 0      0                                 0.0.0.0:631        0.0.0.0:*    users:(("cups-browsed",pid=1979,fd=7))   
UNCONN 0      0                                 0.0.0.0:5353       0.0.0.0:*    users:(("avahi-daemon",pid=816,fd=12))   
UNCONN 0      0                                 0.0.0.0:55762      0.0.0.0:*    users:(("avahi-daemon",pid=816,fd=14))   
UNCONN 0      0      [fe80::8288:f66b:983a:b934]%wlp1s0:546           [::]:*    users:(("NetworkManager",pid=822,fd=21)) 
UNCONN 0      0                                    [::]:5353          [::]:*    users:(("avahi-daemon",pid=816,fd=13))   
UNCONN 0      0                                    [::]:34038         [::]:*    users:(("avahi-daemon",pid=816,fd=15))   

```

---

### Post by TheFu on 2022-10-09
Avahi sucks. Servers aren't meant to have it.

Use DNS and set at least 1 static IP on the system.

ssh has a config file that is per individual which can be setup and all ssh-based tools will honor it for tab-completion.
~/.ssh/config
```
host xubu-22
  user deploy4200
  hostname 10.22.22.246
```

So, tab-completion for 'ssh xu{tab}' will fill in 'ssh xubu-22'  which becomes this command behind the scenes:
```
ssh deploy4200@10.22.22.246
```
Alternate users, ports, whatever, can be under different 'host' stanzas.  If you have different users to connect or rsync or backup using, add a different stanza.  The ~/.ssh/config is a handy file to document connections and users. Plus, you probably already backup the entire ~/.ssh/ directory for safety, right?

The easiest way to get more than just DNS is to setup a pi-hole system - mine runs inside an LXD container. A pi-hole nominally performs DNS ad and evil-parts-of-the-intern blocking, but it will use the /etc/hosts file on the pi-hole system as a DNS config file too, making all systems able to find each other.
[Https://ubuntuforums.org/showthread.php?t=2440863&p=13947454#post13947454](Https://ubuntuforums.org/showthread.php?t=2440863&p=13947454#post13947454)
A few months ago, the lxd pi-hole container was migrated to 20.04 (from 18.04). Easy.  Plus, all the ad blocking at the network layer is really needed these days.

The main reason I did this was so that our android devices would have access to internal servers. Without a proper (enough) DNS, those just don't work and all my attempts to find a workaround failed.  Bind is a bit overkill. I used to run bind ... before it was hacked. That was over 20 yrs ago now.

---

### Post by MAFoElffen on 2022-10-09
> **TheFu said:**
> Bind is a bit overkill....
I use Bind9... With a primary and secondary for my ***internal networks***. I do that, because that is what I know.

If no FQDN, then try IP, as you did. If IP and no FQDN, then no DNS resolv. Then I use 'dig' or' traceroute' to diagnose further. That is the part of my logical diagnostics tree of that. If "No DNS resolv" could mean a lot of things, depending on how the network and DNS is setup and configured... As the last 3 posts have uncovered. LOL

---

### Post by japtar on 2022-10-09
FacePalm.jpg

I didn't realize the other major difference between these two days was what client I was using: Windows and EndeavorOS (Arch Linux).  I just switched between the two to make sure, and it looks like Windows recognizes the hostname.local just fine, while EndeavorOS doesn't.  It's probably just a firewall issue on the client, rather than the server.

---

### Post by TheFu on 2022-10-10
Well, Linux may not be configured to look/use mDNS at all.  Servers wouldn't, at least I don't think they would.  Desktops probably would use mDNS, but I'd disable that and force DNS to be used myself.  No need to chatty protocols on our LAN here.

/etc/nsswitch.conf is the file which controls that for name resolution.
```
hosts:          files dns
```
is the line in my main 20.04 desktop.  I may have modified it. An 18.04 server looks the same.

A fresh (3 week old) 20.04 server install has this:
```
hosts:          files mdns4_minimal [NOTFOUND=return] dns mymachines
```
which I'll be fixing immediately.  Fixing is for my network, not yours. It explains some problems that specific new server has finding other systems too.  Thanks for the question. I may have not looked in that file for a few more months. Whenever I modify a file under /etc/, I add a tag to know it has been modified so that during a restore from backups any files I've touched get looked at carefully.

---

