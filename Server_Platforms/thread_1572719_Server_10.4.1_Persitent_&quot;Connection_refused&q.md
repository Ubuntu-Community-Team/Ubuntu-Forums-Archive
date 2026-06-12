---
title: "Server 10.4.1: Persitent &quot;Connection refused&quot;"
date: 2010-09-11
forum: Server Platforms
---

### Post by Fraaik on 2010-09-11
Hello forum users!

I've often visited this site and I have used Ubuntu as "client" for long.

Last week I dicded to install Ubuntu Server 10.4.1 on a brand new Dell PowerEdge R310.
(In the past I installed several Servers based on Debian).

Installation worked fine and quick. Base installation is done without any additional software (which where offered during first installation).
IP is set static - no DHCP.

For documentation reasons I want to install more software remote (putty from a windows machine). First I did a "sudo apt-get install ssh openssh-server".
This installation went ok and ssh server is runing: login from "localhost" works.

But login from any other machine results in "connection refused".
Checking port 22 with nmap says "port closed". (ping works)

My search on this issue yields that "ufw" is a part of Ubuntu Server.
After checking this "ufw" is diasbled.

But why always the connection is refued?
Two days I did testings and trials but got no resolution...
Does anyone have an idea, what goes wrong here??

Any hint is welcome!

Cheers
Fraaik

---

### Post by thingy on 2010-09-11
1. Is the Windows machine and the Ubuntu server machine on the same LAN?

2. Are you using NAT or IP Masq?

3. Does netstat -pan | grep sshd show that sshd is listening on 0.0.0.0:22?

4. Provide the ouput of iptables --list

---

### Post by Fraaik on 2010-09-11
Thank you for your quick reply, thingy!

(Sorry, it seems to be the same problem, as               waloshin discribed in his thread).

To your questions:

> 1. Is the Windows machine and the Ubuntu server machine on the same LAN?yes, all my servers and clients are in the same LAN. I tried to connect from an other server in the LAN via ssh too: same result.

> 2. Are you using NAT or IP Masq?I think its NAT (I do not really know, its the default from installation. How can I check this?)

> 3. Does netstat -pan | grep sshd show that sshd is listening on 0.0.0.0:22?I'm sorry I can check this on monday in the office only.

> 4. Provide the ouput of iptables --list     See above...

Thanks again

---

### Post by thingy on 2010-09-11
> I think its NAT (I do not really know, its the default from installation. How can I check this?)

You can ignore the query about NAT.


5. Does the Ubuntu server have more than one network card?

6. If possible, provide the output of ifconfig -a from the Ubuntu server, and ipconfig /all on the Windows server, so that we understand a little more about the networking.

7. Other things to check is to see if the /etc/hosts.allow & /etc/hosts.deny files are allowing/denying connections. E.g. check for the following:

In /etc/hosts.deny:
> 
sshd: ALL


and maybe try adding a line at the end of the /etc/hosts.allow file such as:

> 
sshd: x.x.x.x/255.255.255.0


* Replace the x.x.x.x with your Windows server's IP and adjust the netmask to suit your network.

8. Did you install any software or make any configuration changes that:

   - protects SSH services(e.g. DenyHosts)
   - sets up VPNs/wireless networks etc
   - adjusts routing tables/firewall rules or basically does any simple to complicated network changes?

---

### Post by Fraaik on 2010-09-12
Hello thingy, hello all!

Here are some more infos, that your are requested.

> 5. Does the Ubuntu server have more than one network card?Yes, see ifconfig below. But only eth0 is connected (yet).

> 6. If possible, provide the output of ifconfig -a from the Ubuntu  server, and ipconfig /all on the Windows server, so that we understand a  little more about the networking.Here it is:
```

eth0      Link encap:Ethernet  HWaddr 84:2b:2b:4b:47:46  
          inet addr:192.168.0.40  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::862b:2bff:fe4b:4746/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:45 errors:0 dropped:0 overruns:0 frame:0
          TX packets:70 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:5211 (5.2 KB)  TX bytes:7254 (7.2 KB)
          Interrupt:16 Memory:da000000-da012800 

eth1      Link encap:Ethernet  HWaddr 84:2b:2b:4b:47:47  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:17 Memory:dc000000-dc012800 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:8 errors:0 dropped:0 overruns:0 frame:0
          TX packets:8 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:480 (480.0 B)  TX bytes:480 (480.0 B)


```(the windows machine is only a xp pro client).

> 7. Other things to check is to see if the /etc/hosts.allow & /etc/hosts.deny files are allowing/denying connections. They are empty (there are only the default comments).
Trying a "sshd: 192.168.0.x/255.255.255.0" where "x" is the ip of my xp-client
has the following fun effect:

Only one time the connection was valid and I can provide my username an pw.
But login canceled with this message:

```

--------------------------- 
PuTTY Fatal Error 
--------------------------- 
Network error: Software caused connection abort 

```Afterwards the old problem: "connection denied" - on every new trial to connect.

> Does netstat -pan | grep sshd show that sshd is listening on 0.0.0.0:22?                      There is:
```

tcp        0      0 0.0.0.0:22              0.0.0.0:*               LISTEN      994/sshd        
tcp6       0      0 :::22                   :::*                    LISTEN      994/sshd        

```And

>                               4. Provide the ouput of iptables --list                      ```

Chain INPUT (policy DROP)
target     prot opt source               destination         
ufw-before-logging-input  all  --  anywhere             anywhere            
ufw-before-input  all  --  anywhere             anywhere            
ufw-after-input  all  --  anywhere             anywhere            
ufw-after-logging-input  all  --  anywhere             anywhere            
ufw-reject-input  all  --  anywhere             anywhere            
ufw-track-input  all  --  anywhere             anywhere            

Chain FORWARD (policy DROP)
target     prot opt source               destination         
ufw-before-logging-forward  all  --  anywhere             anywhere            
ufw-before-forward  all  --  anywhere             anywhere            
ufw-after-forward  all  --  anywhere             anywhere            
ufw-after-logging-forward  all  --  anywhere             anywhere            
ufw-reject-forward  all  --  anywhere             anywhere            

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination         
ufw-before-logging-output  all  --  anywhere             anywhere            
ufw-before-output  all  --  anywhere             anywhere            
ufw-after-output  all  --  anywhere             anywhere            
ufw-after-logging-output  all  --  anywhere             anywhere            
ufw-reject-output  all  --  anywhere             anywhere            
ufw-track-output  all  --  anywhere             anywhere            

Chain ufw-after-forward (1 references)
target     prot opt source               destination         

Chain ufw-after-input (1 references)
target     prot opt source               destination         
ufw-skip-to-policy-input  udp  --  anywhere             anywhere            udp dpt:netbios-ns 
ufw-skip-to-policy-input  udp  --  anywhere             anywhere            udp dpt:netbios-dgm 
ufw-skip-to-policy-input  tcp  --  anywhere             anywhere            tcp dpt:netbios-ssn 
ufw-skip-to-policy-input  tcp  --  anywhere             anywhere            tcp dpt:microsoft-ds 
ufw-skip-to-policy-input  udp  --  anywhere             anywhere            udp dpt:bootps 
ufw-skip-to-policy-input  udp  --  anywhere             anywhere            udp dpt:bootpc 
ufw-skip-to-policy-input  all  --  anywhere             anywhere            ADDRTYPE match dst-type BROADCAST 

Chain ufw-after-logging-forward (1 references)
target     prot opt source               destination         
LOG        all  --  anywhere             anywhere            limit: avg 3/min burst 10 LOG level warning prefix `[UFW BLOCK] ' 

Chain ufw-after-logging-input (1 references)
target     prot opt source               destination         
LOG        all  --  anywhere             anywhere            limit: avg 3/min burst 10 LOG level warning prefix `[UFW BLOCK] ' 

Chain ufw-after-logging-output (1 references)
target     prot opt source               destination         

Chain ufw-after-output (1 references)
target     prot opt source               destination         

Chain ufw-before-forward (1 references)
target     prot opt source               destination         
ufw-user-forward  all  --  anywhere             anywhere            

Chain ufw-before-input (1 references)
target     prot opt source               destination         
ACCEPT     all  --  anywhere             anywhere            
ACCEPT     all  --  anywhere             anywhere            state RELATED,ESTABLISHED 
ufw-logging-deny  all  --  anywhere             anywhere            state INVALID 
DROP       all  --  anywhere             anywhere            state INVALID 
ACCEPT     icmp --  anywhere             anywhere            icmp destination-unreachable 
ACCEPT     icmp --  anywhere             anywhere            icmp source-quench 
ACCEPT     icmp --  anywhere             anywhere            icmp time-exceeded 
ACCEPT     icmp --  anywhere             anywhere            icmp parameter-problem 
ACCEPT     icmp --  anywhere             anywhere            icmp echo-request 
ACCEPT     udp  --  anywhere             anywhere            udp spt:bootps dpt:bootpc 
ufw-not-local  all  --  anywhere             anywhere            
ACCEPT     all  --  224.0.0.0/4          anywhere            
ACCEPT     all  --  anywhere             224.0.0.0/4         
ufw-user-input  all  --  anywhere             anywhere            

Chain ufw-before-logging-forward (1 references)
target     prot opt source               destination         

Chain ufw-before-logging-input (1 references)
target     prot opt source               destination         

Chain ufw-before-logging-output (1 references)
target     prot opt source               destination         

Chain ufw-before-output (1 references)
target     prot opt source               destination         
ACCEPT     all  --  anywhere             anywhere            
ACCEPT     all  --  anywhere             anywhere            state RELATED,ESTABLISHED 
ufw-user-output  all  --  anywhere             anywhere            

Chain ufw-logging-allow (0 references)
target     prot opt source               destination         
LOG        all  --  anywhere             anywhere            limit: avg 3/min burst 10 LOG level warning prefix `[UFW ALLOW] ' 

