---
title: "Unknwon Instance"
date: 2013-02-12
forum: Server Platforms
---

### Post by chrisguk on 2013-02-12
Hi,

Can you assist with possible reasons why I would get this unknown instance message after restarting my networking:

```


sudo service networking restart
stop: Unknown instance:
networking stop/waiting


```

I have DNS BIND9 setup and isc-dhcp-server

Also if I issue the NSLOOKUP like this, is this the correct output:

```


 nslookup simpson.home
Server:         172.22.22.100
Address:        172.22.22.100#53

*** Can't find simpson.home: No answer


```

here is my zone files:
```


$TTL 3D
@       IN      SOA     ralph.simpson.home. admin.simpson.home. (
                        2013011403;
                        28800;
                        3600;
                        604800;
                        3600

);

simpson.home.   IN      NS   ralph.simpson.home.
simpson.home.   IN      NS   ralph2.simpson.home.
router          IN      A       172.22.22.100
link            IN      A       172.22.22.25
marge           IN      A       172.22.22.30
akira           IN      A       172.22.22.35
maggie          IN      A       172.22.22.40
lisa            IN      A       172.22.22.45
www             IN      A       172.22.22.50
homer           IN      A       172.22.22.55
ralph           IN      A       172.22.22.100
ralph2          IN      A       172.22.22.101



```

```


$TTL 3D
@       IN      SOA     ralph.simpson.home. admin.simpson.home. (
                        2013011307;
                        28800;
                        3600;
                        604800;
                        38400
);

                        IN      NS      ralph.simpson.home.
                        IN      NS      ralph2.simpson.home.
40                      IN      PTR     router.simpson.home.
25                      IN      PTR     link.simpson.home.
30                      IN      PTR     marge.simpson.home.
35                      IN      PTR     akira.simpson.home.
40                      IN      PTR     maggie.simpson.home.
45                      IN      PTR     lisa.simpson.home.
50                      IN      PTR     www.simpson.home.
100                     IN      PTR     ralph.simpson.home.
101                     IN      PTR     ralph.simpson.home.


```

---

### Post by Doug S on 2013-02-12
Doesn't your unkown instance problem just indicate that the network service was already stopped when it was asked to stop? At least that is what I found when I tried it on one of my test computers.> Also if I issue the NSLOOKUP like this, is this the correct output:It is for the zone file you are using as there is no lookup for the base domain name. If you want base name lookup to work, try this version of your zone file:```
;
; BIND data for simpson.home
;
$TTL 3D
@       IN      SOA     simpson.home. admin.simpson.home. (
                        2013021201   ; Serial
                        28800        ; Refresh
                        3600         ; Retry
                        604800       ; Expire
                        3600 )       ; Negative Cache TTL
                IN      A       172.22.22.100
;
@               IN      NS   ralph.simpson.home.
@               IN      NS   ralph2.simpson.home.
router          IN      A       172.22.22.100
link            IN      A       172.22.22.25
marge           IN      A       172.22.22.30
akira           IN      A       172.22.22.35
maggie          IN      A       172.22.22.40
lisa            IN      A       172.22.22.45
www             IN      A       172.22.22.50
homer           IN      A       172.22.22.55
ralph           IN      A       172.22.22.100
ralph2          IN      A       172.22.22.101
```

---

### Post by chrisguk on 2013-02-12
Hi Doug and thanks for your reply.

The second issue I will take a look at in a moment.

The first issue.  I am not sure what the issue with this is, would I be right to assume that if I have access to the machine via SSH, I am able to ping the machine then the network interface is up and running?

Any further assistance will be gratefully received ;)


**EDIT:   Awesome thanks Doug the zone file worked.  I will update my docs to reflect the change ;)  Do I need to make any changes to the reverse lookup file now?**

---

### Post by chrisguk on 2013-02-12
The following NSLOOKUP is not working either.  I issued the dig command too to try to find out what is wrong to no avail.  Any ideas?

```


waiting for pid 8115 to die
                                                                                                                              [ OK ]
 * Starting domain name service... bind9                                                                                      [ OK ]
chrisguk@ralph:/etc/bind$ nslookup 172.22.22.100
Server:         172.22.22.100
Address:        172.22.22.100#53

** server can't find 100.22.22.172.in-addr.arpa.: NXDOMAIN

chrisguk@ralph:/etc/bind$ dig 172.22.22.100

