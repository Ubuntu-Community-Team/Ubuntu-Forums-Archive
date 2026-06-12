---
title: "apt-get update showing proxy server error"
date: 2023-03-16
forum: Server Platforms
---

### Post by smit9522 on 2023-03-16
Hey guys,

As I am trying to update packages of my ubuntu server 22.10 which I am using it as a remote server. As I am sure that there is no error in DNS because I did ping 8.8.8.8 and 8.8.4.4 which are working perfectly.

I am not sure with my ufw firewall port. And do let me know is I have my mistakenly opened any wrong ports or ports that can be easy to hack...

ufw firewall status
```

root@ubuntu:~# sudo ufw status
Status: active


To                         Action      From
--                         ------      ----
10000                      ALLOW       Anywhere                  
22/tcp                     ALLOW       Anywhere                  
80/tcp                     ALLOW       Anywhere                  
443                        ALLOW       Anywhere                  
80                         ALLOW       Anywhere                  
53                         ALLOW       Anywhere                  
443/tcp                    ALLOW       Anywhere                  
9200                       ALLOW       Anywhere                  
10000 (v6)                 ALLOW       Anywhere (v6)             
22/tcp (v6)                ALLOW       Anywhere (v6)             
80/tcp (v6)                ALLOW       Anywhere (v6)             
80 (v6)                    ALLOW       Anywhere (v6)             
53 (v6)                    ALLOW       Anywhere (v6)             
443/tcp (v6)               ALLOW       Anywhere (v6)             
443 (v6)                   ALLOW       Anywhere (v6)             
9200 (v6)                  ALLOW       Anywhere (v6)

```

Error that it's showing
```
root@ubuntu:~# sudo apt-get update
Ign:1 http://download.opensuse.org/repositories/isv:/ownCloud:/server:/10/Ubuntu_21.10  InRelease
Ign:2 http://ports.ubuntu.com/ubuntu-ports kinetic InRelease
Ign:3 https://ppa.launchpadcontent.net/ondrej/php/ubuntu kinetic InRelease
Ign:4 http://ports.ubuntu.com/ubuntu-ports kinetic-updates InRelease
Ign:5 http://ports.ubuntu.com/ubuntu-ports kinetic-backports InRelease
Ign:6 http://ports.ubuntu.com/ubuntu-ports kinetic-security InRelease
Ign:1 http://download.opensuse.org/repositories/isv:/ownCloud:/server:/10/Ubuntu_21.10  InRelease
Ign:2 http://ports.ubuntu.com/ubuntu-ports kinetic InRelease
Ign:3 https://ppa.launchpadcontent.net/ondrej/php/ubuntu kinetic InRelease
Ign:4 http://ports.ubuntu.com/ubuntu-ports kinetic-updates InRelease
Ign:5 http://ports.ubuntu.com/ubuntu-ports kinetic-backports InRelease
Ign:6 http://ports.ubuntu.com/ubuntu-ports kinetic-security InRelease
Ign:1 http://download.opensuse.org/repositories/isv:/ownCloud:/server:/10/Ubuntu_21.10  InRelease
Ign:2 http://ports.ubuntu.com/ubuntu-ports kinetic InRelease
Ign:3 https://ppa.launchpadcontent.net/ondrej/php/ubuntu kinetic InRelease
Ign:4 http://ports.ubuntu.com/ubuntu-ports kinetic-updates InRelease
Ign:5 http://ports.ubuntu.com/ubuntu-ports kinetic-backports InRelease
Ign:6 http://ports.ubuntu.com/ubuntu-ports kinetic-security InRelease
Err:1 http://download.opensuse.org/repositories/isv:/ownCloud:/server:/10/Ubuntu_21.10  InRelease
  Temporary failure resolving 'proxyserver'
Err:2 http://ports.ubuntu.com/ubuntu-ports kinetic InRelease
  Temporary failure resolving 'proxyserver'
Err:3 https://ppa.launchpadcontent.net/ondrej/php/ubuntu kinetic InRelease
  Temporary failure resolving 'proxyserver'
Err:4 http://ports.ubuntu.com/ubuntu-ports kinetic-updates InRelease
  Temporary failure resolving 'proxyserver'
Err:5 http://ports.ubuntu.com/ubuntu-ports kinetic-backports InRelease
  Temporary failure resolving 'proxyserver'
Err:6 http://ports.ubuntu.com/ubuntu-ports kinetic-security InRelease
  Temporary failure resolving 'proxyserver'
Reading package lists... Done
W: Failed to fetch http://ports.ubuntu.com/ubuntu-ports/dists/kinetic/InRelease  Temporary failure resolving 'proxyserver'
W: Failed to fetch http://ports.ubuntu.com/ubuntu-ports/dists/kinetic-updates/InRelease  Temporary failure resolving 'proxyserver'
W: Failed to fetch http://ports.ubuntu.com/ubuntu-ports/dists/kinetic-backports/InRelease  Temporary failure resolving 'proxyserver'
W: Failed to fetch http://ports.ubuntu.com/ubuntu-ports/dists/kinetic-security/InRelease  Temporary failure resolving 'proxyserver'
W: Failed to fetch http://download.opensuse.org/repositories/isv:/ownCloud:/server:/10/Ubuntu_21.10/InRelease  Temporary failure resolving 'proxyserver'
W: Failed to fetch https://ppa.launchpadcontent.net/ondrej/php/ubuntu/dists/kinetic/InRelease  Temporary failure resolving 'proxyserver'
W: Some index files failed to download. They have been ignored, or old ones used instead.

```

