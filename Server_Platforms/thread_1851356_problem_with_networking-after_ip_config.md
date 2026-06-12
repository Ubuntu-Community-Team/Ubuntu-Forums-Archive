---
title: "problem with networking-after ip config"
date: 2011-09-28
forum: Server Platforms
---

### Post by gabikilalala on 2011-09-28
hell, 
well i ran
vi /etc/network/interfaces
then /etc/init.d/networking restart after making static the ip
then vi /etc/hosts
giving other details about ip.
so then i cannot update or install any package.
what should i do?

---

### Post by haqking on 2011-09-28
> **gabikilalala said:**
> hell, 
well i ran
vi /etc/network/interfaces
then /etc/init.d/networking restart after making static the ip
then vi /etc/hosts
giving other details about ip.
so then i cannot update or install any package.
what should i do?

that depends on the information you placed on those files.

can you show us

```
ifconfig
```

```
cat /etc/resolv.conf
```

---

### Post by gabikilalala on 2011-09-28
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet static
        address 192.168.0.100
        netmask 255.255.255.0
        network 192.168.0.0
        broadcast 192.168.0.255
        gateway 192.168.0.1
on the /etc/network/interfaces

127.0.0.1       localhost.localdomain   localhost
192.168.0.100   server1.example.com     server1

# The following lines are desirable for IPv6 capable hosts
::1     ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters

