---
title: "Ubuntu Xenial LTS fail to fetch updates"
date: 2018-02-02
forum: Server Platforms
---

### Post by athornfam2 on 2018-02-02
[COLOR=#000000]I thought I would reach out to everyone in the Ubuntu forums to see if someone can enlighten me on this issue. So out of the blues i've been getting this issue below... Its happened on two machines... not sure if anyone has any suggestions. For more information what I've already performed please look at this thread [/COLOR][https://community.spiceworks.com/top...ial-lts?page=1]("https://community.spiceworks.com/topic/2102742-problems-with-apt-get-update-xenial-lts?page=1")

```
Err:1 http://archive.canonical.com/ubuntu xenial InRelease  Could not connect to archive.canonical.com:80 (91.189.91.15). - connect (111: Connection refused) [IP: 91.189.91.15 80]
Err:2 http://archive.ubuntu.com/ubuntu xenial InRelease
  Could not connect to archive.ubuntu.com:80 (91.189.88.162). - connect (111: Connection refused) [IP: 91.189.88.162 80]
Err:3 http://archive.ubuntu.com/ubuntu xenial-updates InRelease
  Unable to connect to archive.ubuntu.com:http: [IP: 91.189.88.162 80]
Err:4 http://archive.ubuntu.com/ubuntu xenial-backports InRelease
  Unable to connect to archive.ubuntu.com:http: [IP: 91.189.88.162 80]
Err:5 http://archive.ubuntu.com/ubuntu xenial-security InRelease
  Unable to connect to archive.ubuntu.com:http: [IP: 91.189.88.162 80]
Reading package lists... Done
W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/xenial/InRelease  Could not connect to archive.ubuntu.com:80 (91.189.88.162). - connect (111: Connection refused) [IP: 91.189.88.162 80]
W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/xenial-updates/InRelease  Unable to connect to archive.ubuntu.com:http: [IP: 91.189.88.162 80]
W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/xenial-backports/InRelease  Unable to connect to archive.ubuntu.com:http: [IP: 91.189.88.162 80]
W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/xenial-security/InRelease  Unable to connect to archive.ubuntu.com:http: [IP: 91.189.88.162 80]
W: Failed to fetch http://archive.canonical.com/ubuntu/dists/xenial/InRelease  Could not connect to archive.canonical.com:80 (91.189.91.15). - connect (111: Connection refused) [IP: 91.189.91.15 80] W: Some index files failed to download. They have been ignored, or old ones used instead.
```

---

### Post by linuchsan on 2018-02-02
Are you behind a proxy?

---

### Post by athornfam2 on 2018-02-02
No I'm not. All other services work besides Apt-get, apt-upgrade, or apt dist-upgrade

---

### Post by athornfam2 on 2018-02-02
Just the basic sources.list

```
#

# deb cdrom:[Ubuntu-Server 16.04.1 LTS _Xenial Xerus_ - Release amd64 (20160719)]/ xenial main restricted


#deb cdrom:[Ubuntu-Server 16.04.1 LTS _Xenial Xerus_ - Release amd64 (20160719)]/ xenial main restricted


# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.
deb http://us.archive.ubuntu.com/ubuntu/ xenial main restricted
# deb-src http://us.archive.ubuntu.com/ubuntu/ xenial main restricted


## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu/ xenial-updates main restricted
# deb-src http://us.archive.ubuntu.com/ubuntu/ xenial-updates main restricted


## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://us.archive.ubuntu.com/ubuntu/ xenial universe
# deb-src http://us.archive.ubuntu.com/ubuntu/ xenial universe
deb http://us.archive.ubuntu.com/ubuntu/ xenial-updates universe
# deb-src http://us.archive.ubuntu.com/ubuntu/ xenial-updates universe


## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://us.archive.ubuntu.com/ubuntu/ xenial multiverse
# deb-src http://us.archive.ubuntu.com/ubuntu/ xenial multiverse
deb http://us.archive.ubuntu.com/ubuntu/ xenial-updates multiverse
# deb-src http://us.archive.ubuntu.com/ubuntu/ xenial-updates multiverse


## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://us.archive.ubuntu.com/ubuntu/ xenial-backports main restricted universe multiverse
# deb-src http://us.archive.ubuntu.com/ubuntu/ xenial-backports main restricted universe multiverse


## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb http://archive.canonical.com/ubuntu xenial partner
# deb-src http://archive.canonical.com/ubuntu xenial partner


deb http://security.ubuntu.com/ubuntu xenial-security main restricted
# deb-src http://security.ubuntu.com/ubuntu xenial-security main restricted
deb http://security.ubuntu.com/ubuntu xenial-security universe
# deb-src http://security.ubuntu.com/ubuntu xenial-security universe
deb http://security.ubuntu.com/ubuntu xenial-security multiverse
# deb-src http://security.ubuntu.com/ubuntu xenial-security multiverse
```

---

### Post by linuchsan on 2018-02-02
What does cat **/etc/apt/apt.conf ** say?

---

### Post by athornfam2 on 2018-02-02
This is all it states when running that command

```
root@ubuntu-ck:/etc/apt# cat /etc/apt/apt.conf


root@ubuntu-ck:/etc/apt#

```

---

### Post by volkswagner on 2018-02-02
Do you have static IP set? If so, please post contents of /etc/network/interfaces.

What do you get with:
```
 nslookup us.archive.ubuntu.com 
```

---

### Post by athornfam2 on 2018-02-02
I have a local dns server at home. This is what I get with nslookup

```
root@ubuntu-ck:/etc/apt# nslookup us.archive.ubuntu.comServer:         192.168.4.31
Address:        192.168.4.31#53


Non-authoritative answer:
Name:   us.archive.ubuntu.com
Address: 91.189.91.23
Name:   us.archive.ubuntu.com
Address: 91.189.91.26

```

```

root@ubuntu-ck:/etc/apt# ping www.google.com
PING www.google.com (173.194.208.99) 56(84) bytes of data.
64 bytes from ql-in-f99.1e100.net (173.194.208.99): icmp_seq=1 ttl=45 time=32.6 ms
64 bytes from ql-in-f99.1e100.net (173.194.208.99): icmp_seq=2 ttl=45 time=32.4 ms
^C
--- www.google.com ping statistics ---
2 packets transmitted, 2 received, 0% packet loss, time 1001ms
rtt min/avg/max/mdev = 32.460/32.563/32.667/0.208 ms
root@ubuntu-ck:/etc/apt# wget www.google.com
--2018-02-02 18:46:54--  http://www.google.com/
Resolving www.google.com (www.google.com)... 173.194.208.104, 173.194.208.147, 173.194.208.105, ...
Connecting to www.google.com (www.google.com)|173.194.208.104|:80... ^C

```

Firewall is turned off and Unifi cloud key services are working

---

### Post by volkswagner on 2018-02-02
The reason I asked about static IP and network config is because I've seen this symptom when the network stanza is missing from config file. You didn't answer the question, so I can't confirm. Perhaps you are using DHCP, so moot point.

---

### Post by athornfam2 on 2018-02-02
My apologies. This is the information that I've gathered from the system

```
# The primary network interfaceauto ens160
iface ens160 inet static
   address 192.168.4.68
   netmask 255.255.255.0
   network 192.168.4.0
   gateway 192.168.4.1
   dns-nameservers 75.75.75.75
   dns-nameservers 75.75.76.76

```

---

### Post by volkswagner on 2018-02-03
You are getting connection refused on this machine.

This is likely a firewall issue. You'll want to first determine if
it's your router/firewall or firewall on Ubuntu Server.

Can you browse to any of the urls from inside your LAN?
[http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu)
[http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu)

What happens when you try to get a file directly without apt.
```
wget http://archive.ubuntu.com/ubuntu/ls-lR.gz
```

---

### Post by athornfam2 on 2018-02-03
I can reach those http links through my browser of my VM. I cannot reach the wget link through my ubuntu machine.

```

mwolf@ubuntu-ck:~$ wget http://archive.ubuntu.com/ubuntu/ls-lR.gz
--2018-02-03 19:40:19--  http://archive.ubuntu.com/ubuntu/ls-lR.gz
Resolving archive.ubuntu.com (archive.ubuntu.com)... failed: Temporary failure in name resolution.
wget: unable to resolve host address &#8216;archive.ubuntu.com&#8217;

```

---

### Post by darkod on 2018-02-04
Well, there you have your problem. The DNS server you are using can't resolve the URL.

At the same time while looking at using better DNS server, I would also look into the option to use different mirror. Not because of this error, but in general. The standard ubuntu mirrors are usually more loaded and slower. There are plenty other mirrors with faster links, you have a full list here also with link bandwidth: [https://launchpad.net/ubuntu/+archivemirrors](https://launchpad.net/ubuntu/+archivemirrors)

Use something geographically closer to your location (better speed).

But in any case check out your DNS server and why it doesn't resolve that URL.

---

### Post by athornfam2 on 2018-02-04
I've ruled out my Windows DNS servers being the issue as I can ping from them directly, MacBook, & other linux boxes. I turned off the loopback interfaces, fixed my resolv.conf and changed my sources.list. Now I get this below.

**Before changing the above items**
```

root@ubuntu-ck:/etc/apt# apt-get update
Err:1 http://us.archive.ubuntu.com/ubuntu xenial InRelease
  Could not connect to us.archive.ubuntu.com:80 (91.189.91.23). - connect (111: Connection refused) [IP: 91.189.91.23 80]
Err:2 http://us.archive.ubuntu.com/ubuntu xenial-updates InRelease
  Unable to connect to us.archive.ubuntu.com:http: [IP: 91.189.91.23 80]
Err:3 http://us.archive.ubuntu.com/ubuntu xenial-backports InRelease
  Unable to connect to us.archive.ubuntu.com:http: [IP: 91.189.91.23 80]
Err:4 http://security.ubuntu.com/ubuntu xenial-security InRelease                                   
  Could not connect to security.ubuntu.com:80 (91.189.88.152). - connect (111: Connection refused) [IP: 91.189.88.152 80]
0% [Connecting to mirrors.bloomu.edu (148.137.11.75)]^C

```                                        
**Changes made to sources.list mirrors**
```

root@ubuntu-ck:/etc/apt# nano sources.list
root@ubuntu-ck:/etc/apt# apt update
0% [Connecting to mirrors.bloomu.edu (148.137.11.75)]

```

---

### Post by athornfam2 on 2018-02-05
Still having issues connecting to another repo??

---

### Post by darkod on 2018-02-05
What do these commands show from the ubuntu server:
```
dig mirrors.bloomu.edu
nslookup mirrors.bloomu.edu
```

I will say again, you have issues with dns and/or routing or firewall. We can't know your LAN in details, so you have to figure it out... Just follow the traffic.

---

### Post by athornfam2 on 2018-02-05
[B]dig mirrors.bloomu.edu


[/B]```

root@ubuntu-ck:/# dig mirrors.bloomu.edu


; <<>> DiG 9.10.3-P4-Ubuntu <<>> mirrors.bloomu.edu
;; global options: +cmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 25869
;; flags: qr rd ra; QUERY: 1, ANSWER: 2, AUTHORITY: 0, ADDITIONAL: 1


;; OPT PSEUDOSECTION:
; EDNS: version: 0, flags:; udp: 4000
;; QUESTION SECTION:
;mirrors.bloomu.edu.            IN      A


;; ANSWER SECTION:
mirrors.bloomu.edu.     3599    IN      CNAME   pearl.bloomu.edu.
pearl.bloomu.edu.       3599    IN      A       148.137.11.75


;; Query time: 65 msec
;; SERVER: 192.168.4.31#53(192.168.4.31)
;; WHEN: Mon Feb 05 14:38:34 EST 2018
;; MSG SIZE  rcvd: 83

```
[B]
nslookup mirrors.bloomu.edu
[/B]
```

root@ubuntu-ck:/# nslookup mirrors.bloomu.edu
Server:         192.168.4.31
Address:        192.168.4.31#53


Non-authoritative answer:
mirrors.bloomu.edu      canonical name = pearl.bloomu.edu.
Name:   pearl.bloomu.edu
Address: 148.137.11.75

```

---

### Post by darkod on 2018-02-05
Ok, how about:
```
traceroute mirrors.bloomu.edu
```

You might need to install the package traceroute, it's not by default. But if apt-get is not working it's not very easy to install any package...

You can also try telnet to port 80:
```
telnet mirrors.bloomu.edu 80
```

---

### Post by athornfam2 on 2018-02-05
```

root@ubuntu-ck:/home/mwolf# cd /
root@ubuntu-ck:/# traceroute mirrors.bloomu.edu
The program 'traceroute' can be found in the following packages:
 * inetutils-traceroute (You will have to enable component called 'universe')
 * traceroute (You will have to enable component called 'universe')
Try: apt install <selected package>
root@ubuntu-ck:/# apt install inetutils-traceroute
Reading package lists... Done
Building dependency tree
Reading state information... Done
E: Unable to locate package inetutils-traceroute
root@ubuntu-ck:/# telnet mirrors.bloomu.edu
Trying 148.137.11.75...
^C
root@ubuntu-ck:/# telnet mirrors.bloomu.edu 80
Trying 148.137.11.75...

```

---

### Post by darkod on 2018-02-05
Hmmm, telnet seems to connect you, right?

It's very weird why apt wouldn't work then... Can you post the whole content of the sources please:
```
cat /etc/apt/sources.list
```

---

### Post by athornfam2 on 2018-02-05
Telnet didn't work for me either but I can post my sources.list

```

root@ubuntu-ck:/# cat /etc/apt/sources.list
deb http://mirrors.bloomu.edu/ubuntu/ xenial main
deb-src http://mirrors.bloomu.edu/ubuntu/ xenial main

```

---

### Post by darkod on 2018-02-05
Ah, if telnet didn't work you are not reaching the site on port 80... How about iptables rules:
```
sudo iptables -L -n -v
```

---

### Post by athornfam2 on 2018-02-05
You see where I'm going with this? Its just strange the majority of everything else works... It just all the sudden stopped work

```

root@ubuntu-ck:/# sudo iptables -L -n -v
Chain INPUT (policy ACCEPT 0 packets, 0 bytes)
 pkts bytes target     prot opt in     out     source               destination                                     


Chain FORWARD (policy ACCEPT 0 packets, 0 bytes)
 pkts bytes target     prot opt in     out     source               destination                                     


Chain OUTPUT (policy ACCEPT 0 packets, 0 bytes)
 pkts bytes target     prot opt in     out     source               destination     

```

---

### Post by darkod on 2018-02-05
I'm officially lost! :)

---

### Post by athornfam2 on 2018-02-05
See now you can share the craziness with me. I've about lost my mind on this.

---

### Post by volkswagner on 2018-02-05
You should fire up a packet trace.
I usually kick myself in the butt when I kill several hours
debugging/troubleshooting, then fire up WireShark to find
my problem in minutes (in plain text even!)
If you can run packet tracer on your router, that would be best.

There is some sort of firewall issue. What is your network topology like?
What kind of router do you have? What are the firewall rules on it?

Try adding the following to your /etc/hosts file:
```
91.189.88.152   archive.ubuntu.com
```
the run:
```
wget http://archive.ubuntu.com:80/ubuntu/ls-lR.gz
```

Also try:
```
wget https://the.earth.li/~sgtatham/putty/latest/putty-0.70.tar.gz
```

also try:
```
wget http://the.earth.li:80/~sgtatham/putty/latest/putty-0.70.tar.gz
```
The putty link above should redirect to https and you should see such in your terminal.
If it doesn't redirect, this points to a firewall issue on port 80 (of course if the original https for putty works!)
:)

---

### Post by athornfam2 on 2018-02-06
All of those attempts failed. In my home I have my ASA 5506-X -> Cisco 3750G Stack -> ESXI R710 Host

---

### Post by darkod on 2018-02-06
Wow, quite firepower for a home connection... :)