; <<>> DiG 9.8.1-P1 <<>> 172.22.22.100
;; global options: +cmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NXDOMAIN, id: 16025
;; flags: qr rd ra; QUERY: 1, ANSWER: 0, AUTHORITY: 1, ADDITIONAL: 0

;; QUESTION SECTION:
;172.22.22.100.                 IN      A

;; AUTHORITY SECTION:
.                       1800    IN      SOA     a.root-servers.net. nstld.verisign-grs.com. 2013021201 1800 900 604800 86400

;; Query time: 91 msec
;; SERVER: 172.22.22.100#53(172.22.22.100)
;; WHEN: Tue Feb 12 22:00:12 2013
;; MSG SIZE  rcvd: 106



```

This is my reverse zone file:


```


$TTL 3D
@       IN      SOA     simpson.home. admin.simpson.home. (
                        2013011307;
                        28800;
                        3600;
                        604800;
                        38400
);

@                       IN      NS      ralph.simpson.home.
@                       IN      NS      ralph2.simpson.home.
40                      IN      PTR     router.simpson.home.
25                      IN      PTR     link.simpson.home.
30                      IN      PTR     marge.simpson.home.
35                      IN      PTR     akira.simpson.home.
40                      IN      PTR     maggie.simpson.home.
45                      IN      PTR     lisa.simpson.home.
50                      IN      PTR     www.simpson.home.
100                     IN      PTR     ralph.simpson.home.
101                     IN      PTR     ralph2.simpson.home.



```

---

### Post by Doug S on 2013-02-12
Did reverse lookups work before? I don't know why you changed the reverse zone file, I would not have other than to: have an @ at the start of the NS lines, and make the reverse of 101 ralph2 instead of ralph.
 
On the first issue, "Unkown Instance", yes it seems your netowrk was up, so then I don't know.

---

### Post by chrisguk on 2013-02-12
> **Doug S said:**
> Did reverse lookups work before? I don't know why you changed the reverse zone file, I would not have other than to: have an @ at the start of the NS lines, and make the reverse of 101 ralph2 instead of ralph.
 
On the first issue, "Unkown Instance", yes it seems your netowrk was up, so then I don't know.

Hi,

No the reverse didn't work before either.  I just changed it to the below and as you can see still nothing:

```


$TTL 3D
@       IN      SOA     simpson.home. admin.simpson.home. (
                        2013011307;
                        28800;
                        3600;
                        604800;
                        38400
);

@                       IN      NS      ralph.simpson.home.
@                       IN      NS      ralph2.simpson.home.
40                      IN      PTR     router.simpson.home.
25                      IN      PTR     link.simpson.home.
30                      IN      PTR     marge.simpson.home.
35                      IN      PTR     akira.simpson.home.
40                      IN      PTR     maggie.simpson.home.
45                      IN      PTR     lisa.simpson.home.
50                      IN      PTR     www.simpson.home.
100                     IN      PTR     ralph.simpson.home.
101                     IN      PTR     ralph2.simpson.home.
chrisguk@ralph:/etc/bind$ sudo nano zones/rev.22.22.172.in-addr.arpa
[sudo] password for chrisguk:
chrisguk@ralph:/etc/bind$ sudo service bind9 restart
 * Stopping domain name service... bind9                                                                                             waiting for pid 8255 to die
                                                                                                                              [ OK ]
 * Starting domain name service... bind9                                                                                      [ OK ]
chrisguk@ralph:/etc/bind$ nslookup 172.22.22.100
Server:         172.22.22.100
Address:        172.22.22.100#53

** server can't find 100.22.22.172.in-addr.arpa.: NXDOMAIN



```


Here is my zone file include:

```


#FORWARD
zone "simpson.home"
{

        type master;
        file "/etc/bind/zones/simpson.home.db";

};


#REVERSE
zone "22.22.172.in-addr-arpa"
{

        type master;
        file "/etc/bind/zones/rev.22.22.172.in-addr.arpa";

};



```

---

### Post by Doug S on 2013-02-12
Change this line:```
zone "22.22.172.in-addr[COLOR=red]-[/COLOR]arpa"

```to this:```
zone "22.22.172.in-addr[COLOR=red].[/COLOR]arpa"