on the /etc/hosts
well i am trying to follow the guide [http://www.howtoforge.com/perfect-server-ubuntu-11.04-ispconfig-3-p3](http://www.howtoforge.com/perfect-server-ubuntu-11.04-ispconfig-3-p3)
but i have problems.I really need some help so i can continue.
thank you

---

### Post by gabikilalala on 2011-09-28
hello,
i have problem with network.
[HTML]eth0      Link encap:Ethernet  HWaddr 00:0c:29:2d:27:9a  
          inet addr:172.16.161.130  Bcast:172.16.161.255  Mask:255.255.255.0
          inet6 addr: fe80::20c:29ff:fe2d:279a/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:13560 errors:0 dropped:0 overruns:0 frame:0
          TX packets:9501 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:11355798 (11.3 MB)  TX bytes:1229438 (1.2 MB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
[/HTML]


[HTML]ping 82.211.81.158
PING 82.211.81.158 (82.211.81.158) 56(84) bytes of data.
^C
--- 82.211.81.158 ping statistics ---
204 packets transmitted, 0 received, 100% packet loss, time 203004ms

root@gaserver:/home/administrator# ping www.ubuntu.com
PING www.ubuntu.com (91.189.90.40) 56(84) bytes of data.
^C
--- www.ubuntu.com ping statistics ---
347 packets transmitted, 0 received, 100% packet loss, time 346006ms
[/HTML]

i run cat /etc/resolv.conf

[HTML]domain localdomain
search localdomain
nameserver 172.16.161.2
[/HTML]

any ideas?i cannot update or install packages!!

---

### Post by haqking on 2011-09-28
OK so im confused, do you have internet access issues ? resolution issues ?

the only issue you mentioned it that you cannot update or install a package, is this correct ?

what errors do you get ?

---

### Post by gabikilalala on 2011-09-28
well i am confused too!!!:p
i am trying to follow this guide-->[http://www.howtoforge.com/perfect-server-ubuntu-11.04-ispconfig-3-p3](http://www.howtoforge.com/perfect-server-ubuntu-11.04-ispconfig-3-p3)
So after giving server1.example.com etc in the file /etc/hosts
i have the same problem as this [http://ubuntuforums.org/showthread.php?t=1130535](http://ubuntuforums.org/showthread.php?t=1130535)
but when i run ping 72.14.205.100 i have no result
[HTML]PING 72.14.205.100 (72.14.205.100) 56(84) bytes of data.
^C
--- 72.14.205.100 ping statistics ---
5 packets transmitted, 0 received, 100% packet loss, time 4006ms[/HTML]

then i run nslookup google.com and i have this 

[HTML]Server:		172.16.161.2
Address:	172.16.161.2#53

Non-authoritative answer:
Name:	google.com
Address: 74.125.39.147
Name:	google.com
Address: 74.125.39.99
Name:	google.com
Address: 74.125.39.103
Name:	google.com
Address: 74.125.39.104
Name:	google.com
Address: 74.125.39.105
Name:	google.com
Address: 74.125.39.106
[/HTML]

i dont know what to do.here is the ifconfig result

[HTML]eth0      Link encap:Ethernet  HWaddr 00:0c:29:2d:27:9a  
          inet addr:172.16.161.130  Bcast:172.16.161.255  Mask:255.255.255.0
          inet6 addr: fe80::20c:29ff:fe2d:279a/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2997 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2358 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:268893 (268.8 KB)  TX bytes:363761 (363.7 KB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
[/HTML]

and my cat /etc/resolv.conf result 

[HTML]domain localdomain
search localdomain
nameserver 172.16.161.2[/HTML]

and for the errors i have i just cannot update and install packages it tries to load but it stacks in 0% and says something like not fetched to security.ubuntu.com...etc

i thought that it is a problem fro the ip change..but i dont know.
well thank you for your help,really!

---

### Post by sffvba[e0rt on 2011-09-28
Threads merged.  @OP, please don't split your support requests for the same issue over multiple threads.


404

---

### Post by gabikilalala on 2011-09-28
ok..sorry!

---

### Post by gabikilalala on 2011-09-28
oh for the internet access i dont know i am in command line so a cannot browse to a site, but when i ping 172.16.161.2 the result is 

[HTML]PING 172.16.161.2 (172.16.161.2) 56(84) bytes of data.
64 bytes from 172.16.161.2: icmp_req=1 ttl=128 time=5.39 ms
64 bytes from 172.16.161.2: icmp_req=2 ttl=128 time=0.253 ms
64 bytes from 172.16.161.2: icmp_req=3 ttl=128 time=0.289 ms
64 bytes from 172.16.161.2: icmp_req=4 ttl=128 time=0.239 ms
64 bytes from 172.16.161.2: icmp_req=5 ttl=128 time=0.236 ms
^C
--- 172.16.161.2 ping statistics ---
5 packets transmitted, 5 received, 0% packet loss, time 3999ms
rtt min/avg/max/mdev = 0.236/1.282/5.395/2.056 ms[/HTML]

maybe it is from the rooter but i dont know!

---

### Post by haqking on 2011-09-28
your eth0 address is a reserved class B address ?

I am confused here, hang on let me read it over again

---

### Post by gabikilalala on 2011-09-28
well i dont know what class it is.where can i see that?

---

### Post by haqking on 2011-09-28
172.16.x.x is a class B address, i suggest reading up on TC/IP before playing with your addresses though as classes of IP are a basic 101 ;-)

However i will have to come back to this and read through it again, i have to nip out for an hour now though.

---

### Post by gabikilalala on 2011-09-28
ok thanks for your help! i will wait.and maybe i will read this..thank you i wait for your answer

---

### Post by gabikilalala on 2011-09-28
well i just reinstalled ubuntu server 11.04 32 bit.I followed again the steps but this time i ran ifconfig and i put 192.168.1.89 for ip in the /etc/network/interfaces.
then i restarted the networking (/etc/init.d/networking restart
then i edited /etc/hosts like this

[HTML]
127.0.0.1       localhost.localdomain   localhost
192.168.1.89    ga-server1.example.com  ga-server1   

# The following lines are desirable for IPv6 capable hosts
::1     ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
[/HTML]

So then i ran echo ga-server1.example.com > /etc/hostname
then /etc/init.d/hostname restart
then hostname
and hostname -f
both printed ga-server1.example.com


then i edited /etc/apt/sources.list as it says

and then i ran apt-get update
and it worked!
then apt-get upgrade
and it worked!
then reboot!
so i am running again apt-get update and.....errors!!!!!!!!!
So what is going on???
please please please some help!

---

### Post by gabikilalala on 2011-09-28
Well after searching again i found that i have the exactly same problem [http://ubuntuforums.org/showthread.php?t=871741](http://ubuntuforums.org/showthread.php?t=871741)
with the same prints of the commands...help..

---

### Post by gabikilalala on 2011-09-28
well here is the erros after apt-get update

[HTML]Ign http://gr.archive.ubuntu.com natty InRelease                               
Ign http://gr.archive.ubuntu.com natty-updates InRelease                       
Err http://gr.archive.ubuntu.com natty Release.gpg     
  Unable to connect to gr.archive.ubuntu.com:http:
Err http://gr.archive.ubuntu.com natty-updates Release.gpg
  Unable to connect to gr.archive.ubuntu.com:http:
Ign http://gr.archive.ubuntu.com natty Release         
Ign http://gr.archive.ubuntu.com natty-updates Release 
Ign http://gr.archive.ubuntu.com natty/main Sources/DiffIndex
Ign http://gr.archive.ubuntu.com natty/restricted Sources/DiffIndex
Ign http://gr.archive.ubuntu.com natty/universe Sources/DiffIndex
Ign http://gr.archive.ubuntu.com natty/multiverse Sources/DiffIndex
Ign http://gr.archive.ubuntu.com natty/main i386 Packages/DiffIndex
Ign http://gr.archive.ubuntu.com natty/restricted i386 Packages/DiffIndex
Ign http://gr.archive.ubuntu.com natty/universe i386 Packages/DiffIndex
Ign http://gr.archive.ubuntu.com natty/multiverse i386 Packages/DiffIndex
Ign http://gr.archive.ubuntu.com natty/main TranslationIndex
Ign http://gr.archive.ubuntu.com natty/multiverse TranslationIndex
Ign http://gr.archive.ubuntu.com natty/restricted TranslationIndex
Ign http://gr.archive.ubuntu.com natty/universe TranslationIndex
Ign http://gr.archive.ubuntu.com natty-updates/main Sources/DiffIndex
Ign http://gr.archive.ubuntu.com natty-updates/restricted Sources/DiffIndex
Ign http://gr.archive.ubuntu.com natty-updates/universe Sources/DiffIndex
Ign http://gr.archive.ubuntu.com natty-updates/multiverse Sources/DiffIndex
Ign http://gr.archive.ubuntu.com natty-updates/main i386 Packages/DiffIndex
Ign http://gr.archive.ubuntu.com natty-updates/restricted i386 Packages/DiffIndex
Ign http://gr.archive.ubuntu.com natty-updates/universe i386 Packages/DiffIndex
Ign http://gr.archive.ubuntu.com natty-updates/multiverse i386 Packages/DiffIndex
Ign http://gr.archive.ubuntu.com natty-updates/main TranslationIndex
Ign http://gr.archive.ubuntu.com natty-updates/multiverse TranslationIndex
Ign http://gr.archive.ubuntu.com natty-updates/restricted TranslationIndex
Ign http://gr.archive.ubuntu.com natty-updates/universe TranslationIndex
Err http://gr.archive.ubuntu.com natty/main Sources    
  Unable to connect to gr.archive.ubuntu.com:http:
Err http://gr.archive.ubuntu.com natty/restricted Sources
  Unable to connect to gr.archive.ubuntu.com:http:
Err http://gr.archive.ubuntu.com natty/universe Sources
  Unable to connect to gr.archive.ubuntu.com:http:
Err http://gr.archive.ubuntu.com natty/multiverse Sources
  Unable to connect to gr.archive.ubuntu.com:http:
Err http://gr.archive.ubuntu.com natty/main i386 Packages
  Unable to connect to gr.archive.ubuntu.com:http:
Err http://gr.archive.ubuntu.com natty/restricted i386 Packages
  Unable to connect to gr.archive.ubuntu.com:http:
Err http://gr.archive.ubuntu.com natty/universe i386 Packages
  Unable to connect to gr.archive.ubuntu.com:http:
Err http://gr.archive.ubuntu.com natty/multiverse i386 Packages
  Unable to connect to gr.archive.ubuntu.com:http:
Err http://gr.archive.ubuntu.com natty/main Translation-en_US
  Unable to connect to gr.archive.ubuntu.com:http:
Err http://gr.archive.ubuntu.com natty/main Translation-en
  Unable to connect to gr.archive.ubuntu.com:http:
Err http://gr.archive.ubuntu.com natty/multiverse Translation-en_US
  Unable to connect to gr.archive.ubuntu.com:http:
Err http://gr.archive.ubuntu.com natty/multiverse Translation-en
  Unable to connect to gr.archive.ubuntu.com:http:
Err http://gr.archive.ubuntu.com natty/restricted Translation-en_US
  Unable to connect to gr.archive.ubuntu.com:http:
Err http://gr.archive.ubuntu.com natty/restricted Translation-en
  Unable to connect to gr.archive.ubuntu.com:http:
Err http://gr.archive.ubuntu.com natty/universe Translation-en_US
  Unable to connect to gr.archive.ubuntu.com:http:
Err http://gr.archive.ubuntu.com natty/universe Translation-en
  Unable to connect to gr.archive.ubuntu.com:http:
Err http://gr.archive.ubuntu.com natty-updates/main Sources
  Unable to connect to gr.archive.ubuntu.com:http:
Err http://gr.archive.ubuntu.com natty-updates/restricted Sources
  Unable to connect to gr.archive.ubuntu.com:http:
Err http://gr.archive.ubuntu.com natty-updates/universe Sources
  Unable to connect to gr.archive.ubuntu.com:http:
Err http://gr.archive.ubuntu.com natty-updates/multiverse Sources
  Unable to connect to gr.archive.ubuntu.com:http:
Err http://gr.archive.ubuntu.com natty-updates/main i386 Packages
  Unable to connect to gr.archive.ubuntu.com:http:
Err http://gr.archive.ubuntu.com natty-updates/restricted i386 Packages
  Unable to connect to gr.archive.ubuntu.com:http:
Err http://gr.archive.ubuntu.com natty-updates/universe i386 Packages
  Unable to connect to gr.archive.ubuntu.com:http:
Err http://gr.archive.ubuntu.com natty-updates/multiverse i386 Packages
  Unable to connect to gr.archive.ubuntu.com:http:
Err http://gr.archive.ubuntu.com natty-updates/main Translation-en_US
  Unable to connect to gr.archive.ubuntu.com:http:
Err http://gr.archive.ubuntu.com natty-updates/main Translation-en
  Unable to connect to gr.archive.ubuntu.com:http:
Err http://gr.archive.ubuntu.com natty-updates/multiverse Translation-en_US
  Unable to connect to gr.archive.ubuntu.com:http:
Err http://gr.archive.ubuntu.com natty-updates/multiverse Translation-en
  Unable to connect to gr.archive.ubuntu.com:http:
Err http://gr.archive.ubuntu.com natty-updates/restricted Translation-en_US
  Unable to connect to gr.archive.ubuntu.com:http:
Err http://gr.archive.ubuntu.com natty-updates/restricted Translation-en
  Unable to connect to gr.archive.ubuntu.com:http:
Err http://gr.archive.ubuntu.com natty-updates/universe Translation-en_US
  Unable to connect to gr.archive.ubuntu.com:http:
Err http://gr.archive.ubuntu.com natty-updates/universe Translation-en
  Unable to connect to gr.archive.ubuntu.com:http:
Ign http://security.ubuntu.com natty-security InRelease
Err http://security.ubuntu.com natty-security Release.gpg
  Unable to connect to security.ubuntu.com:http: [IP: 91.189.92.171 80]
Ign http://security.ubuntu.com natty-security Release
Ign http://security.ubuntu.com natty-security/main Sources/DiffIndex
Ign http://security.ubuntu.com natty-security/restricted Sources/DiffIndex
Ign http://security.ubuntu.com natty-security/universe Sources/DiffIndex
Ign http://security.ubuntu.com natty-security/multiverse Sources/DiffIndex
Ign http://security.ubuntu.com natty-security/main i386 Packages/DiffIndex
Ign http://security.ubuntu.com natty-security/restricted i386 Packages/DiffIndex
Ign http://security.ubuntu.com natty-security/universe i386 Packages/DiffIndex
Ign http://security.ubuntu.com natty-security/multiverse i386 Packages/DiffIndex
Ign http://security.ubuntu.com natty-security/main TranslationIndex
Ign http://security.ubuntu.com natty-security/multiverse TranslationIndex
Ign http://security.ubuntu.com natty-security/restricted TranslationIndex
Ign http://security.ubuntu.com natty-security/universe TranslationIndex
Err http://security.ubuntu.com natty-security/main Sources
  Unable to connect to security.ubuntu.com:http: [IP: 91.189.92.171 80]
Err http://security.ubuntu.com natty-security/restricted Sources
  Unable to connect to security.ubuntu.com:http: [IP: 91.189.92.171 80]
Err http://security.ubuntu.com natty-security/universe Sources
  Unable to connect to security.ubuntu.com:http: [IP: 91.189.92.171 80]
Err http://security.ubuntu.com natty-security/multiverse Sources
  Unable to connect to security.ubuntu.com:http: [IP: 91.189.92.171 80]
Err http://security.ubuntu.com natty-security/main i386 Packages
  Unable to connect to security.ubuntu.com:http: [IP: 91.189.92.171 80]
Err http://security.ubuntu.com natty-security/restricted i386 Packages
  Unable to connect to security.ubuntu.com:http: [IP: 91.189.92.171 80]
Err http://security.ubuntu.com natty-security/universe i386 Packages
  Unable to connect to security.ubuntu.com:http: [IP: 91.189.92.171 80]
Err http://security.ubuntu.com natty-security/multiverse i386 Packages
  Unable to connect to security.ubuntu.com:http: [IP: 91.189.92.171 80]
Err http://security.ubuntu.com natty-security/main Translation-en_US
  Unable to connect to security.ubuntu.com:http: [IP: 91.189.92.171 80]
Err http://security.ubuntu.com natty-security/main Translation-en
  Unable to connect to security.ubuntu.com:http: [IP: 91.189.92.171 80]
Err http://security.ubuntu.com natty-security/multiverse Translation-en_US
  Unable to connect to security.ubuntu.com:http: [IP: 91.189.92.171 80]
Err http://security.ubuntu.com natty-security/multiverse Translation-en
  Unable to connect to security.ubuntu.com:http: [IP: 91.189.92.171 80]
Err http://security.ubuntu.com natty-security/restricted Translation-en_US
  Unable to connect to security.ubuntu.com:http: [IP: 91.189.92.171 80]
Err http://security.ubuntu.com natty-security/restricted Translation-en
  Unable to connect to security.ubuntu.com:http: [IP: 91.189.92.171 80]
Err http://security.ubuntu.com natty-security/universe Translation-en_US
  Unable to connect to security.ubuntu.com:http: [IP: 91.189.92.171 80]
Err http://security.ubuntu.com natty-security/universe Translation-en
  Unable to connect to security.ubuntu.com:http: [IP: 91.189.92.171 80]
W: Failed to fetch http://gr.archive.ubuntu.com/ubuntu/dists/natty/Release.gpg  Unable to connect to gr.archive.ubuntu.com:http:

W: Failed to fetch http://gr.archive.ubuntu.com/ubuntu/dists/natty-updates/Release.gpg  Unable to connect to gr.archive.ubuntu.com:http:

W: Failed to fetch http://gr.archive.ubuntu.com/ubuntu/dists/natty/main/source/Sources  Unable to connect to gr.archive.ubuntu.com:http:

W: Failed to fetch http://gr.archive.ubuntu.com/ubuntu/dists/natty/restricted/source/Sources  Unable to connect to gr.archive.ubuntu.com:http:

W: Failed to fetch http://gr.archive.ubuntu.com/ubuntu/dists/natty/universe/source/Sources  Unable to connect to gr.archive.ubuntu.com:http:

W: Failed to fetch http://gr.archive.ubuntu.com/ubuntu/dists/natty/multiverse/source/Sources  Unable to connect to gr.archive.ubuntu.com:http:

W: Failed to fetch http://gr.archive.ubuntu.com/ubuntu/dists/natty/main/binary-i386/Packages  Unable to connect to gr.archive.ubuntu.com:http:

W: Failed to fetch http://gr.archive.ubuntu.com/ubuntu/dists/natty/restricted/binary-i386/Packages  Unable to connect to gr.archive.ubuntu.com:http:

W: Failed to fetch http://gr.archive.ubuntu.com/ubuntu/dists/natty/universe/binary-i386/Packages  Unable to connect to gr.archive.ubuntu.com:http:

W: Failed to fetch http://gr.archive.ubuntu.com/ubuntu/dists/natty/multiverse/binary-i386/Packages  Unable to connect to gr.archive.ubuntu.com:http:

W: Failed to fetch http://gr.archive.ubuntu.com/ubuntu/dists/natty/main/i18n/Translation-en_US  Unable to connect to gr.archive.ubuntu.com:http:

W: Failed to fetch http://gr.archive.ubuntu.com/ubuntu/dists/natty/main/i18n/Translation-en  Unable to connect to gr.archive.ubuntu.com:http:

W: Failed to fetch http://gr.archive.ubuntu.com/ubuntu/dists/natty/multiverse/i18n/Translation-en_US  Unable to connect to gr.archive.ubuntu.com:http:

W: Failed to fetch http://gr.archive.ubuntu.com/ubuntu/dists/natty/multiverse/i18n/Translation-en  Unable to connect to gr.archive.ubuntu.com:http:

W: Failed to fetch http://gr.archive.ubuntu.com/ubuntu/dists/natty/restricted/i18n/Translation-en_US  Unable to connect to gr.archive.ubuntu.com:http:

W: Failed to fetch http://gr.archive.ubuntu.com/ubuntu/dists/natty/restricted/i18n/Translation-en  Unable to connect to gr.archive.ubuntu.com:http:

W: Failed to fetch http://gr.archive.ubuntu.com/ubuntu/dists/natty/universe/i18n/Translation-en_US  Unable to connect to gr.archive.ubuntu.com:http:

W: Failed to fetch http://gr.archive.ubuntu.com/ubuntu/dists/natty/universe/i18n/Translation-en  Unable to connect to gr.archive.ubuntu.com:http:

W: Failed to fetch http://gr.archive.ubuntu.com/ubuntu/dists/natty-updates/main/source/Sources  Unable to connect to gr.archive.ubuntu.com:http:

W: Failed to fetch http://gr.archive.ubuntu.com/ubuntu/dists/natty-updates/restricted/source/Sources  Unable to connect to gr.archive.ubuntu.com:http:

W: Failed to fetch http://gr.archive.ubuntu.com/ubuntu/dists/natty-updates/universe/source/Sources  Unable to connect to gr.archive.ubuntu.com:http:

W: Failed to fetch http://gr.archive.ubuntu.com/ubuntu/dists/natty-updates/multiverse/source/Sources  Unable to connect to gr.archive.ubuntu.com:http:

W: Failed to fetch http://gr.archive.ubuntu.com/ubuntu/dists/natty-updates/main/binary-i386/Packages  Unable to connect to gr.archive.ubuntu.com:http:

W: Failed to fetch http://gr.archive.ubuntu.com/ubuntu/dists/natty-updates/restricted/binary-i386/Packages  Unable to connect to gr.archive.ubuntu.com:http:

W: Failed to fetch http://gr.archive.ubuntu.com/ubuntu/dists/natty-updates/universe/binary-i386/Packages  Unable to connect to gr.archive.ubuntu.com:http:

W: Failed to fetch http://gr.archive.ubuntu.com/ubuntu/dists/natty-updates/multiverse/binary-i386/Packages  Unable to connect to gr.archive.ubuntu.com:http:

W: Failed to fetch http://gr.archive.ubuntu.com/ubuntu/dists/natty-updates/main/i18n/Translation-en_US  Unable to connect to gr.archive.ubuntu.com:http:

W: Failed to fetch http://gr.archive.ubuntu.com/ubuntu/dists/natty-updates/main/i18n/Translation-en  Unable to connect to gr.archive.ubuntu.com:http:

W: Failed to fetch http://gr.archive.ubuntu.com/ubuntu/dists/natty-updates/multiverse/i18n/Translation-en_US  Unable to connect to gr.archive.ubuntu.com:http:

W: Failed to fetch http://gr.archive.ubuntu.com/ubuntu/dists/natty-updates/multiverse/i18n/Translation-en  Unable to connect to gr.archive.ubuntu.com:http:

W: Failed to fetch http://gr.archive.ubuntu.com/ubuntu/dists/natty-updates/restricted/i18n/Translation-en_US  Unable to connect to gr.archive.ubuntu.com:http:

W: Failed to fetch http://gr.archive.ubuntu.com/ubuntu/dists/natty-updates/restricted/i18n/Translation-en  Unable to connect to gr.archive.ubuntu.com:http:

W: Failed to fetch http://gr.archive.ubuntu.com/ubuntu/dists/natty-updates/universe/i18n/Translation-en_US  Unable to connect to gr.archive.ubuntu.com:http:

W: Failed to fetch http://gr.archive.ubuntu.com/ubuntu/dists/natty-updates/universe/i18n/Translation-en  Unable to connect to gr.archive.ubuntu.com:http:

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/natty-security/Release.gpg  Unable to connect to security.ubuntu.com:http: [IP: 91.189.92.171 80]

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/natty-security/main/source/Sources  Unable to connect to security.ubuntu.com:http: [IP: 91.189.92.171 80]

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/natty-security/restricted/source/Sources  Unable to connect to security.ubuntu.com:http: [IP: 91.189.92.171 80]

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/natty-security/universe/source/Sources  Unable to connect to security.ubuntu.com:http: [IP: 91.189.92.171 80]

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/natty-security/multiverse/source/Sources  Unable to connect to security.ubuntu.com:http: [IP: 91.189.92.171 80]

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/natty-security/main/binary-i386/Packages  Unable to connect to security.ubuntu.com:http: [IP: 91.189.92.171 80]

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/natty-security/restricted/binary-i386/Packages  Unable to connect to security.ubuntu.com:http: [IP: 91.189.92.171 80]

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/natty-security/universe/binary-i386/Packages  Unable to connect to security.ubuntu.com:http: [IP: 91.189.92.171 80]

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/natty-security/multiverse/binary-i386/Packages  Unable to connect to security.ubuntu.com:http: [IP: 91.189.92.171 80]

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/natty-security/main/i18n/Translation-en_US  Unable to connect to security.ubuntu.com:http: [IP: 91.189.92.171 80]

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/natty-security/main/i18n/Translation-en  Unable to connect to security.ubuntu.com:http: [IP: 91.189.92.171 80]

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/natty-security/multiverse/i18n/Translation-en_US  Unable to connect to security.ubuntu.com:http: [IP: 91.189.92.171 80]

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/natty-security/multiverse/i18n/Translation-en  Unable to connect to security.ubuntu.com:http: [IP: 91.189.92.171 80]

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/natty-security/restricted/i18n/Translation-en_US  Unable to connect to security.ubuntu.com:http: [IP: 91.189.92.171 80]

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/natty-security/restricted/i18n/Translation-en  Unable to connect to security.ubuntu.com:http: [IP: 91.189.92.171 80]

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/natty-security/universe/i18n/Translation-en_US  Unable to connect to security.ubuntu.com:http: [IP: 91.189.92.171 80]

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/natty-security/universe/i18n/Translation-en  Unable to connect to security.ubuntu.com:http: [IP: 91.189.92.171 80]

E: Some index files failed to download. They have been ignored, or old ones used instead.
[/HTML]

well i dont know well working with ubuntu but i am trying too too hard.If someone does not find this problem difficult,please give it a try to help me.
thank you

---

### Post by haqking on 2011-09-28
ok first of all lets be clear here.

The guide you are following uses examples of entries to make.

You seem to be making them verbatim.

such as the example.com domain.

you substitute to examples given in the guide for entries which suits your situation.

If i was you i would go back to some basic settings for now to give you internet access.

so add your 192.168.x.x addresses and gateway and the gateway is likely to be your DNS resolver entry also.

then go from there

---

### Post by gabikilalala on 2011-09-28
well thanks, 
sorry but i dont understand all things.
what basic settings?in which step?
i googled example.com and i realized that it is a domain.What should i try if not example.com?
and for the ip and the gateway?what do you mean dns resolver?
thanks

---

### Post by haqking on 2011-09-28
> **gabikilalala said:**
> well thanks, 
sorry but i dont understand all things.
what basic settings?in which step?
i googled example.com and i realized that it is a domain.What should i try if not example.com?
and for the ip and the gateway?what do you mean dns resolver?
thanks

OK forgive me if this sounds rude, it is not meant to, but it is apparent you are lacking some basic knowledge required here for what it seems you are trying to achieve (and by your own admission so please dont be offended).

So rather than troubleshoot what is going on here by the fact that you have copied the steps as laid out with examples instead of using your own valid information.

What is it you are actually trying to achieve here in the long run ?

So you have a install of 11.04 server correct ?

and you want it act as a server, doing what services exactly ?

is this to be a internet facing server ?

providing apache web services to the outside world ?

or merely for your own LAN ? and for using ISPCONFIG3 correct ?

so you have more server that you wish to manage by using ISPCONFIG3 correct ?

---

### Post by gabikilalala on 2011-09-28
well, 
firstly i like the way you talk because many of things you say are very correct.Yes i lack some knowledge but i am going deeper and deeper every day and that's way i am trying new things.
Well i have installed ubuntu server 11.04 32 bit on an old computer.
What i wanted firstly was to store all of my data on the a web server so i can reach this data from my laptop, my desktop, and later on my father can reach this for work mostly but my friends too. Later on i would like to have my own website on it. All this staff is something that i think i can handle with a little help.
So i want to install apache because i googled it and i think i should give it a try. I have already set up a ftp-server on the desktop and i found it very easy. 
Although, i would like to manage my web-server remotely and start learning what exactly are the security issues in a server.
So i test myself with this.And i am trying too hard and i am glad for all this information you have allready given to me.

So what do you suggest? I just started the server things. 

thanks

---

### Post by haqking on 2011-09-28
> **gabikilalala said:**
> well, 
firstly i like the way you talk because many of things you say are very correct.Yes i lack some knowledge but i am going deeper and deeper every day and that's way i am trying new things.
Well i have installed ubuntu server 11.04 32 bit on an old computer.
What i wanted firstly was to store all of my data on the a web server so i can reach this data from my laptop, my desktop, and later on my father can reach this for work mostly but my friends too. Later on i would like to have my own website on it. All this staff is something that i think i can handle with a little help.
So i want to install apache because i googled it and i think i should give it a try. I have already set up a ftp-server on the desktop and i found it very easy. 
Although, i would like to manage my web-server remotely and start learning what exactly are the security issues in a server.
So i test myself with this.And i am trying too hard and i am glad for all this information you have allready given to me.

So what do you suggest? I just started the server things. 

thanks

OK, now i am more confused then.

Because you are following a guide which is to setup ISPCONFIG3 which is software for managing multiple servers ?

So what you want simply is a Ubuntu server running which you can access remotely (ssh i presume) and you want it to host a website (apache)

---

### Post by gabikilalala on 2011-09-28
thank you very much for your help. Well i don't have more than one server. And honestly,,,,,i did not know exactly what the ispconfig is. I can feel now like an idiot..But never mind! I just saw all these programs and i assumed that i can learn them, but some of them i do not need...
So you suggest what? I want security on a server which i can store all data from desktop,laptop etc and have a site. All this staff about mail.clients? and this php etc..is there any guide or can you tell me what to look or to do? t
thanks

---

### Post by Dangertux on 2011-09-28
I am also confused -- but I'll try to help here. From looking at the tutorial you linked versus about how far you've gotten it seems the set up is failing right before step 8. Is that about right?

Right off the bat, there is an issue with what is going on with IP addresses here. So you need to answer a few questsion

1 - Where is this machine getting Internet access from?  Is it connected to a router which is connected to your ISP? Is it directly connected to your ISP? If so is eth0 what is connecting to your ISP? If yes, is it configured for DHCP or did YOU assign the 172.16.x address? 

*these are important, because they are likely why you have no connectivity.

2 - Are you entering the steps in the tutorial word for word? For instance if it saves your name server needs to be ns1.example.com , that would need to be the address of a REAL name server, whether it is your ISP's name server, or one you've created or rented, but it has to be a legit address. The same goes for all of the IP addresses, they aren't just made up numbers, so anywhere you are seeing generic numbers or example.com, you need to have actual information that goes in there. Using it as is with example.com will not function.

If you can answer these questions we can probably help you better.

EDIT : After reading your last post you might find these helpful

[https://help.ubuntu.com/11.04/serverguide/C/index.html](https://help.ubuntu.com/11.04/serverguide/C/index.html)
[http://dangertux.wordpress.com/tutorials/reasonably-secure-ubuntu-homesmall-business-server-tutorial/](http://dangertux.wordpress.com/tutorials/reasonably-secure-ubuntu-homesmall-business-server-tutorial/)
[http://www.ubuntugeek.com/step-by-step-ubuntu-11-04-natty-lamp-server-setup.html](http://www.ubuntugeek.com/step-by-step-ubuntu-11-04-natty-lamp-server-setup.html)

---

### Post by gabikilalala on 2011-09-28
Alright, i understand. Well when i am saying deeper and deeper i dont mean in this tutorial but in my linux experience and knowledge in a period of a year.
Well it is connected to a router which is connected to my ISP.eth0 is connecting to my ISP.
For the ip address firstly i gave the machine the 172.16.x.x...
But later i reinstalled ubuntu and i saw the ip the mchine had from dhcp configuration.So i edited /etc/network/interfaces for static ip and i gave it 192.168.1.x!
For the isp name do you mean i have to set it server_name.isp_name.com?
thanks

---

### Post by Iowan on 2011-09-28
[Here]("https://help.ubuntu.com/11.04/serverguide/C/index.html") is a Server Guide for 11.04 that may answer some of the questions you haven't asked yet. (Tuck it away for future reference).
There is also a [PDF]("https://help.ubuntu.com/11.04/serverguide/C/serverguide.pdf") version.

---

### Post by haqking on 2011-09-28
> **Iowan said:**
> [Here]("https://help.ubuntu.com/11.04/serverguide/C/index.html") is a Server Guide for 11.04 that may answer some of the questions you haven't asked yet. There is also a [PDF]("https://help.ubuntu.com/11.04/serverguide/C/serverguide.pdf") version.

yes this ^

and from the thread and the problems you have had i would suggest making sure you read the DNS and networking sections and make sure you understand them along with the TCP/IP section as you are obviously suffering with that.

Enjoy and good luck

---

### Post by gabikilalala on 2011-09-28
thank you guys,
but i have already read the tcp/ip and i have one question about the ip choice. For static ip i am taking any that we have already in ifconif?
and the .example.com replacement is isp_name.com?
maybe it is silly but it is a question right???
thanks!

---

### Post by BkkBonanza on 2011-09-28
If your router assigned you 172.16.161.130 then most likely trying to use a static IP outside it's range will not work. If you try to force a static IP of 192.168.0.100 it is outside the range that your router is listening to. If you want a static IP then you should give one like 172.16.161.130 or check the network range your router is using, or change the router to 192.168.0.* - either way will work. But mix-n-match won't do. Make sure when you change the settings in the interfaces file that the network and mask match up with your router values.

Another way to do static IP is to leave the interfaces file set for DHCP and then on your router assign a "static lease" - this causes the router to always assign the same IP even when using DHCP. Some routers don't use the name "static lease" but call it "server IP" or something like that.

If you can ping your router then make sure that the gateway setting in interfaces file matches your router IP otherwise you will have local LAN but no route to the internet.

---

### Post by gabikilalala on 2011-09-29
OK! I have done it!With your help, a lot of reading about tcp/ip information!
I ve searched almost everything in google!!And finally i have completed the [http://www.howtoforge.com/perfect-server-ubuntu-11.04-ispconfig-3-p5](http://www.howtoforge.com/perfect-server-ubuntu-11.04-ispconfig-3-p5) guide!
I looked the /etc/network/interfaces and i ran route -n so i can see what is going on! I realized that there was no destination! So i browsed to my router ip ( as i understant router is like a server that brings me to the internet connection to other servers in the net---correct me if  i am wrong ), and i looked for the "network ip" and i supposed that if i want the route -n prints me that there is specific route with destination, i had to go in the file interfaces, and fill in the network entry the network ip i found before.Also the getaway should be 192.168.x.1 for me..!
Although in the guide when it says example.com i found out that it means the domain for my server not my isp's name!!!
So i have now a working server with mailclient,ftpclient,apche2 installed etc

The problem i now have is that this moment i can clearly see what i really need!I want to store all my data on the server and next thing i want is to reach that data from a folder like home folder. Like mounting the server's drive on the desktop or my laptop. Is this possible in anyway? Only over the lan connection or from internet too?

Thank you very much for you time and help!

---

### Post by BkkBonanza on 2011-09-29
Yes, that is possible. There are a few different ways to do it.

Samba is popular if you want access from Win machines too.
NFS is good as well.

For a secure file system over ssh connections you can use sshfs, or just sftp which is already available in Nautilus by default and can be used over any ssh connection. eg. if your server is server.com and has ssh access then you can use sftp://username@server.com:/home/username as a location url in Nautilus.

Anyway, those are some topics to read up on and decide which will do for you.

---

### Post by gabikilalala on 2011-09-30
hello again, thanks for your reply. I'll try them. Well i have one more question (i propably won't stop aking..:)). I am getting in this page [http://www.whatsmyip.org/](http://www.whatsmyip.org/) this ip Your IP Address is 79.x.y.z. I have read that this is an a-class ip adress (1-127). Am i wrong? i am getting in my router settings and the same staff. But my rutters ip is 192.168.1.x. And my network's mask is 255.255.255.0. So, when we have a network 192.168.1.x we must have ip adresses 192.168.1.x. I have set 192.168.1.x as static ip on server then why it shows me for the desktop and laptop 79.x.y.z. The dhcp can give any address? I am confused again!!!
thanks

---

### Post by haqking on 2011-09-30
> **gabikilalala said:**
> hello again, thanks for your reply. I'll try them. Well i have one more question (i propably won't stop aking..:)). I am getting in this page [http://www.whatsmyip.org/](http://www.whatsmyip.org/) this ip Your IP Address is 79.x.y.z. I have read that this is an a-class ip adress (1-127). Am i wrong? i am getting in my router settings and the same staff. But my rutters ip is 192.168.1.x. And my network's mask is 255.255.255.0. So, when we have a network 192.168.1.x we must have ip adresses 192.168.1.x. I have set 192.168.1.x as static ip on server then why it shows me for the desktop and laptop 79.x.y.z. The dhcp can give any address? I am confused again!!!
thanks

Your router has 2 interface (some have more), one for outside (WAN) one for inside (LAN) your WAN IP address is the one assigend to your router from your ISP, your LAN addresses are reserved and not used on the Internet.  192.168.x.x is a class C reserved address space for LAN usage and the most common.

Your WAN IP (the one from the whatismyip) is the address assigned to your internet connection from your ISP.

If you setup a server on your LAN it would have a 192.168.x.x address so all machines on the LAN could talk to it, its gateway to the internet would be your router IP address, probably 192.168.0.1 or similar.

You could access that server from across the internet by heading to your WAN IP address and having your router forward requests for your server from its WAN address to the servers LAN address internally.

---

### Post by gabikilalala on 2011-09-30
well thanks,
So 1).If i want to reach my server from another city let's say i have to browse to my wan ip?And how to do that?Do i have to set a wan static ip? How can i do that?Or do i have to reach my server over the domain name?please help me to understand
   2).For the lan, Do i have to set static ip on the other machines?with ip addresses similar to 192.168.x.y?And then make the data shared with nfs?with mounting the drives.
   3).a question for me, to make sure that i make everything right..-->the way for the ip address is :
setting static in the file /etc/network/interfaces
and giving address,netmask,network,broadcast,gateway. After that..
giving the name server on /etc/resolv.conf (what should i give?)
is there anything else i should do?( i think the /etc/hosts change is optional or am i wrong?
I think that after those qusetions i do not have to ask anything else about ips..
thank you very much!

---

### Post by gabikilalala on 2011-10-01
hello everyone,

My first question is:Is it is possible to create my own e-mail adress? (xxxxx@my_name or my company name.com)
if yes,
My second question is:How??( I have configured ispconfig3 on my ubuntu server 11.04--so i am trying to understand how this thing works..)It has the option of making email domains,but what exactly do i have to do?
Thank you for your time!

---

### Post by gabikilalala on 2011-10-01
anyone???thanks!

---

### Post by gabikilalala on 2011-10-01
anyone??

---

### Post by volkswagner on 2011-10-01
You will first need to purchase/register the domain you'd like to use.   You can then either use a hosting solution for email, or run your own mail server.

---

### Post by haqking on 2011-10-01
> **gabikilalala said:**
> hello everyone,

My first question is:Is it is possible to create my own e-mail adress? (xxxxx@my_name or my company name.com)
if yes,
My second question is:How??( I have configured ispconfig3 on my ubuntu server 11.04--so i am trying to understand how this thing works..)It has the option of making email domains,but what exactly do i have to do?
Thank you for your time!

As i mentioned before, ISPConfig3 is a central control panel interface for managing multiple servers, which you dont have as you have a server at home which i understood you wanted to be a web/file server.

You need to purchase a domain name from the internic (or a registrar such as godaddy who will give you one) then you can host that yourself if you like depedning on your setup at home, such as DNS etc

---

### Post by haqking on 2011-10-01
> **gabikilalala said:**
> well thanks,
So 1).If i want to reach my server from another city let's say i have to browse to my wan ip?And how to do that?Do i have to set a wan static ip? How can i do that?Or do i have to reach my server over the domain name?please help me to understand
   2).For the lan, Do i have to set static ip on the other machines?with ip addresses similar to 192.168.x.y?And then make the data shared with nfs?with mounting the drives.
   3).a question for me, to make sure that i make everything right..-->the way for the ip address is :
setting static in the file /etc/network/interfaces
and giving address,netmask,network,broadcast,gateway. After that..
giving the name server on /etc/resolv.conf (what should i give?)
is there anything else i should do?( i think the /etc/hosts change is optional or am i wrong?
I think that after those qusetions i do not have to ask anything else about ips..
thank you very much!

1. You will need to purchase a static IP from your ISP or use dynamic DNS which there are a few providers on the net, you can then browse to that IP and if set up correctly will forward the request to your internal WEB Server on port 80.

2. statics on your lan are good for services, but DHCP can be used for desktop machines.

3.  The DNS resolver you use depends on you, if your using your own, ISP or external to that, alot of people use googles DNS servers, i run a script to find my fastest and use that on my router, then use my router as my resolver.

all these questions should be answered in the links provided so far for setting up a server, dns, TCP/IP, Apache, etc etc

cheers

---

### Post by lisati on 2011-10-01
> **gabikilalala said:**
> anyone???thanks!

Please see the replies in your other thread.

---

### Post by gabikilalala on 2011-10-01
Ok! Well maybe my questions should have been answered already reading the guides..!i am reading them again, but thank you for your help.I am thinking of running virtual machines one for website one for mail one for file..!(from what you say about ispconfig i understand that it controls multiple machines and not installed features on the server--mail,ftp,apache etc--Am i correct)>Anyway, i am thinking of virtual machines to have custom mail adress hosted on mail server website hosted on web server etc. Any advice of you will be great.

Thank you

---

### Post by gabikilalala on 2011-10-01
oh, one more thing! When you say dynamic dns can you help me about it? Do i have to take a google dns server as you said? And edit my router's dns entry? What exactly do i have to do? Is there any guide?
thanks again!

---

### Post by haqking on 2011-10-02
> **gabikilalala said:**
> Ok! Well maybe my questions should have been answered already reading the guides..!i am reading them again, but thank you for your help.I am thinking of running virtual machines one for website one for mail one for file..!(from what you say about ispconfig i understand that it controls multiple machines and not installed features on the server--mail,ftp,apache etc--Am i correct)>Anyway, i am thinking of virtual machines to have custom mail adress hosted on mail server website hosted on web server etc. Any advice of you will be great.

Thank you

> **gabikilalala said:**
> oh, one more thing! When you say dynamic dns can you help me about it? Do i have to take a google dns server as you said? And edit my router's dns entry? What exactly do i have to do? Is there any guide?
thanks again!

It will use more resources having multiple machines than running the multiple services.

From what you have described you have a home network so there it not going to be any load on the machine, just run the server services on the server, setting up a virtual machine on it will use more resrouces.

You dont need ISP3Config

LIke i said you can use any DNS resolver that is valid.

Dnynamic DNS, purchase a name that follows your IP address such as from [http://dyn.com/dns/dyndns-free/](http://dyn.com/dns/dyndns-free/) or tons of others, google for Dynamic DNS


As for is there a guide for setting up your DNS, yes the server guide which TCP/IP and DNS in there.

---

### Post by gabikilalala on 2011-10-02
OK!!!I will remove isp config. I am going then to rinstall ubuntu server 11.04 32 bit setting static ips and using dynamic dns services!(i am thinking of something like lamp with mail services installed like i the ispconfig3 guide)!Will i be able to have my custom email addresses through those mail services?Or do i have to have onother machine?Give me some help to understand!thanks!! Any suggest will be great!

---

### Post by gabikilalala on 2011-10-03
Well every day i feel more confident.But still i have questions!
[http://brunogirin.blogspot.com/2007/11/dhcp-and-dynamic-dns-on-ubuntu-server.html](http://brunogirin.blogspot.com/2007/11/dhcp-and-dynamic-dns-on-ubuntu-server.html) 
This is a tutorial of how setting up dhcp and dynamic dns server. I'd like to ask if this server is doing the same work as a server used by this site 
[https://www.dyndns.com](https://www.dyndns.com)
So my main question is:If set up the server from this tutorial is the same thing as registering and using dyndns.com?Or the first is for local networking?
Is it working as the router? So even if i set up this server a must register and use dyndns.com?
thanks!

---

### Post by gabikilalala on 2011-10-03
any help??

---

### Post by gabikilalala on 2011-10-06
Stupid questions ah?

---

### Post by haqking on 2011-10-06
> **gabikilalala said:**
> Stupid questions ah?

Install your server, give it a static IP for the LAN. POrt forward from your router requests for given services to your server via its LAN IP, such as port 80 for web server, 22 for SSH etc.

Assign a static IP to your router WAN if you have one from your ISP or use dyndns from the links provided to allow you to track your WAN IP changes.

Once you have that up and running (without following tutorials which install services you dont need such as ISPConfig3) then it is working and you have what you need, then you can look at changing things and playing once its setup and have backups.

For setting up the server and services in the first place then as provided previously [https://help.ubuntu.com/10.04/serverguide/C/index.html](https://help.ubuntu.com/10.04/serverguide/C/index.html)

---

### Post by gabikilalala on 2011-10-06
Ok!So do you think that port forwarding is better confiqured from the router settings or from the linux system via a script or something like that.?Can you suggest anything about it?thanks

---

### Post by haqking on 2011-10-06
> **gabikilalala said:**
> Ok!So do you think that port forwarding is better confiqured from the router settings or from the linux system via a script or something like that.?Can you suggest anything about it?thanks

it is done on your router as it is your router that is forwarding the requests to your LAN IP.

look at the documentation of your router

---

### Post by gabikilalala on 2011-10-07
thank you very very much dude!I am trying to configure basic server from the official guide!Thanks, I have learned many things through this. Well maybe i will have more questions when playing with my server.Can you help me in this thread?
[http://ubuntuforums.org/showthread.php?t=1854058](http://ubuntuforums.org/showthread.php?t=1854058)
Thanks!

---

### Post by CharlesA on 2011-10-07
Hiya,

I am going to close this thread since it looks like the problem is solved and y'all are working on another problem in another thread.

Thanks,
Charles

---