Chain ufw-logging-deny (2 references)
target     prot opt source               destination         
RETURN     all  --  anywhere             anywhere            state INVALID limit: avg 3/min burst 10 
LOG        all  --  anywhere             anywhere            limit: avg 3/min burst 10 LOG level warning prefix `[UFW BLOCK] ' 

Chain ufw-not-local (1 references)
target     prot opt source               destination         
RETURN     all  --  anywhere             anywhere            ADDRTYPE match dst-type LOCAL 
RETURN     all  --  anywhere             anywhere            ADDRTYPE match dst-type MULTICAST 
RETURN     all  --  anywhere             anywhere            ADDRTYPE match dst-type BROADCAST 
ufw-logging-deny  all  --  anywhere             anywhere            limit: avg 3/min burst 10 
DROP       all  --  anywhere             anywhere            

Chain ufw-reject-forward (1 references)
target     prot opt source               destination         

Chain ufw-reject-input (1 references)
target     prot opt source               destination         

Chain ufw-reject-output (1 references)
target     prot opt source               destination         

Chain ufw-skip-to-policy-forward (0 references)
target     prot opt source               destination         
DROP       all  --  anywhere             anywhere            

Chain ufw-skip-to-policy-input (7 references)
target     prot opt source               destination         
DROP       all  --  anywhere             anywhere            

Chain ufw-skip-to-policy-output (0 references)
target     prot opt source               destination         
ACCEPT     all  --  anywhere             anywhere            

Chain ufw-track-input (1 references)
target     prot opt source               destination         

Chain ufw-track-output (1 references)
target     prot opt source               destination         
ACCEPT     tcp  --  anywhere             anywhere            state NEW 
ACCEPT     udp  --  anywhere             anywhere            state NEW 

Chain ufw-user-forward (1 references)
target     prot opt source               destination         

Chain ufw-user-input (1 references)
target     prot opt source               destination         
ACCEPT     tcp  --  anywhere             anywhere            tcp dpt:ssh 
ACCEPT     udp  --  anywhere             anywhere            udp dpt:ssh 
ACCEPT     udp  --  anywhere             anywhere            multiport dports netbios-ns,netbios-dgm /* 'dapp_Samba' */ 
ACCEPT     tcp  --  anywhere             anywhere            multiport dports netbios-ssn,microsoft-ds /* 'dapp_Samba' */ 

Chain ufw-user-limit (0 references)
target     prot opt source               destination         
LOG        all  --  anywhere             anywhere            limit: avg 3/min burst 5 LOG level warning prefix `[UFW LIMIT BLOCK] ' 
REJECT     all  --  anywhere             anywhere            reject-with icmp-port-unreachable 

Chain ufw-user-limit-accept (0 references)
target     prot opt source               destination         
ACCEPT     all  --  anywhere             anywhere            

Chain ufw-user-logging-forward (0 references)
target     prot opt source               destination         

Chain ufw-user-logging-input (0 references)
target     prot opt source               destination         

Chain ufw-user-logging-output (0 references)
target     prot opt source               destination         

Chain ufw-user-output (1 references)
target     prot opt source               destination         

```(Don't be confused about the "samba" entries. One time I give up the ssh problem an installed "samba". But there a too strange connect defficulties - but this later one. One step after the other...)

Hope there are sone usable informations.

Thank you again...

Cheers, Fraaik

---

### Post by thingy on 2010-09-12
You need to disable the firewall in Ubuntu to rule it out as a source of the problem.

Enter:

> sudo ufw disable;
sudo /etc/init.d/iptables stop;

Another thing you can try is to disable IPV6. [Link]("http://www.webupd8.org/2010/05/how-to-disable-ipv6-in-ubuntu-1004.html")

---

### Post by Fraaik on 2010-09-13
Hello thingy,

IPV6 is now disabled and ufw too (ufw status -> Status: inactive).

> sudo /etc/init.d/iptables stopdin't work (in this setup it is located in "sbin"), but giving "sudo /sbin/iptables stop" results in "Bad argument 'stop'".

Now I had one (and only one) time to logon. But making a simle "ls" the same effect as yesterday happens:

Network error: Software caused connection abort

and after that, every retry: connection refused.... :(

[edit]
Addendum:

I've just tried to connect in the other dircection into WAN by typing

```