```and restore your SOA line, in the reverse file, to what it used to be.```
@       IN      SOA     ralph.simpson.home. admin.simpson.home. (

```

---

### Post by chrisguk on 2013-02-12
Thats quite embarrassing to be honest.  I go to all that trouble of typing the code out and make a stupid mistake like that.

**[COLOR="Red"][SIZE="2"]Point to note:  Tired eyes = fail[/SIZE][/COLOR]**

I still have this unknown instance thing going on so I will do some more research into this area.

Everything works as desired.  Thank you for being patient with me.

---

### Post by Doug S on 2013-02-12
Oh, and by the way, you should bump the file serial number every time you edit it. You seem to be using the YYYYMMDDXX format, where XX is the edit number on any given day. However, you do not appear to be modifiing it. Upon start or re-start, bind might not know that the file needs to be re-parsed if the serial number is not changed.

---

### Post by Doug S on 2013-02-12
O.K., glad you got it working (the lookups part, at least). I recommand to take a moment to test everything, all possible forward and reverse lookups and whatever, from all clients, before moving forward from here.

---

### Post by chrisguk on 2013-02-12
> **Doug S said:**
> O.K., glad you got it working (the lookups part, at least). I recommand to take a moment to test everything, all possible forward and reverse lookups and whatever, from all clients, before moving forward from here.


Serial numbers changed......

Just checking All possible combinations now.

---

### Post by chrisguk on 2013-02-12
Windows machine not working.  I flushed the DNS too:

```


C:\Users\chrisguk>nslookup ralph
DNS request timed out.
    timeout was 2 seconds.
Server:  UnKnown
Address:  172.22.22.40

DNS request timed out.
    timeout was 2 seconds.
DNS request timed out.
    timeout was 2 seconds.
*** Request to UnKnown timed-out


```

weird

---

### Post by chrisguk on 2013-02-12
okay I am getting closer:

Here is the output now:

```



C:\Users\chrisguk>nslookup ralph
Server:  ralph.simpson.home
Address:  172.22.22.100

*** ralph.simpson.home can't find ralph: Non-existent domain



```

---

### Post by Doug S on 2013-02-12
It looks as though your windows computer does not know to autoappend the dns suffix. What does "ipconfing /all" reveal? Example:```
C:\Users\Doug>ipconfig /all
Windows IP Configuration
   Host Name . . . . . . . . . . . . : Doug-XPS
   Primary Dns Suffix  . . . . . . . :
   Node Type . . . . . . . . . . . . : Hybrid
   IP Routing Enabled. . . . . . . . : No
   WINS Proxy Enabled. . . . . . . . : No
   [COLOR=red]DNS Suffix Search List. . . . . . : smythies.com[/COLOR]
Ethernet adapter Local Area Connection:
   [COLOR=red]Connection-specific DNS Suffix  . : smythies.com[/COLOR]
   Description . . . . . . . . . . . : Broadcom NetXtreme 57xx Gigabit Controller
   Physical Address. . . . . . . . . : 00-21-9B-F9-21-26
   DHCP Enabled. . . . . . . . . . . : Yes
   Autoconfiguration Enabled . . . . : Yes
   IPv4 Address. . . . . . . . . . . : 192.168.111.101(Preferred)
   Subnet Mask . . . . . . . . . . . : 255.255.255.0
   Lease Obtained. . . . . . . . . . : January-29-2013 21:35:20
   Lease Expires . . . . . . . . . . : February-13-2013 09:35:28
   Default Gateway . . . . . . . . . : 192.168.111.1
   DHCP Server . . . . . . . . . . . : 192.168.111.1
   DNS Servers . . . . . . . . . . . : 192.168.111.1
   NetBIOS over Tcpip. . . . . . . . : Disabled
```Have a look at this recent thread (start at about post 4): [http://ubuntuforums.org/showthread.php?t=2112686&highlight=abbreviated](http://ubuntuforums.org/showthread.php?t=2112686&highlight=abbreviated)

---

### Post by chrisguk on 2013-02-12
Ahhh, I dont have that.  Ill check that post out now.

```


Windows IP Configuration

   Host Name . . . . . . . . . . . . : akira
   Primary Dns Suffix  . . . . . . . :
   Node Type . . . . . . . . . . . . : Hybrid
   IP Routing Enabled. . . . . . . . : No
   WINS Proxy Enabled. . . . . . . . : No

Ethernet adapter Local Area Connection:

   Media State . . . . . . . . . . . : Media disconnected
   Connection-specific DNS Suffix  . :
   Description . . . . . . . . . . . : TAP-Win32 Adapter V9
   Physical Address. . . . . . . . . : 00-FF-CD-1E-DB-69
   DHCP Enabled. . . . . . . . . . . : Yes
   Autoconfiguration Enabled . . . . : Yes

Ethernet adapter Ethernet:

   Connection-specific DNS Suffix  . :
   Description . . . . . . . . . . . : Atheros L1 Gigabit Ethernet 10/100/1000
se-T Controller
   Physical Address. . . . . . . . . : 00-1D-60-AE-DE-C3
   DHCP Enabled. . . . . . . . . . . : No


```

---

### Post by CharlesA on 2013-02-12
FWIW, I messed with some of this stuff the other day when trying to figure out why some names on my home network would resolve and some wouldn't.

The dns connection specific suffix is set via DHCP and the only way I found to restart networking was via:

```
sudo /etc/init.d/networking restart
```

I don't know why ```
sudo service networking restart
```

Did not work, however.

---

### Post by matt_symes on 2013-02-12
Hi

Out of interest, what does this return ?

```
sudo initctl list | grep networking
```

Kind regards

---

### Post by CharlesA on 2013-02-12
Ubuntu Server 12.04 x64

```
charles@Thor:~$ sudo initctl list | grep networking
network-interface-security (networking) start/running
networking stop/waiting
```

I took out the ing and it returned this:

```
charles@Thor:~$ sudo initctl list | grep network
network-interface (vboxnet0) start/running
network-interface (lo) start/running
network-interface (eth0) start/running
network-interface-security (network-interface/eth0) start/running
network-interface-security (network-interface/vboxnet0) start/running
network-interface-security (network-interface/lo) start/running
network-interface-security (networking) start/running
networking stop/waiting
network-interface-container stop/waiting

```

---

### Post by matt_symes on 2013-02-12
That's odd. This is mine
```

matthew-S206:/home/matthew/iplayer % sudo initctl list | grep network
network-manager stop/waiting
network-interface (lo) start/running
network-interface (eth0) start/running
network-interface-security (network-manager) start/running
network-interface-security (network-interface/eth0) start/running
network-interface-security (network-interface/lo) start/running
network-interface-security (networking) start/running
networking start/running
network-interface-container stop/waiting
matthew-S206:/home/matthew/iplayer %
```

Are the config files good ? What does this return ?

```
sudo initctl check-config
```

---

### Post by CharlesA on 2013-02-12
```
charles@Thor:~$ sudo initctl check-config
plymouth
  start on: unknown job uxlaunch
  start on: unknown job xdm
  start on: unknown event desktop-shutdown
plymouth-stop
  start on: unknown job oem-config
  start on: unknown job ubiquity
  start on: unknown job uxlaunch
  start on: unknown job lightdm
  start on: unknown job lxdm
  start on: unknown job xdm
  start on: unknown job kdm
  start on: unknown job gdm

```

Server box, no GUI. When I run those commands on my desktop VM, they spit out:

```
charles@Precise:~$ sudo initctl list | grep network
network-manager start/running, process 946
network-interface (lo) start/running
network-interface (eth0) start/running
network-interface-security (network-manager) start/running
network-interface-security (network-interface/eth0) start/running
network-interface-security (network-interface/lo) start/running
network-interface-security (networking) start/running
networking stop/waiting
network-interface-container stop/waiting

```

```
charles@Precise:~$ sudo initctl check-config
plymouth-stop
  start on: unknown job lxdm
  start on: unknown job xdm
  start on: unknown job kdm
  start on: unknown job gdm

```

....

Both these boxes have been rebooted recently and networking works fine.

EDIT: If I try to start the service, it doesn't do anything.

```
charles@Precise:~$ sudo service networking start
networking stop/waiting

```

---

### Post by matt_symes on 2013-02-12
I'll have to check on my server tomorrow.

---

### Post by CharlesA on 2013-02-12
> **matt_symes said:**
> I'll have to check on my server tomorrow.
Thanks! I just tried checking my 10.04 box that I haven't touched in a long time and it spit back that check-config isn't a valid option for initctl.

Hmmmm......

---

### Post by Doug S on 2013-02-13
> **chrisguk said:**
> Ahhh, I dont have that. Ill check that post out now.
 
```

 
Windows IP Configuration
 
   Host Name . . . . . . . . . . . . : akira
   Primary Dns Suffix  . . . . . . . :
   Node Type . . . . . . . . . . . . : Hybrid
   IP Routing Enabled. . . . . . . . : No
   WINS Proxy Enabled. . . . . . . . : No
 
Ethernet adapter Local Area Connection:
 
   Media State . . . . . . . . . . . : Media disconnected
   Connection-specific DNS Suffix  . :
   Description . . . . . . . . . . . : TAP-Win32 Adapter V9
   Physical Address. . . . . . . . . : 00-FF-CD-1E-DB-69
   DHCP Enabled. . . . . . . . . . . : Yes
   Autoconfiguration Enabled . . . . : Yes
 
Ethernet adapter Ethernet:
 
   Connection-specific DNS Suffix  . :
   Description . . . . . . . . . . . : Atheros L1 Gigabit Ethernet 10/100/1000
se-T Controller
   Physical Address. . . . . . . . . : 00-1D-60-AE-DE-C3
   DHCP Enabled. . . . . . . . . . . : No
 

```I don't understand your "ipconfig /all" listing. I don't understand why there is no IP address. I don't understand why DHCP is not enabled (based on other threads, I thought your server was also a DHCP server).

---

### Post by CharlesA on 2013-02-13
> **Doug S said:**
> I don't understand your "ipconfig /all" listing. I don't understand why there is no IP address. I don't understand why DHCP is not enabled (based on other threads, I thought your server was also a DHCP server).

Good catch. I think he is running a *nix box with DHCP/DNS and that was from the Windows box that is having problems resolving hostnames to IPs.

I wonder if running ipconfig /renew would do anything.

Well that and enabling DHCP on the second network interface.

---

### Post by chrisguk on 2013-02-13
> **Doug S said:**
> I don't understand your "ipconfig /all" listing. I don't understand why there is no IP address. I don't understand why DHCP is not enabled (based on other threads, I thought your server was also a DHCP server).


Hi Doug,

I re-enabled DHCP on the Windows client so yes you are absolutely right the server does have DHCP enabled, is that the correct thing to do?

Here is my output from the ipconfig now:

```


Windows IP Configuration

   Host Name . . . . . . . . . . . . : akira
   Primary Dns Suffix  . . . . . . . : simpson.home
   Node Type . . . . . . . . . . . . : Hybrid
   IP Routing Enabled. . . . . . . . : No
   WINS Proxy Enabled. . . . . . . . : No
   DNS Suffix Search List. . . . . . : akira.simpson.hom

Ethernet adapter Local Area Connection:

   Media State . . . . . . . . . . . : Media disconnected
   Connection-specific DNS Suffix  . :
   Description . . . . . . . . . . . : TAP-Win32 Adapter V9
   Physical Address. . . . . . . . . : 00-FF-CD-1E-DB-69
   DHCP Enabled. . . . . . . . . . . : Yes
   Autoconfiguration Enabled . . . . : Yes

Ethernet adapter Ethernet:

   Connection-specific DNS Suffix  . : simpson.home
   Description . . . . . . . . . . . : Atheros L1 Gigabit Ethernet 10/100/1000Ba
se-T Controller
   Physical Address. . . . . . . . . : 00-1D-60-AE-DE-C3
   DHCP Enabled. . . . . . . . . . . : Yes
   Autoconfiguration Enabled . . . . : Yes
   Link-local IPv6 Address . . . . . : fe80::11da:2e77:b0bd:3dc7%12(Preferred)
   IPv4 Address. . . . . . . . . . . : 172.22.22.35(Preferred)
   Subnet Mask . . . . . . . . . . . : 255.255.255.0
   Lease Obtained. . . . . . . . . . : 13 February 2013 15:11:45
   Lease Expires . . . . . . . . . . : 13 February 2013 16:11:46
   Default Gateway . . . . . . . . . : 172.22.22.100
   DHCP Server . . . . . . . . . . . : 172.22.22.100
   DHCPv6 IAID . . . . . . . . . . . : 251665760
   DHCPv6 Client DUID. . . . . . . . : 00-01-00-01-18-A9-FF-E2-00-1D-60-AE-DE-C3

   DNS Servers . . . . . . . . . . . : 172.22.22.100
                                       172.22.22.101
   NetBIOS over Tcpip. . . . . . . . : Enabled


```

Does that look right to you?

---

### Post by Doug S on 2013-02-13
> Here is my output from the ipconfig now:
...
Does that look right to you?I do not know. It looks slightly different than mine, but I don't know that mine is the reference for being correct. I only know that short name lookups work fine. Go back and try the short name nslookup again. Here is an example from my windows vista LapTop:```
C:\Users\Doug\temp>nslookup s15
Server:  ns1.smythies.com
Address:  192.168.111.1
Name:    s15.smythies.com
Address:  192.168.111.112
```> I re-enabled DHCP on the Windows client so yes you are absolutely right the server does have DHCP enabled, is that the correct thing to do?Well, as I understand your network, both from this and other threads, yes.

---

### Post by chrisguk on 2013-02-13
> **Doug S said:**
> I do not know. It looks slightly different than mine, but I don't know that mine is the reference for being correct. I only know that short name lookups work fine. Go back and try the short name nslookup again. Here is an example from my windows vista LapTop:```
C:\Users\Doug\temp>nslookup s15
Server:  ns1.smythies.com
Address:  192.168.111.1
Name:    s15.smythies.com
Address:  192.168.111.112
```Well, as I understand your network, both from this and other threads, yes.

Hi Doug,

something must be wrong.  This is my output:

```



C:\Users\chrisguk>nslookup ralph
Server:  ralph.simpson.home
Address:  172.22.22.100

*** ralph.simpson.home can't find ralph: Non-existent domain


```

---

### Post by Doug S on 2013-02-13
Clarify please. What reverse lookups work and don't work and from what clients, both short and long names. From previous postings I had assumed that only short name lookups and only from the particular windows computer, akira, were not working. However, and based on your posting just now, my assumption must be wrong (I think).

---

### Post by chrisguk on 2013-02-13
Hi I'm away from the terminal right now, I will do a complete test later and post all the results

---

### Post by Doug S on 2013-02-13
For the "Unkown Instance" part of this thread: To clarify my initial posting (#2) and using the very cool "script" command, here is what I did that resulted in my original reply:```
Script started on Wed 13 Feb 2013 08:06:34 AM PST
 
doug@test-smy:~$ ping -c 2 192.168.111.1
PING 192.168.111.1 (192.168.111.1) 56(84) bytes of data.
64 bytes from 192.168.111.1: icmp_req=1 ttl=64 time=0.762 ms
64 bytes from 192.168.111.1: icmp_req=2 ttl=64 time=0.351 ms
--- 192.168.111.1 ping statistics ---
2 packets transmitted, 2 received, 0% packet loss, time 1009ms
rtt min/avg/max/mdev = 0.351/0.556/0.762/0.206 ms
doug@test-smy:~$ [COLOR=red]sudo service networking stop[/COLOR]
[sudo] password for doug: 
networking stop/waiting
doug@test-smy:~$ ping -c 2 192.168.111.1
connect: Network is unreachable
doug@test-smy:~$ [COLOR=red]sudo service networking restart[/COLOR]
[COLOR=red]stop: Unknown instance:[/COLOR] 
networking start/running
doug@test-smy:~$ ping -c 2 192.168.111.1
PING 192.168.111.1 (192.168.111.1) 56(84) bytes of data.
64 bytes from 192.168.111.1: icmp_req=1 ttl=64 time=0.439 ms
64 bytes from 192.168.111.1: icmp_req=2 ttl=64 time=0.353 ms
--- 192.168.111.1 ping statistics ---
2 packets transmitted, 2 received, 0% packet loss, time 1007ms
rtt min/avg/max/mdev = 0.353/0.396/0.439/0.043 ms
doug@test-smy:~$ exit
exit
Script done on Wed 13 Feb 2013 08:08:19 AM PST

```

---

### Post by Doug S on 2013-02-13
> **Doug S said:**
> Clarify please. What reverse lookups work and don't work and from what clients, both short and long names. From previous postings I had assumed that only short name lookups and only from the particular windows computer, akira, were not working. However, and based on your posting just now, my assumption must be wrong (I think).Sorry, I completley mis-read the posting. Nothing has changed, and your windows box is still not auto-appending the domain stuff and thus not submitting the proper long name for reverse lookup. Conclusion: My ipconfig /all output is more like what is needed. Post your dhcpd.conf file, and make sure it contains a line like this (but for your domain):```
option domain-name "smythies.com";
```

---

### Post by chrisguk on 2013-02-13
> **Doug S said:**
> Sorry, I completley mis-read the posting. Nothing has changed, and your windows box is still not auto-appending the domain stuff and thus not submitting the proper long name for reverse lookup. Conclusion: My ipconfig /all output is more like what is needed. Post your dhcpd.conf file, and make sure it contains a line like this (but for your domain):```
option domain-name "smythies.com";
```

Okay, its all fixed.  Everything is displaying the correct output.

Promise me you won't laugh???

[COLOR="Red"]Point to note:  When testing the local machine on a LAN to ensure it resolves to the local DNS make sure you disconnect that machine from the VPN service especially if that service is using its own DNS[/COLOR]

---