Also update on stack exchange : [https://askubuntu.com/q/1459685/1681992](https://askubuntu.com/q/1459685/1681992)

---

### Post by DuckHook on 2023-03-16
*Thread moved to **Server Platforms** as the more appropriate forum.*

---

### Post by MAFoElffen on 2023-03-19
First, if you post in multiple places, such as the thread you have going on at Reddit, you should, by netiquet, post the URL's of the other thread, that way people are informed and not chasing ghosts.

Also, I see that if other places, you post different information. Such as it would be informative to know (here) that the specific server is ARM64 on RaspPi.
```

Err:1 http://download.opensuse.org/repositories/isv:/ownCloud:/server:/10/Ubuntu_21.10  InRelease
  Temporary failure resolving 'proxyserver'
Err:2 http://ports.ubuntu.com/ubuntu-ports kinetic InRelease
  Temporary failure resolving 'proxyserver'
Err:3 https://ppa.launchpadcontent.net/ondrej/php/ubuntu kinetic InRelease
  Temporary failure resolving 'proxyserver'
Err:4 http://ports.ubuntu.com/ubuntu-ports kinetic-updates InRelease
  Temporary failure resolving 'proxyserver'
Err:5 http://ports.ubuntu.com/ubuntu-ports kinetic-backports InRelease
  Temporary failure resolving 'proxyserver'
Err:6 http://ports.ubuntu.com/ubuntu-ports kinetic-security InRelease
  Temporary failure resolving 'proxyserver'
Reading package lists... Done

```
Hmmm. I can get to these with no problems. And if it was just one specific repo, then I would think that is was a problem with the target Repo being down for maintenance. But it is not.

On: 
```

http://download.opensuse.org/repositories/isv:/ownCloud:/server:/10/Ubuntu_21.10  InRelease

```
I have questions and... Well. You say you have an Ubuntu Server 22.10. Why are you using and pointing to the 21.10 repo? Instead of, let's say
```

http://download.opensuse.org/repositories/isv:/ownCloud:/server:/10/Ubuntu_22.10/

```
Which is the repo that matches what you are running... 

Next, why only OpenCloud version 10? Current is 10.12.0
```

http://download.opensuse.org/repositories/isv:/ownCloud:/server:/10.12.0/Ubuntu_22.10/

```
Just a curiosity, and an observation...

You asked about port open for apt... apt transfer method uses:  (HTTP (TCP 80), HTTPS (TCP 443), FTP (TCP 21), or others.  If you use a proxy, there's additional ports based on your configuration that you'll need to tweak as well.

I think you have a misunderstanding in this statement:
[quote=smit9522]
As *[COLOR=#ff0000]I am sure that there is no error in DNS[/COLOR]* because I did ping 8.8.8.8 and 8.8.4.4 which are working perfectly.
[/quote]
Pinging 8.8.8.8 (Google DNS) will tell you you have a connection to Google DNS via it's IP address, but that is not DNS... Pinging [www.google.com]("http://www.google.com") (the same destination) will tell you that you have resolv, DNS name resolution.

For example, both of these are to [www.opensuse.org:]("http://www.opensuse.org:")
```

mafoelffen@Mikes-ThinkPad-T520:~$ ping -c 4 -6 2001:67c:2178:8::16
PING 2001:67c:2178:8::16(2001:67c:2178:8::16) 56 data bytes
64 bytes from 2001:67c:2178:8::16: icmp_seq=1 ttl=33 time=176 ms
64 bytes from 2001:67c:2178:8::16: icmp_seq=2 ttl=33 time=173 ms
64 bytes from 2001:67c:2178:8::16: icmp_seq=3 ttl=33 time=173 ms
64 bytes from 2001:67c:2178:8::16: icmp_seq=4 ttl=33 time=172 ms

--- 2001:67c:2178:8::16 ping statistics ---
4 packets transmitted, 4 received, 0% packet loss, time 3005ms
rtt min/avg/max/mdev = 171.879/173.317/175.809/1.492 ms
mafoelffen@Mikes-ThinkPad-T520:~$ ping -c 4 www.opensuse.org
PING www.opensuse.org(proxy-nue.opensuse.org (2001:67c:2178:8::16)) 56 data bytes
64 bytes from proxy-nue.opensuse.org (2001:67c:2178:8::16): icmp_seq=1 ttl=33 time=175 ms
64 bytes from proxy-nue.opensuse.org (2001:67c:2178:8::16): icmp_seq=2 ttl=33 time=171 ms
64 bytes from proxy-nue.opensuse.org (2001:67c:2178:8::16): icmp_seq=3 ttl=33 time=175 ms
64 bytes from proxy-nue.opensuse.org (2001:67c:2178:8::16): icmp_seq=4 ttl=33 time=174 ms

--- www.opensuse.org ping statistics ---
4 packets transmitted, 4 received, 0% packet loss, time 3004ms
rtt min/avg/max/mdev = 171.162/173.837/175.390/1.631 ms

```
Please try:
```

mafoelffen@Mikes-ThinkPad-T520:~$ dig http://www.opensuse.org

; <<>> DiG 9.18.1-1ubuntu1.3-Ubuntu <<>> http://www.opensuse.org
;; global options: +cmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NXDOMAIN, id: 60787
;; flags: qr rd ra; QUERY: 1, ANSWER: 0, AUTHORITY: 1, ADDITIONAL: 1

;; OPT PSEUDOSECTION:
; EDNS: version: 0, flags:; udp: 65494
;; QUESTION SECTION:
;http://www.opensuse.org.    IN    A

;; AUTHORITY SECTION:
opensuse.org.        1800    IN    SOA    ns1.opensuse.org. admin.opensuse.org. 2023031601 7200 7200 604800 3600

;; Query time: 100 msec
;; SERVER: 127.0.0.53#53(127.0.0.53) (UDP)
;; WHEN: Sun Mar 19 03:11:06 PDT 2023
;; MSG SIZE  rcvd: 98

```

---

### Post by smit9522 on 2023-03-22
So, as you said that the respo is of older version and I did notice that thing and I would like to that what steps would be better to download and run it as update is not working.

> [COLOR=#000000]On:[/COLOR]
[COLOR=#000000]
```
http://download.opensuse.org/repositories/isv:/ownCloud:/server:/10/Ubuntu_21.10  InRelease

```[/COLOR]
[COLOR=#000000]I have questions and... Well. You say you have an Ubuntu Server 22.10. Why are you using and pointing to the 21.10 repo? Instead of, let's say
[/COLOR][COLOR=#000000]
[/COLOR]```
[COLOR=#000000]http://[/COLOR]download.opensuse.org/repositories/isv:/ownCloud:/server:/10/Ubuntu_22.10/[COLOR=#000000]
[/COLOR]
```
[COLOR=#000000]Which is the repo that matches what you are running...

[/COLOR][COLOR=#000000]Next, why only OpenCloud version 10? Current is 10.12.0[/COLOR]
[COLOR=#000000]
[/COLOR]```
[COLOR=#000000]http://[/COLOR]download.opensuse.org/repositories/isv:/ownCloud:/server:/10.12.0/Ubuntu_22.10/
```


Now, as you said me to try
```
[COLOR=#000000]dig http://www.opensuse.org[/COLOR]
```

which came the output as
```
root@ubuntu:~# dig http://www.opensuse.org


; <<>> DiG 9.18.4-2ubuntu2.1-Ubuntu <<>> http://www.opensuse.org
;; global options: +cmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NXDOMAIN, id: 31674
;; flags: qr rd ra; QUERY: 1, ANSWER: 0, AUTHORITY: 1, ADDITIONAL: 1


;; OPT PSEUDOSECTION:
; EDNS: version: 0, flags:; udp: 65494
;; QUESTION SECTION:
;http://www.opensuse.org.       IN      A


;; AUTHORITY SECTION:
opensuse.org.           1800    IN      SOA     ns1.opensuse.org. admin.opensuse.org. 2023032301 7200 7200 604800 3600


;; Query time: 584 msec
;; SERVER: 127.0.0.53#53(127.0.0.53) (UDP)
;; WHEN: Thu Mar 23 03:41:52 UTC 2023
;; MSG SIZE  rcvd: 98

```

Now, damn there is twist that there were somewhat 30 packages pending to update and now there are none and yet the error is been shown

```
root@ubuntu:~# sudo apt-get update
Ign:1 http://download.opensuse.org/repositories/isv:/ownCloud:/server:/10/Ubuntu_21.10  InRelease
Ign:2 http://ports.ubuntu.com/ubuntu-ports kinetic InRelease
Ign:3 https://ppa.launchpadcontent.net/ondrej/php/ubuntu kinetic InRelease
Ign:4 http://ports.ubuntu.com/ubuntu-ports kinetic-updates InRelease
Ign:5 http://ports.ubuntu.com/ubuntu-ports kinetic-backports InRelease
Ign:6 http://ports.ubuntu.com/ubuntu-ports kinetic-security InRelease
Ign:2 http://ports.ubuntu.com/ubuntu-ports kinetic InRelease
Ign:1 http://download.opensuse.org/repositories/isv:/ownCloud:/server:/10/Ubuntu_21.10  InRelease
Ign:3 https://ppa.launchpadcontent.net/ondrej/php/ubuntu kinetic InRelease
Ign:4 http://ports.ubuntu.com/ubuntu-ports kinetic-updates InRelease
Ign:5 http://ports.ubuntu.com/ubuntu-ports kinetic-backports InRelease
Ign:6 http://ports.ubuntu.com/ubuntu-ports kinetic-security InRelease
Ign:1 http://download.opensuse.org/repositories/isv:/ownCloud:/server:/10/Ubuntu_21.10  InRelease
Ign:2 http://ports.ubuntu.com/ubuntu-ports kinetic InRelease
Ign:3 https://ppa.launchpadcontent.net/ondrej/php/ubuntu kinetic InRelease
Ign:4 http://ports.ubuntu.com/ubuntu-ports kinetic-updates InRelease
Ign:5 http://ports.ubuntu.com/ubuntu-ports kinetic-backports InRelease
Ign:6 http://ports.ubuntu.com/ubuntu-ports kinetic-security InRelease
Err:1 http://download.opensuse.org/repositories/isv:/ownCloud:/server:/10/Ubuntu_21.10  InRelease
  Temporary failure resolving 'proxyserver'
Err:2 http://ports.ubuntu.com/ubuntu-ports kinetic InRelease
  Temporary failure resolving 'proxyserver'
Err:3 https://ppa.launchpadcontent.net/ondrej/php/ubuntu kinetic InRelease
  Temporary failure resolving 'proxyserver'
Err:4 http://ports.ubuntu.com/ubuntu-ports kinetic-updates InRelease
  Temporary failure resolving 'proxyserver'
Err:5 http://ports.ubuntu.com/ubuntu-ports kinetic-backports InRelease
  Temporary failure resolving 'proxyserver'
Err:6 http://ports.ubuntu.com/ubuntu-ports kinetic-security InRelease
  Temporary failure resolving 'proxyserver'
Reading package lists... Done
W: Failed to fetch http://ports.ubuntu.com/ubuntu-ports/dists/kinetic/InRelease  Temporary failure resolving 'proxyserver'
W: Failed to fetch http://ports.ubuntu.com/ubuntu-ports/dists/kinetic-updates/InRelease  Temporary failure resolving 'proxyserver'
W: Failed to fetch http://ports.ubuntu.com/ubuntu-ports/dists/kinetic-backports/InRelease  Temporary failure resolving 'proxyserver'
W: Failed to fetch http://ports.ubuntu.com/ubuntu-ports/dists/kinetic-security/InRelease  Temporary failure resolving 'proxyserver'
W: Failed to fetch http://download.opensuse.org/repositories/isv:/ownCloud:/server:/10/Ubuntu_21.10/InRelease  Temporary failure resolving 'proxyserver'
W: Failed to fetch https://ppa.launchpadcontent.net/ondrej/php/ubuntu/dists/kinetic/InRelease  Temporary failure resolving 'proxyserver'
W: Some index files failed to download. They have been ignored, or old ones used instead.
root@ubuntu:~# sudo apt-get update --list
E: Command line option --list is not understood in combination with the other options
root@ubuntu:~# sudo update --list
sudo: update: command not found
root@ubuntu:~# apt list --upgradable
Listing... Done
root@ubuntu:~# sudo apt list --upgradable
Listing... Done
root@ubuntu:~# apt list --upgradable | grep "\-security"


WARNING: apt does not have a stable CLI interface. Use with caution in scripts.


root@ubuntu:~# sudo cat /var/lib/update-notifier/updates-available


0 updates can be applied immediately.
```

I am using webmin to give my ubuntu server a small GUI and there it showed me that 30 packages pending to update after trying out different stuffs to solve the errors for few days and then the updates went away. As I am sure that it was not a bug as my webmin did update to newer version.

You can see I have marked in red box and all the other required details are given in the image

[IMG]https://ubuntuforums.org/attachment.php?attachmentid=291940&stc=1[/IMG]

---

### Post by MAFoElffen on 2023-03-23
I don't see where you answered if you had a proxy configured somewhere(?)

It still is having a DNS challenge somewhere, somehow.

Have you tried testing repetively with traceroute?

---

### Post by smit9522 on 2023-03-23
No I have note configured any proxy server anywhere.

below are the methods that I used to check if any proxy server are made:

```
root@ubuntu:~# echo $http_proxy


root@ubuntu:~# 

```

```
root@ubuntu:~# sudo cat /etc/apt/apt.conf
Acquire::http::Proxy "http://proxyserver:port";
root@ubuntu:~# 

```

As I am not able to install traceroute

```
E: Package 'traceroute' has no installation candidate
root@ubuntu:~# apt install traceroute
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
Package traceroute is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source


E: Package 'traceroute' has no installation candidate
root@ubuntu:~# 

```

This error is common as it is not allowing me to install anything

```
root@ubuntu:~# sudo apt install python3-pip
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
E: Unable to locate package python3-pip

```

I am very much confused and have zero idea what to do please ask anything you need I'll let you everything.

---

### Post by MAFoElffen on 2023-03-24
Wow... Your apt system seems to be trashed.
```

mafoelffen@Mikes-ThinkPad-T520:~/Scripts$ apt list traceroute --installed
Listing... Done
traceroute/jammy,now 1:2.1.0-2 amd64 [installed]
mafoelffen@Mikes-ThinkPad-T520:~/Scripts$ apt-cache show traceroute
Package: traceroute
Architecture: amd64
Version: 1:2.1.0-2
Priority: optional
Section: universe/net
Origin: Ubuntu
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Original-Maintainer: Laszlo Boszormenyi (GCS) <gcs@debian.org>
Bugs: https://bugs.launchpad.net/ubuntu/+filebug
Installed-Size: 148
Depends: libc6 (>= 2.14)
Filename: pool/universe/t/traceroute/traceroute_2.1.0-2_amd64.deb
Size: 45386
MD5sum: aaeda2e2d75c065b0c42622a230edb2e
SHA1: dfa8299bd3f99920d6b8514e1c9b940b8029cb38
SHA256: f04499e59e7dab53c2ba50da052ca5338cb66da08d93ff8662a11a0a1a904dff
SHA512: 25beb696cb067a37c63f1e9a4485afc63d357039e00942240f6c8447033352ebfbd01395712c97a1027efa0d918e834695b8ce35ff848640712db517bf2c838a
Homepage: http://traceroute.sourceforge.net/
Description-en: Traces the route taken by packets over an IPv4/IPv6 network
 The traceroute utility displays the route used by IP packets on their way to a
 specified network (or Internet) host. Traceroute displays the IP number and
 host name (if possible) of the machines along the route taken by the packets.
 Traceroute is used as a network debugging tool. If you're having network
 connectivity problems, traceroute will show you where the trouble is coming
 from along the route.
 .
 Install traceroute if you need a tool for diagnosing network connectivity
 problems.
Description-md5: 8a3a47eccb961a38576ee994d96f3d2c

```
[s]My condolences.

In 17 years of using Linux, I have not found any successful methods to "reinstall" a broken apt system in Debian, without doing a fresh install. It takes reinstalling the base system. And hard to do that without apt working or from dpkg...

My suggestions would be to do a good backup. Install fresh. Install the manually installed packages. Migrate your data, configs, and settings to the new installation.

To easily get a list of your manually installed package, run the [UbuntuForums 'system-info' script]("https://github.com/UbuntuForums/system-info"), and look near the end of the report. I use that part of the report (the list of packages) to create a post-installation script for migrations.[/s]

[SIZE=3][COLOR=#ff0000]EDIT:[/COLOR][/SIZE]
I went back and looked at your last post...

You said you have no proxy's setup, but when you did this:
> ```
root@ubuntu:~# sudo cat /etc/apt/apt.conf
Acquire::http::Proxy "http://proxyserver:port";
root@ubuntu:~#

```
That is a proxy statement... in a file you created, because apt.conf is not there by default in that directory, and not in that format.

First do this
```

sudo mv /etc/apt/apt.conf /etc/apt/apt.conf.bak

```
I would verify there is no more there
```

grep -i "proxy" /etc/apt/*
grep -i "proxy" /etc/apt/apt.conf.d/*

```

---

### Post by smit9522 on 2023-03-25
Is there anything that can be done as it is yet a new server and what I tried is to make a server where I would host webmin for my part and ownCloud infinite scale for my staff for storing there work data which can be used even remotely.

I don't know what to do as its still not working 

```
root@ubuntu:~# sudo mv /etc/apt/apt.conf /etc/apt/apt.conf.bak
root@ubuntu:~# grep -i "proxy" /etc/apt/*
/etc/apt/apt.conf.bak:Acquire::http::Proxy "http://proxyserver:port";
grep: /etc/apt/apt.conf.d: Is a directory
/etc/apt/apt.conf.save:#Acquire::http::Proxy "http://proxyserver:port";
/etc/apt/apt.conf.save:Acquire::http::Proxy "http://
/etc/apt/apt.conf.save:Acquire::https::Proxy "http://ubuntu:password@proxyserver:port/";
grep: /etc/apt/auth.conf.d: Is a directory
grep: /etc/apt/keyrings: Is a directory
grep: /etc/apt/preferences.d: Is a directory
grep: /etc/apt/sources.list.d: Is a directory
grep: /etc/apt/trusted.gpg.d: Is a directory
root@ubuntu:~# grep -i "proxy" /etc/apt/apt.conf.d/*
root@ubuntu:~# apt install traceroute
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
Package traceroute is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source


E: Package 'traceroute' has no installation candidate
root@ubuntu:~# ~/Scripts$ apt list traceroute --installed
-bash: /root/Scripts$: No such file or directory
root@ubuntu:~#  apt list traceroute --installed
Listing... Done
root@ubuntu:~# apt-cache show traceroute
N: Can't select versions from package 'traceroute' as it is purely virtual
N: No packages found
root@ubuntu:~# sudo apt install python3-pip
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
E: Unable to locate package python3-pip
root@ubuntu:~# 

```

As once I did
```
sudo apt-get update
```

and did work but there some error as you might see
```
root@ubuntu:~# sudo apt-get update
Get:1 http://ports.ubuntu.com/ubuntu-ports kinetic InRelease [267 kB]
Get:2 http://download.opensuse.org/repositories/isv:/ownCloud:/server:/10/Ubuntu_21.10  InRelease [1535 B]
Get:3 http://download.opensuse.org/repositories/isv:/ownCloud:/server:/10/Ubuntu_21.10  Packages [888 B]    
Ign:4 https://ppa.launchpadcontent.net/ondrej/php/ubuntu kinetic InRelease  
Get:5 http://ports.ubuntu.com/ubuntu-ports kinetic-updates InRelease [118 kB]
Get:6 http://ports.ubuntu.com/ubuntu-ports kinetic-backports InRelease [99.9 kB]           
Get:7 http://ports.ubuntu.com/ubuntu-ports kinetic-security InRelease [109 kB]               
Err:8 https://ppa.launchpadcontent.net/ondrej/php/ubuntu kinetic Release                  
  404  Not Found [IP: 185.125.190.52 443]
Get:9 http://ports.ubuntu.com/ubuntu-ports kinetic/main arm64 Packages [1363 kB]
Get:10 http://ports.ubuntu.com/ubuntu-ports kinetic/main Translation-en [509 kB]
Get:11 http://ports.ubuntu.com/ubuntu-ports kinetic/main arm64 c-n-f Metadata [29.7 kB]
Get:12 http://ports.ubuntu.com/ubuntu-ports kinetic/restricted arm64 Packages [48.6 kB]
Get:13 http://ports.ubuntu.com/ubuntu-ports kinetic/restricted Translation-en [18.0 kB]
Get:14 http://ports.ubuntu.com/ubuntu-ports kinetic/restricted arm64 c-n-f Metadata [372 B]
Get:15 http://ports.ubuntu.com/ubuntu-ports kinetic/universe arm64 Packages [14.2 MB]
Get:16 http://ports.ubuntu.com/ubuntu-ports kinetic/universe Translation-en [5791 kB]                                                                 
Get:17 http://ports.ubuntu.com/ubuntu-ports kinetic/universe arm64 c-n-f Metadata [281 kB]                                                            
Get:18 http://ports.ubuntu.com/ubuntu-ports kinetic/multiverse arm64 Packages [194 kB]                                                                
Get:19 http://ports.ubuntu.com/ubuntu-ports kinetic/multiverse Translation-en [112 kB]                                                                
Get:20 http://ports.ubuntu.com/ubuntu-ports kinetic/multiverse arm64 c-n-f Metadata [7084 B]                                                          
Get:21 http://ports.ubuntu.com/ubuntu-ports kinetic-updates/main arm64 Packages [356 kB]                                                              
Get:22 http://ports.ubuntu.com/ubuntu-ports kinetic-updates/main Translation-en [97.7 kB]                                                             
Get:23 http://ports.ubuntu.com/ubuntu-ports kinetic-updates/main arm64 c-n-f Metadata [7760 B]                                                        
Get:24 http://ports.ubuntu.com/ubuntu-ports kinetic-updates/restricted arm64 Packages [174 kB]                                                        
Get:25 http://ports.ubuntu.com/ubuntu-ports kinetic-updates/restricted Translation-en [39.9 kB]                                                       
Get:26 http://ports.ubuntu.com/ubuntu-ports kinetic-updates/restricted arm64 c-n-f Metadata [412 B]                                                   
Get:27 http://ports.ubuntu.com/ubuntu-ports kinetic-updates/universe arm64 Packages [249 kB]                                                          
Get:28 http://ports.ubuntu.com/ubuntu-ports kinetic-updates/universe Translation-en [97.3 kB]                                                         
Get:29 http://ports.ubuntu.com/ubuntu-ports kinetic-updates/universe arm64 c-n-f Metadata [8400 B]                                                    
Get:30 http://ports.ubuntu.com/ubuntu-ports kinetic-updates/multiverse arm64 Packages [3060 B]                                                        
Get:31 http://ports.ubuntu.com/ubuntu-ports kinetic-updates/multiverse Translation-en [1412 B]                                                        
Get:32 http://ports.ubuntu.com/ubuntu-ports kinetic-updates/multiverse arm64 c-n-f Metadata [244 B]                                                   
Get:33 http://ports.ubuntu.com/ubuntu-ports kinetic-backports/main arm64 c-n-f Metadata [112 B]                                                       
Get:34 http://ports.ubuntu.com/ubuntu-ports kinetic-backports/restricted arm64 c-n-f Metadata [120 B]                                                 
Get:35 http://ports.ubuntu.com/ubuntu-ports kinetic-backports/universe arm64 Packages [4240 B]                                                        
Get:36 http://ports.ubuntu.com/ubuntu-ports kinetic-backports/universe Translation-en [1516 B]                                                        
Get:37 http://ports.ubuntu.com/ubuntu-ports kinetic-backports/universe arm64 c-n-f Metadata [196 B]                                                   
Get:38 http://ports.ubuntu.com/ubuntu-ports kinetic-backports/multiverse arm64 c-n-f Metadata [120 B]                                                 
Get:39 http://ports.ubuntu.com/ubuntu-ports kinetic-security/main arm64 Packages [259 kB]                                                             
Get:40 http://ports.ubuntu.com/ubuntu-ports kinetic-security/main Translation-en [69.9 kB]                                                            
Get:41 http://ports.ubuntu.com/ubuntu-ports kinetic-security/main arm64 c-n-f Metadata [5880 B]                                                       
Get:42 http://ports.ubuntu.com/ubuntu-ports kinetic-security/restricted arm64 Packages [174 kB]                                                       
Get:43 http://ports.ubuntu.com/ubuntu-ports kinetic-security/restricted Translation-en [39.6 kB]                                                      
Get:44 http://ports.ubuntu.com/ubuntu-ports kinetic-security/restricted arm64 c-n-f Metadata [416 B]                                                  
Get:45 http://ports.ubuntu.com/ubuntu-ports kinetic-security/universe arm64 Packages [146 kB]                                                         
Get:46 http://ports.ubuntu.com/ubuntu-ports kinetic-security/universe Translation-en [64.5 kB]                                                        
Get:47 http://ports.ubuntu.com/ubuntu-ports kinetic-security/universe arm64 c-n-f Metadata [6368 B]                                                   
Get:48 http://ports.ubuntu.com/ubuntu-ports kinetic-security/multiverse arm64 Packages [2120 B]                                                       
Get:49 http://ports.ubuntu.com/ubuntu-ports kinetic-security/multiverse Translation-en [1012 B]                                                       
Get:50 http://ports.ubuntu.com/ubuntu-ports kinetic-security/multiverse arm64 c-n-f Metadata [216 B]                                                  
Reading package lists... Done                                                                                                                         
E: The repository 'https://ppa.launchpadcontent.net/ondrej/php/ubuntu kinetic Release' does not have a Release file.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
N: See apt-secure(8) manpage for repository creation and user configuration details.

```

yet one more thing
```
root@ubuntu:~# apt-get traceroute
E: Invalid operation traceroute
root@ubuntu:~# sudo apt-get update && sudo apt-get install traceroute
Hit:1 http://ports.ubuntu.com/ubuntu-ports kinetic InRelease
Get:2 http://ports.ubuntu.com/ubuntu-ports kinetic-updates InRelease [118 kB]    
Get:3 http://download.opensuse.org/repositories/isv:/ownCloud:/server:/10/Ubuntu_21.10  InRelease [1535 B]                                        
Ign:4 https://ppa.launchpadcontent.net/ondrej/php/ubuntu kinetic InRelease                                                                        
Get:5 http://ports.ubuntu.com/ubuntu-ports kinetic-backports InRelease [99.9 kB]             
Err:6 https://ppa.launchpadcontent.net/ondrej/php/ubuntu kinetic Release                   
  404  Not Found [IP: 185.125.190.52 443]
Get:7 http://ports.ubuntu.com/ubuntu-ports kinetic-security InRelease [109 kB]
Reading package lists... Done    
E: The repository 'https://ppa.launchpadcontent.net/ondrej/php/ubuntu kinetic Release' does not have a Release file.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
N: See apt-secure(8) manpage for repository creation and user configuration details.

```

---

### Post by MAFoElffen on 2023-03-25
Try looking for the other package it is in:
```

apt-cache show inetutils-traceroute

```
On this:
```

E: The repository 'https://ppa.launchpadcontent.net/ondrej/php/ubuntu [COLOR=#ff0000]kinetic[/COLOR] Release' does not have a Release file.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
N: See apt-secure(8) manpage for repository creation and user configuration details.

```
If you look at that PPA:
```

Index of /ondrej/php/ubuntu/dists
[ICO]    Name    Last modified    Size    Description
[PARENTDIR]    Parent Directory         -      
[DIR]    artful/    2018-10-15 12:10     -      
[DIR]    bionic/    2023-03-16 18:06     -      
[DIR]    cosmic/    2019-08-19 10:34     -      
[DIR]    devel/    2023-03-16 19:30     -      
[DIR]    disco/    2020-02-01 18:00     -      
[DIR]    eoan/    2020-10-10 18:52     -      
[DIR]    focal/    2023-03-16 17:29     -      
[DIR]    groovy/    2021-07-30 13:12     -      
[DIR]    hirsute/    2022-02-17 16:27     -      
[DIR]    impish/    2022-07-20 15:05     -      
[DIR]    jammy/    2023-03-16 19:30     -      
[DIR]    precise/    2017-08-04 12:07     -      
[DIR]    trusty/    2019-05-03 10:10     -      
[DIR]    vivid/    2015-10-17 10:00     -      
[DIR]    wily/    2016-10-12 12:04     -      
[DIR]    xenial/    2021-06-04 21:29     -      
[DIR]    yakkety/    2017-08-04 11:55     -      
[DIR]    zesty/    2018-02-05 12:49     -      
Apache/2.4.18 (Ubuntu) Server at ppa.launchpadcontent.net Port 443

```
There are no packages there built for Kenetic, Nor Lunar... The newest release he has packages for is for Jammy.

Contact:  [EMAIL="ondrej@ubuntu.com"]ondrej@ubuntu.com[/EMAIL] and see if he has plans to built for your release (Kenetic)

---

