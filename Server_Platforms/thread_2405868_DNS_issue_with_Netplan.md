---
title: "DNS issue with Netplan"
date: 2018-11-12
forum: Server Platforms
---

### Post by psd-joshe on 2018-11-12
I'm having an issue with Netplan(I believe) where after a few hours it will stop reading my nameservers. I can run ```
netplan apply
``` which will fix the issue temporarily, but then when I come back the next day the server appears to not be looking at my nameservers again.

for example If I run nslookup on the domain that is pointed at the server I get

```


Non-authoritative answer:
*** Can't find example.domain.com: No answer

```

Any ideas on how to make this stop? This has been an issue because when I call other files in with file_get_contents I get the error. ```
getaddrinfo failed: No address associated with hostname
```


Right now i'm just having to refresh my netplan by applying my config again periodically. To be clear I dont actually have to change the netplan config, I just have to run the command to apply it again to fix the problem.

---

### Post by TheFu on 2018-11-12
Is the IP networking all working still or just the DNS?  For example, can you ping the DNS server BEFORE doing any corrective action?

---

### Post by psd-joshe on 2018-11-12
The IP networking continues to work. It appears its just a DNS thing. I can still SSH in, I can ping it. It can ping out. Its like it just stops looking at the DNS server for whatever reason.

---

### Post by TheFu on 2018-11-12
That is helpful.

Does the /etc/resolv.conf still hold the correct information?

---

### Post by psd-joshe on 2018-11-13
When I run systemd-resolve --status it displays the correct IPs for our nameservers in the DNS Servers line. however if I cat the /etc/resolve file it says nameserver 127.0.0.53

edit: also as of this morning just running netplan apply is not correcting it anymore.

---

### Post by darkod on 2018-11-13
The .53 is normal for 18.04. It is called stub or what ever. If you look with netstat it will show that you have port 53 listening on 127.0.0.53. When that receives a dns request, it asks your dns servers in the background. My 18.04 works correctly like that.

```
darko@filesrv:~$ cat /etc/resolv.conf
# This file is managed by man:systemd-resolved(8). Do not edit.
#
# This is a dynamic resolv.conf file for connecting local clients to the
# internal DNS stub resolver of systemd-resolved. This file lists all
# configured search domains.
#
# Run "systemd-resolve --status" to see details about the uplink DNS servers
# currently in use.
#
# Third party programs must not access this file directly, but only through the
# symlink at /etc/resolv.conf. To manage man:resolv.conf(5) in a different way,
# replace this symlink by a static file or a different symlink.
#
# See man:systemd-resolved.service(8) for details about the supported modes of
# operation for /etc/resolv.conf.

nameserver 127.0.0.53
```

```
darko@filesrv:~$ sudo netstat -plunt | grep 53
[sudo] password for darko: 
tcp        0      0 127.0.0.53:53           0.0.0.0:*               LISTEN      4253/systemd-resolv 
tcp        0      0 192.168.122.1:53        0.0.0.0:*               LISTEN      2066/dnsmasq        
udp    39936      0 127.0.0.53:53           0.0.0.0:*                           4253/systemd-resolv 
udp        0      0 192.168.122.1:53        0.0.0.0:*                           2066/dnsmasq
```

```
darko@filesrv:~$ dig google.com

; <<>> DiG 9.11.3-1ubuntu1.2-Ubuntu <<>> google.com
;; global options: +cmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 50457
;; flags: qr rd ra; QUERY: 1, ANSWER: 1, AUTHORITY: 0, ADDITIONAL: 1

;; OPT PSEUDOSECTION:
; EDNS: version: 0, flags:; udp: 65494
;; QUESTION SECTION:
;google.com.   IN	A

;; ANSWER SECTION:
google.com.  299	IN	A	216.58.201.174

;; Query time: 78 msec
;; SERVER: 127.0.0.53#53(127.0.0.53)
;; WHEN: Tue Nov 13 18:40:12 CET 2018
;; MSG SIZE  rcvd: 55
```

Notice how the dig reply comes from 127.0.0.53?

---

### Post by darkod on 2018-11-13
Can you post your netplan file please?

---

### Post by psd-joshe on 2018-11-13
Here is my netplan file

```

server:/etc$ cat /etc/netplan/01-network-card.yaml 
network:
        version: 2
        renderer: networkd
        ethernets:
                enp2s0f0:
                        dhcp4: no
                        addresses: [158.91.4.26/24]
                        gateway4: 158.91.4.254
                        nameservers:
                                search: [provo.edu]
                                addresses: [158.91.5.199,158.91.5.203]


```

---

### Post by darkod on 2018-11-13
Are those tabs inside the text file? I have seen comments that it doesn't work correct with tabs. You should use space bar and correct indent. Like 3 spaces to the right of the previous line (when indent is needed).

---

### Post by psd-joshe on 2018-11-13
they are space bar spaces as I had netplan fail to apply when I did it with tabs. I had done it completely by hand in the past and have had the same results. where it will work onces I change the file for a day and then go back to ignoring the name servers.

My netplan config file looks like this now
```

server:/etc$ cat /etc/netplan/01-network-card.yaml 
network:
   version: 2
   renderer: networkd
   ethernets:
      enp2s0f0:
         dhcp4: no
         addresses: [158.91.4.26/24]
         gateway4: 158.91.4.254
         nameservers:
            search: [provo.edu]
            addresses: [158.91.5.199,158.91.5.203]

