---
title: "[SOLVED] apt-get update Could not resolve errors"
date: 2008-07-31
forum: Server Platforms
---

### Post by temp1029 on 2008-07-31
I have this server running on my network at work.  I attempt to run ```
sudo apt-get update
sudo aptitude update
``` and for every index file I get the error "Could not resolve xxxxx.xxxxx.xxxxx".

I have used the commands ```
dig us.archive.ubuntu.com
dig security.ubuntu.com
``` and they appear to resolve fine.

Since I have seen it requested numerous times, here is the output of 'cat /etc/apt/sources.list':
```
#
# deb cdrom:[Ubuntu-Server 8.04.1 _Hardy Heron_ - Release i386 (20080701)]/ hardy main restricted

#deb cdrom:[Ubuntu-Server 8.04.1 _Hardy Heron_ - Release i386 (20080701)]/ hardy main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://us.archive.ubuntu.com/ubuntu/ hardy main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ hardy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu/ hardy-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ hardy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://us.archive.ubuntu.com/ubuntu/ hardy universe
deb-src http://us.archive.ubuntu.com/ubuntu/ hardy universe
deb http://us.archive.ubuntu.com/ubuntu/ hardy-updates universe
deb-src http://us.archive.ubuntu.com/ubuntu/ hardy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://us.archive.ubuntu.com/ubuntu/ hardy multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ hardy multiverse
deb http://us.archive.ubuntu.com/ubuntu/ hardy-updates multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ hardy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://us.archive.ubuntu.com/ubuntu/ hardy-backports main restricted universe multiverse
# deb-src http://us.archive.ubuntu.com/ubuntu/ hardy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
# deb http://archive.canonical.com/ubuntu hardy partner
# deb-src http://archive.canonical.com/ubuntu hardy partner

deb http://security.ubuntu.com/ubuntu hardy-security main restricted
deb-src http://security.ubuntu.com/ubuntu hardy-security main restricted
deb http://security.ubuntu.com/ubuntu hardy-security universe
deb-src http://security.ubuntu.com/ubuntu hardy-security universe
deb http://security.ubuntu.com/ubuntu hardy-security multiverse
deb-src http://security.ubuntu.com/ubuntu hardy-security multiverse
```

Any help or suggestions would be appreciated.

---

### Post by windependence on 2008-08-01
What is in your /etc/resolv.conf?

-Tim

---

### Post by temp1029 on 2008-08-01
result of 'cat /etc/resolv.conf':
```
nameserver 10.0.0.11
nameserver 66.155.216.122
```

Just wanted to add that I am unsure what protocol the apt-get command uses to download the index files so I tried connecting to my web host's FTP server and when through a few commands, including get and put, without issue so I know nothing is configured to block FTP, if that is even relevant.

---

### Post by TreeFinger on 2008-08-01
is port 80 open on the server?

---

### Post by temp1029 on 2008-08-01
The result of running 'netstat -nap', which is the best way i know to check open ports, is:
```
Active Internet connections (servers and established)
Proto Recv-Q Send-Q Local Address           Foreign Address         State       PID/Program name
tcp        0      0 127.0.0.1:3306          0.0.0.0:*               LISTEN      4472/mysqld
tcp        0      0 0.0.0.0:139             0.0.0.0:*               LISTEN      4548/smbd
tcp        0      0 0.0.0.0:80              0.0.0.0:*               LISTEN      4617/apache2
tcp        0      0 0.0.0.0:445             0.0.0.0:*               LISTEN      4548/smbd
tcp6       0      0 :::22                   :::*                    LISTEN      4374/sshd
tcp6       0    340 10.0.10.57:22           10.0.10.51:3313         ESTABLISHED 5016/sshd: temp1029
udp        0      0 10.0.10.57:137          0.0.0.0:*                           4546/nmbd
udp        0      0 0.0.0.0:137             0.0.0.0:*                           4546/nmbd
udp        0      0 10.0.10.57:138          0.0.0.0:*                           4546/nmbd
udp        0      0 0.0.0.0:138             0.0.0.0:*                           4546/nmbd
udp        0      0 0.0.0.0:68              0.0.0.0:*                           3968/dhclient3

```

I'm guessing apt-get uses HTTP to get the index files then?

---

### Post by windependence on 2008-08-01
I'm sure having port 80 open is not your problem.

What is 10.0.0.11 on your network?

Also, try adding a third nameserver to your resolv.conf, but put it at the top. I use 2.2.2.4. You don't have to use your ISPs DNS servers and sometimes others are faster.

-Tim

---

### Post by windependence on 2008-08-01
> **TreeFinger said:**
> is port 80 open on the server?

If he can surf the web, 80 is open. most likely not his problem.

-Tim

---

### Post by Mumbly on 2008-08-02
Try to restart networking and see if that doesn't clear things up.
```
sudo /etc/init.d/networking restart
```

---

### Post by temp1029 on 2008-08-02
> **windependence said:**
> I'm sure having port 80 open is not your problem.

What is 10.0.0.11 on your network?