ssh -l <username> x.x.x.x

```

This gives after ssh authentification warning and adding the ip to the "known hosts table" a
"Read from socket failed: Connection reset by peer".

Cross-checking this from our Debian server: connection works as expected...

---

### Post by Fraaik on 2010-09-18
Sorry, I still stuck in this problem.

I've tested around but without any result.

But I have another information.
I told at  my last posting, that I can connect one time to the server, an see the login message as follows:

```


Linux nephele-2 2.6.32-24-generic-pae #39-Ubuntu SMP Wed Jul 28 07:39:26 UTC 2010 i686 GNU/Linux
Ubuntu 10.04.1 LTS

Welcome to Ubuntu!
 * Documentation:  https://help.ubuntu.com/

  System information as of Sat Sep 18 17:49:00 CEST 2010

  System load:    0.09              Processes:           106
  Usage of /home: 0.2% of 85.89GB   Users logged in:     0
  Memory usage:   1%                IP address for lo:   127.0.0.1
  Swap usage:     0%                IP address for eth0: 192.168.0.40

  Graph this data and manage this system at https://landscape.canonical.com/

Last login: ......

```But when I try to do a "ls" or something else I get the message "Network error: Software caused connection abort".

If a have a look at the server console and I do

```

netstat -pan | grep sshd

```I get there:

```

tcp        0      0 0.0.0.0:22              0.0.0.0:*               LISTEN      858/sshd        
tcp        0      0 192.168.0.40:22         192.168.0.7:1182        [COLOR=Red]ESTABLISHED[/COLOR] 1046/sshd: userX [p
tcp6       0      0 :::22                   :::*                    LISTEN      858/sshd        
unix  3      [ ]         STREAM     CONNECTED     4949     1046/sshd: userX [p 
unix  2      [ ]         DGRAM                    4704     1046/sshd: userX [p 


```**It seems as the server/sshd has a valid connection there!?**

Have anyone an idea what this means?
And, of course, how can I solve my problem?

---

### Post by Fraaik on 2010-09-20
Hi guys,

again and again - I know...

I've been testing around a whole week now and got no sulution for this problem.

But it maybe is a hardware, firmware issue: all services I have installed now (samba/svn) have the same problem. All connections are dinied/refused within our LAN.

Outgoing connections can be established but getting sooner or later an "i/o error" -> "broken pipe".

If I do a "apt-get upgrade" its "stalled" often. I thinks that is a further hint for my assumption.

One question abot that: how can I check if the hardware/diver works correct?

Thank you!

---

### Post by obstech on 2010-09-20
I am having the same problem, also with a Dell R310. Eyes are glued to this thread.

- Andy

---

### Post by Fraaik on 2010-09-22
Hello,

the problem seems to be solved, but its strange enough.
Starting point was that I read elsewhere "ubuntu is sometime confused if there are two nics in the system".
First I've disconnected eth0 and connected eth1. Result: the machine was unreachable and there was now way out of the machine.

Its ridiculous but the problem was, that there was no entry for eth1 in /etc/networking/interfaces.
After editing this file (eth1 have an other IP than eth0) and doing

```

sudo /etc/init.d/networking restart

```all my problems disappears:

ssh login works, samba shares are visible in LAN, svn works!

But strange is it at all: after booting the system is not connected to the LAN.
Doing an ping from the machine to an other workstation results in 100% loss.
namp from my personal win xp station says:

```

nmap -p22 192.168.0.40

Nmap scan report for 192.168.0.40
Host is up (0.94s latency).
PORT   STATE  SERVICE
22/tcp closed ssh

nmap -p22 192.168.0.41
Note: Host seems down. If it is really up, but blocking our ping probes, try -PN
Nmap done: 1 IP address (0 hosts up) scanned in 3.09 seconds

```(eth0: 192.168.0.40 connected, eth1: 192.168.0.41)

After

```

sudo /etc/init.d/networking restart

```nmap says:
```

nmap -p22 192.168.0.40

Nmap scan report for 192.168.0.40
Host is up (0.83s latency).
PORT   STATE SERVICE
22/tcp open  ssh

Nmap done: 1 IP address (1 host up) scanned in 1.02 seconds

nmap -p22 192.168.0.41

Nmap scan report for 192.168.0.41
Host is up (1.1s latency).
PORT   STATE SERVICE
22/tcp open  ssh

Nmap done: 1 IP address (1 host up) scanned in 3.59 seconds

```**What's that? eth1 IS NOT CONNECTED???**

ping works too on both addresses!
What is going on here?

Ok, I'm happy this server work now as desired.

But it would be fine, if

- network is up after (re)boot
- eth0 has one IP and eth1 has one IP...

Any ideas?

---

