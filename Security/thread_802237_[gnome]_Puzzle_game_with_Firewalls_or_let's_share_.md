---
title: "[gnome] Puzzle game with Firewalls or let's share knowledge in one place"
date: 2008-05-21
forum: Security
---

### Post by RRFarFar on 2008-05-21
Hie to everybody,

This not the first time I am posting something in this forum. I am concerned about Ubuntu security - IPTABLES (its GUI) in particular. 
I have recently started using Linux on daily basis, so I am not Linux guru or somebody of that kind.
I keep reading those posts saying that Ubuntu is secure and by default all ports are closed. Also I do know that iptables is the default network filtering solution for Ubuntu, although Ubuntu Hardy comes with UFW (uncomplicated firewall), the latter seems to be just a tool to write rules to iptables (please correct me if I am wrong). Anyway I wanted to use Firestarter from the beginning since it was for gnome. Let's not talk about Guarddog here since it is KDE native. Eventhough Firestarter is not being developed by its creator now, I prefer it to UFW, since for instance using UFW you cannot create a rule to manipulate a port range. It is simple impossible)))). So if I want to allow Ekiga with port range from udp 5000-5100; you have to do it separately with every bloody number.
As a former WIN user in major cases I prefer GUI, so Firestarter was the only choice for gnome.
After installing Firestarter from Synaptic I had the following issues:

1. [SOLVED] Firestarter runs from startup but GUI frontend does not, also it asks for password before you can acced it. I wanted to have GUI frontend all the time in tray right from the startup point. So I followed this (see [http://ubuntuforums.org/showthread.php?t=449319&page=2):](http://ubuntuforums.org/showthread.php?t=449319&page=2):)
> 
How to make Firestarter start automatically at startup
* System -> Preferences -> Sessions -> Startup Programs -> Add

sudo firestarter --start-hidden

* Press "OK"

How to have Firestarter start without the root password

Note: THIS IS NOT SECURE !!

In Terminal:
export EDITOR=gedit
sudo visudo

• navigate to the # Defaults section
• and place a # in front of this line 'Defaults !lecture,tty_tickets,!fqdn'
• so it looks like this:

#Defaults !lecture,tty_tickets,!fqdn

• then add this line immediately after it:

Defaults !lecture,tty_tickets,!fqdn,env_reset,env_keep+="DI SPLAY HOME XAUTHORIZATION"

• At the very bottom of the file add this line:

USERNAME ALL= NOPASSWD: /usr/sbin/firestarter

• Save and close the file

• This may cause problems with administrative applets that won't open due to the changes made to the visudo file
including Synaptic and the Updater, which even after entering your password may no longer open. To fix this:

• For the next two lines, USERNAME = your username

~$ sudo ln -fs /home/USERNAME/.Xauthority /root/.Xauthority
~$ sudo chown USERNAME.root /home/USERNAME/.Xauthority

• Restart your computer


Maybe it is not secure, but I do not pay attention to this, since I want convenience and not total security.
=======================================
2. [SOLVED or maybe NOT??] Every time I booted my laptop, as every other Ubuntu user I have seen a line "preparing boot files", so during this stage of starting up Firestarter gave some kind of an error (read about that here [http://ubuntuforums.org/showthread.php?t=542756](http://ubuntuforums.org/showthread.php?t=542756)). So I followed this small guide in order to remove an error before x even started. There is no explicit error, but there are lines indicatng that it fails to launch.
=======================================
3. [NOT SOLVED] Despite my effort to remove errors, Firestarter always starts before any network interface is up, therefore I wants to shutdown. I do not know how to make it start later. Any ideas???
=======================================
4. [NOT SOLVED] Another strange thing was that after installing firestarter it did not change anything. I suspect that it is not working right or maybe not working at all. I have it my tray, but applications can access Internet as it was before. You know, on windows when installa firewall it changes everything. I am not asking for autmatic popup messages, but there is no need even to open port manually. All aplication can access Internet, all I can see is just some kind of activity inside Firestarter's GUI. Is it normal or should Firestarter close all ports after installation????
=======================================
5. [NOT SOLVED] By reading numerous posts I was unable to understand the difference between open port and when the port is listened by some kind of service or application. ???
=======================================
6. [NOT SOLVED] Checking iptables state with "sudo iptables -L" gives me this

> 
Chain INPUT (policy DROP)
target     prot opt source               destination         
ACCEPT     tcp  --  myISPprovider       anywhere            tcp flags:!FIN,SYN,RST,ACK/SYN 
ACCEPT     udp  --  myISPprovider       anywhere            
ACCEPT     tcp  --  myISPprovider       anywhere            tcp flags:!FIN,SYN,RST,ACK/SYN 
ACCEPT     udp  --  myISPprovider       anywhere            
ACCEPT     all  --  anywhere             anywhere            
ACCEPT     icmp --  anywhere             anywhere            limit: avg 10/sec burst 5 
DROP       all  --  anywhere             255.255.255.255     
DROP       all  --  anywhere             192.168.1.255       
DROP       all  --  BASE-ADDRESS.MCAST.NET/8  anywhere            
DROP       all  --  anywhere             BASE-ADDRESS.MCAST.NET/8 
DROP       all  --  255.255.255.255      anywhere            
DROP       all  --  anywhere             0.0.0.0             
DROP       all  --  anywhere             anywhere            state INVALID 
LSI        all  -f  anywhere             anywhere            limit: avg 10/min burst 5 
INBOUND    all  --  anywhere             anywhere            
LOG_FILTER  all  --  anywhere             anywhere            
LOG        all  --  anywhere             anywhere            LOG level info prefix `Unknown Input' 

Chain FORWARD (policy DROP)
target     prot opt source               destination         
ACCEPT     icmp --  anywhere             anywhere            limit: avg 10/sec burst 5 
LOG_FILTER  all  --  anywhere             anywhere            
LOG        all  --  anywhere             anywhere            LOG level info prefix `Unknown Forward' 

Chain OUTPUT (policy DROP)
target     prot opt source               destination         
ACCEPT     tcp  --  192.168.1.102        myISPprovider      tcp dpt:domain 
ACCEPT     udp  --  192.168.1.102        myISPprovider      udp dpt:domain 
ACCEPT     tcp  --  192.168.1.102        myISPprovider      tcp dpt:domain 
ACCEPT     udp  --  192.168.1.102        myISPprovider      udp dpt:domain 
ACCEPT     all  --  anywhere             anywhere            
DROP       all  --  BASE-ADDRESS.MCAST.NET/8  anywhere            
DROP       all  --  anywhere             BASE-ADDRESS.MCAST.NET/8 
DROP       all  --  255.255.255.255      anywhere            
DROP       all  --  anywhere             0.0.0.0             
DROP       all  --  anywhere             anywhere            state INVALID 
OUTBOUND   all  --  anywhere             anywhere            
LOG_FILTER  all  --  anywhere             anywhere            
LOG        all  --  anywhere             anywhere            LOG level info prefix `Unknown Output' 

Chain INBOUND (1 references)
target     prot opt source               destination         
ACCEPT     tcp  --  anywhere             anywhere            state RELATED,ESTABLISHED 
ACCEPT     udp  --  anywhere             anywhere            state RELATED,ESTABLISHED 
LSI        all  --  anywhere             anywhere            

Chain LOG_FILTER (5 references)
target     prot opt source               destination         

Chain LSI (2 references)
target     prot opt source               destination         
LOG_FILTER  all  --  anywhere             anywhere            
LOG        tcp  --  anywhere             anywhere            tcp flags:FIN,SYN,RST,ACK/SYN limit: avg 1/sec burst 5 LOG level info prefix `Inbound ' 
DROP       tcp  --  anywhere             anywhere            tcp flags:FIN,SYN,RST,ACK/SYN 
LOG        tcp  --  anywhere             anywhere            tcp flags:FIN,SYN,RST,ACK/RST limit: avg 1/sec burst 5 LOG level info prefix `Inbound ' 
DROP       tcp  --  anywhere             anywhere            tcp flags:FIN,SYN,RST,ACK/RST 
LOG        icmp --  anywhere             anywhere            icmp echo-request limit: avg 1/sec burst 5 LOG level info prefix `Inbound ' 
DROP       icmp --  anywhere             anywhere            icmp echo-request 
LOG        all  --  anywhere             anywhere            limit: avg 5/sec burst 5 LOG level info prefix `Inbound ' 
DROP       all  --  anywhere             anywhere            

Chain LSO (0 references)
target     prot opt source               destination         
LOG_FILTER  all  --  anywhere             anywhere            
LOG        all  --  anywhere             anywhere            limit: avg 5/sec burst 5 LOG level info prefix `Outbound ' 
REJECT     all  --  anywhere             anywhere            reject-with icmp-port-unreachable 

Chain OUTBOUND (1 references)
target     prot opt source               destination         
ACCEPT     icmp --  anywhere             anywhere            
ACCEPT     tcp  --  anywhere             anywhere            state RELATED,ESTABLISHED 
ACCEPT     udp  --  anywhere             anywhere            state RELATED,ESTABLISHED 
ACCEPT     all  --  anywhere             anywhere   


As far as I understand everything is allowed. Right?????
===========================================================
7.[NOT SOLVED] How to create Firestarter rules and populate iptables with those rules???

Please write your story of using applications as we call them firewalls, and maybe we will find solution to many problem in one thread.
I think it is necessary to manage iptables, but since this things is alien for new user, let's try to use other applications like Firestarter

---

### Post by The Cog on 2008-05-21
4) Firestarter clearly **is** working because you can see a load of iptables rules. But the rules are allowing all outgoing connections at the moment. Chain OUTPUT calls chain OUTBOUND, the last entry of which says accept everything. Incoming connections are mostly dropped.

5) A confusing issue because "open port" has two different meanings:

a) On a server, an open port is one that has a service running that has opened the port and is listening for incoming connections. Frinstance, starting a web server will open port 80. If no application is listening, the OS port is closed. These are the only two possible states.

b) On a firewall (or nat router), or even in firewall rules on the server, opening a port means configuring the firewall to allow packets to/from that port. Of course the port may actually be closed even if connections are allowed by the firewall, in which case the user will get connection refused. Alternatively a firewall may choose to simply drop packets to/from that port (sometimes called "stealthed" because a caller sees no reply to his request). Another alternative is for the firewall to respond to packets for that port by sending a "port unreachable" message back. In this case the caller gets a "connection refused" indication, and would probably regard the port as closed.