```

after doing a neplan generate, and netplan apply it is now working(as expected). I'll check back in if it stops working again tomorrow as it has previously.

---

### Post by darkod on 2018-11-13
OK.

One more question. Did you try rebooting the server or only netplan apply? I have seen on my server that apply sometimes is not doing it as expected. But I have never had any problems with a reboot.

---

### Post by psd-joshe on 2018-11-13
I do always try a reboot when it stops reading, but it has never actually fixed it. there for awhile it appeared just re applying the netplan config was fixing it but i'm starting to think it was me altering the config file then reapplying that was actually fixing it. 

Like I said it usually works for the day and then is not working when I come into the office the next day.

---

### Post by psd-joshe on 2018-11-14
the server stopped looking at the DNS server again.  Any other suggestions?

---

### Post by The Cog on 2018-11-14
Have you tried ```
renderer: NetworkManager
``` instead?
Or looked at /usr/lib/systemd/network to see what configuration netplan has written for networkd?

I would not blame netplan until I had ruled out a problem with systemd-networkd.

---

### Post by darkod on 2018-11-15
When it stops working, did you check if it's still listening on 127.0.0.53:53? You can use the commands I posted earlier and compare output.

If you tried using other packages that can control the networking you might end up with unexpected results. I use netplan in my newly reinstalled server with 18.04 and it worked out of the box. I was even able to easily set it up to use a bridge (because I have libvirt KVM) and it doesn't complain.

Mentioning NetworkManager, that package is not included in the server version by default, is it? I thought you have to add it yourself.

---

### Post by The Cog on 2018-11-15
> **darkod said:**
> Mentioning NetworkManager, that package is not included in the server version by default, is it? I thought you have to add it yourself.

Oops. I had not appreciated that. 

The the end of the day, I would probably end up using wireshark to see if it was sending DNS queries anywhere.

---

### Post by darkod on 2018-11-15
Like I thought. I just checked my server, network-manager is not installed by default.

```
darko@filesrv:~$ apt-cache policy network-manager
network-manager:
  Installed: (none)
  Candidate: 1.10.6-2ubuntu1.1
```

---

### Post by psd-joshe on 2018-11-26
I fixed this by adding a line in my hosts file that points the public IP to the domain name.

I'm not sure if you're supposed to do this or not. I just know that i've never had to do in the past with 14, 16. but I didn't have this problem on either OS previously. 

Anyway just posting an update for anyone who might happen accross this thread. This fixed myissue.

Thanks everyone for your help

---

### Post by rewen on 2019-03-03
> **psd-joshe said:**
> I fixed this by adding a line in my hosts file that points the public IP to the domain name.

I'm not sure if you're supposed to do this or not. I just know that i've never had to do in the past with 14, 16. but I didn't have this problem on either OS previously. 

Anyway just posting an update for anyone who might happen accross this thread. This fixed myissue.

Thanks everyone for your help

That's an unfortunate fix.

I am having the same issue. Every few days DNS stops working and it looks like 'netplan apply' fixes it. 

```

network:
    ethernets:
        ens192:
            addresses: []
            dhcp4: true
            optional: true
    version: 2

```

Nothing special going on.. Ubuntu Server 18.04 VM (in esxi) with a couple of docker containers (home-assistant, mosquitto, plex, sonarr, radarr).

I'll check if there's still anything listening on port 53 next time it happens..

---

### Post by rewen on 2019-03-09
It happened again

```
rewen@home-server:~/home-automation$ sudo netstat -anp | grep ':53 '
tcp        0      0 127.0.0.53:53           0.0.0.0:*               LISTEN      839/systemd-resolve 
udp        0      0 127.0.0.53:53           0.0.0.0:*                           839/systemd-resolve 
```

Looks like systemd-resolve is in fact listening on port 53 at the time

---

### Post by psd-joshe on 2019-03-11
so pointing your DNS name back to the server in your hosts file didn't fix this for you?

---

### Post by rewen on 2019-03-15
I don't suppose this thread's going to get any more attention since it's marked solved eh..

EDIT: Oh crap, didn't even see the replies. Nevermind

---

### Post by rewen on 2019-03-15
> **psd-joshe said:**
> so pointing your DNS name back to the server in your hosts file didn't fix this for you?

Adding the address of my DNS server to the netplan config helps (see below). The hosts file would help too, for the machines that's done on. But neither of those are fixes.. the problem is still there. Those are only workarounds that will fail if the network topology changes (eg getting a new router or moving the machine to another network). 

```
network:
    ethernets:
        ens192:
            addresses: []
            dhcp4: true
            optional: true
            nameservers:
                addresses: [192.168.86.1]


    version: 2
```

---

### Post by psd-joshe on 2019-03-21
sounds like your problem isn't quite the same the one I was having then. 

Mine was a DNS issue only related to itself. the actual DNS was always directing to the right place. 

the actual issue only came up when I was doing includes of files on the local machine based on static addresses. they would just say "couldn't resolve address" so just telling the local machine that my name name went back to itself so it didn't have to reach out to the DNS for that was able to solve my issue.

---

### Post by rewen on 2019-03-21
It may be different. This is the closest I've come to someone appearing to have the same issue.

My issue is simply that I can't resolve hostnames or internet domain names to IP addresses after a day or two. DNS just stops functioning, as if it forgot that my router is used for the DNS lookups. Manually specifying my router IP as the nameserver to use seems to have worked around the issue for the time being.

---

### Post by john-sweeney on 2019-05-24
I have this intermittent problem too. My workaround is to create a resolve.conf with a list of my internal DNS servers and a search domain-name line. It works but I still don't know what causes the problem

---

