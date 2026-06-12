---
title: "DNS Issues 18.04 Server"
date: 2018-05-02
forum: Server Platforms
---

### Post by frbastiat on 2018-05-02
I can't seem to get DNS to resolve on my fresh 18.04 server. I get 'connect: Network is unreachable' every time I ping google.com but it works if I ping 8.8.8.8.

My /etc/netplan/*.yaml is  

```
network:
    version: 2
    renderer: networkd
    ethernets:
        eno1:
            addresses: [10.0.2.10/24]
            gateway4: 10.0.2.1
            dhcp4: no
            nameservers:
                addresses: [8.8.8.8,8.8.4.4]
                #addresses: [208.67.222.222,208.67.220.220]

```

And systemd-resolve --status shows:  
    
```
Link 2 (eno1)
      Current Scopes: DNS
       LLMNR setting: yes
MulticastDNS setting: no
      DNSSEC setting: no
    DNSSEC supported: no
         DNS Servers: 208.67.222.222
                      208.67.220.220
```

Any suggestions?

---

### Post by jeremy31 on 2018-05-02
Moved to server platforms

---

### Post by TheFu on 2018-05-02
yaml is space/indentation sensitive, so if code-tags aren't used, we can't see the indentation levels.  Please edit the OP and correct.

---

### Post by frbastiat on 2018-05-02
Thanks, this is my first experience with netplan. So I checked my indentations based on your reply and noticed that I was using 2 spaces instead of 4 for the addresses potion of the nameservers. After updating that and restarting (not sure which service to restart for networking just yet) I was able to ping google.com just one time. Then back to failure.

```
17:33:02[frbastiat@server]~$ ping google.com
PING google.com (172.217.13.238) 56(84) bytes of data.
64 bytes from server (172.217.13.238): icmp_seq=1 ttl=55 time=7.89 ms
64 bytes from server (172.217.13.238): icmp_seq=2 ttl=55 time=6.80 ms
^C
--- google.com ping statistics ---
2 packets transmitted, 2 received, 0% packet loss, time 1001ms
rtt min/avg/max/mdev = 6.806/7.348/7.891/0.549 ms
17:33:12[frbastiat@server]~$ ping google.com
connect: Network is unreachable
```

---

### Post by TheFu on 2018-05-02
Yaml doesn't care if indentation is 2, 3 or 4 spaces, it just cares about consistency.

$ netplan --debug generate
[https://askubuntu.com/questions/961552/need-example-netplan-yaml-for-static-ip](https://askubuntu.com/questions/961552/need-example-netplan-yaml-for-static-ip) might be able to help.

I don't have netplan here, so can't help much with that. Sorry. 
[http://manpages.ubuntu.com/manpages/bionic/man5/netplan.5.html](http://manpages.ubuntu.com/manpages/bionic/man5/netplan.5.html) (or man netplan on your system) is really the best place for how it should work.  If they showed working examples in the manpages, that would be very helpful.  [https://insights.ubuntu.com/2017/12/01/ubuntu-bionic-netplan](https://insights.ubuntu.com/2017/12/01/ubuntu-bionic-netplan) should help.

Moving on for network issues ... 
Whenever there is any network issue, start by 
* pinging the router using the IP
* Then ping something external by IP.  This will clearly show if the problem is inside or outside your network. 
* Lastly, ping by name ... which tests DNS.  

DNS settings can be modified on the fly by a number of other tools, but the final answer for those settings, as far as I know is the /etc/resolv.conf file.

It appears you have at least 2 issues.  Sorry I'm not more help.

---