Also, try adding a third nameserver to your resolv.conf, but put it at the top. I use 2.2.2.4. You don't have to use your ISPs DNS servers and sometimes others are faster.

-Tim

10.0.0.11 is the local network's DNS server.  I tried putting 2.2.2.4 as the first, second and last line of the resolv.conf file and then doing '/etc/init.d/networking restart' and it appears to re-assert the previous state, with just the two nameserver lines.  Any other ideas?

I might bring this box home and plug it into my home network to see if it is a network or machine issue, although I'm not quite sure how the network it is currently on would block the apt-get request but allow other requests, any ideas here?

---

### Post by windependence on 2008-08-02
Are you running a lot of computers on your LAN (more than 10 or so)? If not, you probably don't need to be running a local DNS server. For some reason, here on the Ubuntu forums, everyone thinks they need to be running one of those. If you have a very large network, then yes, you need one but otherwise, it just adds more complexity to your network.

Obviously, it can't connect to the repositories. You could try substituting the actual IP of the repo servers in your sources list to eliminate the need for DNS lookup, OR you could add an entry for them in your /etc/hosts file which isn't a bad idea anyway because it eliminates the DNS lookup on the external DNS. The server checks that file first when resolving names so it's faster for any site you use frequently.

-Tim

---

### Post by temp1029 on 2008-08-02
> **windependence said:**
> Are you running a lot of computers on your LAN (more than 10 or so)? If not, you probably don't need to be running a local DNS server. For some reason, here on the Ubuntu forums, everyone thinks they need to be running one of those. If you have a very large network, then yes, you need one but otherwise, it just adds more complexity to your network.

There are about 50-60 computers running on this network, including a few people who connect via a VPN.

> **windependence said:**
> Obviously, it can't connect to the repositories. You could try substituting the actual IP of the repo servers in your sources list to eliminate the need for DNS lookup

What do I do about the sub-domains?  Sorry for my lack of knowledge here, but will it still work if I substitute all of it or what portion of the name do I substitute?

> **windependence said:**
> OR you could add an entry for them in your /etc/hosts file which isn't a bad idea anyway because it eliminates the DNS lookup on the external DNS. The server checks that file first when resolving names so it's faster for any site you use frequently.

-Tim

This solution makes sense to me, I'll try it and let you know the result.  My only concern is still the sub-domains, although I'd imagine these would be handled by the web server based on the information I was requesting.  Any help in better understanding this would be appreciated!

---

### Post by windependence on 2008-08-02
OK for example, [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) becomes:

[http://91.189.88.46/ubuntu/](http://91.189.88.46/ubuntu/)

In your hosts file you need only the main domain:

```
91.189.88.46     us.archive.ubuntu.com
```

Got it? :) You should restart the network after the changes.

-Tim

---

### Post by temp1029 on 2008-08-02
OK, looks like that did it, no more could not resolve errors!!

Just as a side note i had to add:
```
91.189.88.46    us.archive.ubuntu.com
91.189.88.46    security.ubuntu.com
```

But I wanted to know can I do this instead:
```
91.189.88.46    *.ubuntu.com
```

Seems to be working ok, just curious in case something changes in the future with the sub-domains, I don't want to be left guessing!!

Again, thanks for all the help, always find what I need on here!!

---

### Post by windependence on 2008-08-02
I don't think you even need the wildcard. I think 

```
91.189.88.46    ubuntu.com
```

will work just fine. You could even leave the other entries. Won't hurt anything.

BTW, glad to help. Keeps my skills sharp.

-Tim

---

### Post by temp1029 on 2008-08-02
Hmmmm, doesn't appear to work if i just put in 'ubuntu.com' for some reason, although I, just like you, thought that should work.  Not complaining though, just glad I found a workaround, thanks again!!

---

### Post by windependence on 2008-08-02
Well I wasn't sure about it. Now we know.

Glad you got it worked out.

-Tim

---

### Post by wickedbadawesome on 2008-08-06
i was having this problem as well and followed what you suggested about editing the /etc/hosts file - it worked. but this means for me that i am not communicating with a dns server at all - as this is a list for matching ip to a name. what do you think? i am using a ATT dsl router that acts as a gateway and DNS resolver i updated with apt-get update but can ping anyone.

---

### Post by Grwndi on 2009-07-17
I had this exact problem, and thought it silly that there wasn't a simple fix.

I checked my network config, and saw that I hadn't hooked up the server to the gateway on my router (don't ask me why my DHCP server isn't handling this: let's just say cheap router).

I set the correct value, restarted my networking, and it all just worked.

Yes, I'm dumb - but thought this might help some ;)

---

### Post by zachjacobs on 2009-07-23
I was able to solve this problem by doing a dhcp release/dhcp renew on my router.  Everything works great after that :)

---

### Post by windependence on 2009-07-24
Since you brought the thread back up, I need to make a correction as well. The DNS server I quoted should be 4.2.2.2, NOT 2.2.2.4.  You can use 4.2.2.2 thru 4.2.2.6.

-Tim

---

