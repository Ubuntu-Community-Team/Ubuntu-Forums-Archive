---
title: "monitoring my network.."
date: 2006-03-10
forum: Server Platforms
---

### Post by warbux on 2006-03-10
i've read some how-to's on monitoring network security, but im a little bit flustered.  i just installed ethereal..but have no idea how to read the logs..also, i run ssh server on my laptop for work purposes..where in the system would i check to see if someone has been dictionary attacking me etc? thanks in advance.

---

### Post by amohanty on 2006-03-11
First, use nmap to make sure that you dont have more ports open than you absolutely need to using:
assuming you have unverse enabled
> 
sudo apt-get install nmap
sudo nmap -vv -sS -p 1-65535 <your ip address>

If you see any daemons/services that you dont need with open ports, shut them down using something line bootup manager (bum) or sysv-rc-conf (available in unverse).

Then you can use something like snort in conjunction with something like tripwire and firestarter on top will keep you in reasonably good shape.

You can use the lastlog command to view the last logins. Several useful utiltities to analyze your log files and secure your box are available at:
[http://cs-www.ncsl.nist.gov/tools/tools.htm](http://cs-www.ncsl.nist.gov/tools/tools.htm)

Finally look at /etc/login.def or do a man login.def

HTH
AM

---

### Post by warbux on 2006-03-11
thanks for the response..will it matter if i am behind a router? im pretty sure the router has a built in firewall, because i had to do some port mapping to get ssh and bit torrent working properly.

\ when i tried to run  snort i got the following error.
```
No snort instance found to be stopped!
Starting Network Intrusion Detection System: snort(eth0)No /etc/snort/snort.eth0.conf, defaulting to snort.conf
...failed (check /var/log/daemon.log).
invoke-rc.d: initscript snort, action "start" failed.

```

checked the log and got this..
> Mar 11 03:55:42 localhost snort: FATAL ERROR: OpenPcap() device eth0 open:  ^Ibind: Network is down 

*sigh* ps im down in San Jose..nice to see some users from the bay area :D

---

### Post by amohanty on 2006-03-12
> OpenPcap() device eth0 open: ^Ibind: Network is down

This would imply that your primary network connection is not calle eth0.
Can you post the output of ifconfig

AM

---

### Post by vayu on 2006-03-14
[QUOTE=amohanty]First, use nmap to make sure that you dont have more ports open [/QUOTE]


Hey thanks that was something I've always wanted to know how to do.

I ran it on the local address of my laptop, then I ran it on my router (local address), then I ran it on the IP assigned by my dsl provider as shown by my router.

The wan address and the router local address only showed port 80 open.

My machine (only one of several on the network) showed several open ports.
I assume that based on the above, it doesn't matter when I'm on this network.

Since that machine is my laptop, I'm wondering what happens when I go out to a coffee shop with it?  Are these ports then vulnerable?
What do I have to do? I know nothing about security.  Is there a way that I can easily close these ports when I go out and then turn them back on again when I get back to my network?

That machine runs Apache, MySQL, Samba and SSH.
It listed these ports as open:
22/tcp      open   ssh
80/tcp      open   http
139/tcp    open   netbios-ssn
445/tcp    open   microsoft-ds
7741/tcp  open    unknown

For some reason I thought MySQL ran on something like 3306, why isn't it there?

I guess the netbios and microsoft are from Samba, does that seem right?

What could 7741 be and/or how do I trace it to an application?

---

### Post by amohanty on 2006-03-14
> 22/tcp open ssh
80/tcp open http
139/tcp open netbios-ssn
445/tcp open microsoft-ds
7741/tcp open unknown

to stop any of those services on the fly:
> sudo /etc/init.d/<service name> stop

To start them back up:
> sudo /etc/init.d/<service name> start

I beleive the service name for ssh is ssh or sshd (I dont run ssh or httpd on ubuntu so its not installed), the one for apache mght be called either httpd or apache2 (you also have the option of using apachectl) and for samba its samba.

To see what 7741 is used for look up /etc/services or the files in /etc/xinetd.d
To see what port mysql is using look up its conf file in /etc or shut down the service using the method described above and run nmap once again.

> Since that machine is my laptop, I'm wondering what happens when I go out to a coffee shop with it? Are these ports then vulnerable?

Well in theory you are only as vulnerable as your last patch. In general linux vulnerabilities (critical ones at least) get fixed very quickly and then the little red update icon should show up. If you are going to use the laptop on a public network, I would suggest just closing all the ports.

HTH
AM

---

### Post by warbux on 2006-03-15
here is my ifconfig guys, hope this helps.

```
eth1      Link encap:Ethernet  HWaddr 00:13:CE:23:A7:2D
          inet addr:10.0.1.2  Bcast:255.255.255.255  Mask:255.255.255.0
          inet6 addr: fe80::213:ceff:fe23:a72d/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:31768 errors:12 dropped:12 overruns:0 frame:0
          TX packets:26071 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:175764278 (167.6 MiB)  TX bytes:2244702309 (2.0 GiB)
          Interrupt:17 Base address:0xe000 Memory:dfdfd000-dfdfdfff

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:939492 errors:0 dropped:0 overruns:0 frame:0
          TX packets:939492 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:73908421 (70.4 MiB)  TX bytes:73908421 (70.4 MiB)

```

---

### Post by amohanty on 2006-03-16
So you are not using eth0 but eth1. YOu have to change the default interface in snort. The manual is here:
[http://www.snort.org/docs/snort_htmanuals/htmanual_2.4/rc1/](http://www.snort.org/docs/snort_htmanuals/htmanual_2.4/rc1/)

Snort is quite an advanced tool and can be quite daunting to configure. I would suggest starting out with something simple like tripwire and then moving up the ladder.

One starting point can be found here:
[http://netsecurity.about.com/cs/hackertools/a/aa030504.htm](http://netsecurity.about.com/cs/hackertools/a/aa030504.htm)

HTH
AM

---