As suggested, I would start running packet tracing to check what really goes on the ASA and the Cisco 3750G if necessary.

Since the apt messages said connection denied, it would be interesting to see if the same thing happens over a VPN connection (not running through your router/FW and your ISP). If apt works over VPN then surely the problem is in your home equipment. The only issue is if you have such VPN available for such testing...

---

### Post by athornfam2 on 2018-02-06
Yeah, Was thinking about upgrading to the ASA 5525-X Active/Standby, upgrading to 3850's with 10GB fiber, and finally upgrading to r720XD's

How would I go about using a vpn on the ubuntu installation if I can't get apt to work? I have to download the module right?

---

### Post by volkswagner on 2018-02-06
All test results point to your firewall/network config.

Is your hypervisor running NAT or any firewall/routing?

It seems you have some intermittent or timing related issues.
Your earlier post while installing traceroute acted like it didn't install, but then you were
able to run the command. If you were able to download package but can't run
apt update seems odd, but perhaps some repositories are connecting???

You didn't post results of the wget commands, so we have to assume you got
"connection refused". It seems you can't connect out on port 80 and port 443.
Do you have any servers outside that you can try connecting to ssh or ftp
to try other ports?

Do you have  a DHCP server on the network, have you tried setting up DHCP?
Is your public ip blacklisted?

I doubt this is an Ubuntu issue, likely a network/firewall issue.

---

### Post by linuchsan on 2018-02-07
Maybe this helps: [https://www.speaknetworks.com/basic-cisco-asa-5506-x-configuration-example/](https://www.speaknetworks.com/basic-cisco-asa-5506-x-configuration-example/)

---

### Post by athornfam2 on 2018-02-07
Don't ask me how but I resolved the issue. 

I went into /etc/network/interfaces. Changed the static ip address 192.168.4.69 > sudo /etc/init.d/networking restart > logged back in and apt-get update, upgrade, and dist-upgrade worked. After I updated a few things I went back changed the static ip address to 192.168.4.68... apt-get update, upgrade, and dist-upgrade work... Very odd.

---

### Post by darkod on 2018-02-07
Is it possible there was something "stuck" pending a reboot, so actually changing the ip didn't help but the reboot itself?

Strange, usually the first thing to try reboot is for windows servers. :)

Anyway glad you got it fixed. Please mark the thread as solved. You can do that in Thread Tools above he first post.

---