In summary:
   SERVER:
      Open:     Application listening
      Closed:   Nobody listening (connection refused)
   FIREWALL:
      Open:    Allowed through
      Closed:  Dropped or refused before ever reaching the server

```

 FIREWALL   SERVER      RESULT
 ----------------------------
 ACCEPT     Open       Connected
 ACCEPT     Closed     Connection refused
 DROP         -        Timeout
 REJECT       -        Connection refused
```
  

6)
Outgoing connections allowed (OUTPUT->OUTBOUND). 
Incoming connections dropped (INPUT->INBOUND->LSI)

Things will make more sense if you use **iptables -vL** (or -nvL) because it then also lists any interface specification. Otherwise  this line:
**ACCEPT all -- anywhere anywhere**
halfway down INPUT makes the rest of the chain look unreachable. In fact, I guess this line only identifies packets to/from interface lo, meaning allow connections from myself. Blocking self-connections breaks lots of things - don't do it.


7)
Change the rules in the firestarter GUI. I'm sure the active iptables rules will change accordingly. 

Note that I don't think blocking outgoing connections is very useful. Like trying to fasten the windows to stop burglars getting back out. Others will likely disagree I suppose.

I only looked briefly at firestarter, and I think I prefer guarddog. But I currently use a script that issues iptables commands directly.

---

### Post by RRFarFar on 2008-05-21
Thanks for reply. I am sure it is hard to read that much, especially when most of it I guess is nonsense. Anyway, i will examine what you've said in couple of days time.

So far I have found the following useful info:

1. [http://www.hackerwatch.org/probe/](http://www.hackerwatch.org/probe/) - check you ports, there are several tests there. In my case everything was OK. I suspected that everything is opened in my system, but all test showed I am secure. I will research this question more.

2. [http://ubuntuforums.org/showthread.php?t=159661&highlight=howto+firewall](http://ubuntuforums.org/showthread.php?t=159661&highlight=howto+firewall) - good how to on using iptables. For instance the ideal thread which I am looking for would have a HOWTO ON FIRESTARTER WITH IPTABLES FOR HARDY

---

