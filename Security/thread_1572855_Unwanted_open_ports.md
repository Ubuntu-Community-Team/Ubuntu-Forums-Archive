---
title: "Unwanted open ports"
date: 2010-09-11
forum: Security
---

### Post by Hadeda on 2010-09-11
A portscan reveals that port 39878 is 'open', service: 'unknown.
I deny service for this port in Firestarter FW 'policy'
Firestarter does not show any active connection.

I am not running any apps, so how can I close this port?
What does this mean? 
Many thanks.

---

### Post by CharlesA on 2010-09-11
See what is listening on that port by running:

```
netstat -ln
```

Also, firestarter is no longer in development, you should use ufw or gufw to configure yer firewall. :)

---

### Post by Hadeda on 2010-09-11
Great help,  CharlesA :D

I still have to learn what all the info means, but one thing I did see: 

unix  2      [ ACC ]     STREAM     LISTENING     4502     /var/run/avahi-daemon/socket

I checked out Avahi:
"Avahi is a system which facilitates service discovery on a local network via the mDNS/DNS-SD protocol suite. This enables you to plug your laptop or computer into a network and instantly be able to **view other people who you can chat with, find printers to print to or find files being shared**."

I don't want to share any of this...

Is this something one should be concerned about?
If yes, what is the remedy?
Many thanks

---

### Post by CharlesA on 2010-09-11
Then stop the service:

```
sudo service avahi-daemon stop
```

There is no way it would harm your machine to have it running. It just makes networking easier.

---

### Post by bodhi.zazen on 2010-09-12
See also :

[https://wiki.ubuntu.com/ZeroConfPolicySpec](https://wiki.ubuntu.com/ZeroConfPolicySpec)

[SecurityTeam/Policies - Ubuntu Wiki]("https://wiki.ubuntu.com/SecurityTeam/Policies") 

[SecurityConsiderations – Avahi]("http://avahi.org/wiki/SecurityConsiderations") 

[SecurityTeam/FAQ - Ubuntu Wiki]("https://wiki.ubuntu.com/SecurityTeam/FAQ#Sudo") 

With that said, I do not use avahi, and always disable it (usually I do a minimal install and do not install it at all).

---

### Post by HermanAB on 2010-09-12
Howdy,

Avahi is the piece of junk that gives you a 169.x.y.z addresses on Windows machines when the network is otherwise down - it is a kind of broken DHCP server.  

I have never used it for anything and I don't even know anybody that ever used it for anything, so I always disable it.  Goodness knows why each Linux distribution insists on installing it.

---

### Post by BkkBonanza on 2010-09-12
I always wondered why I left it there (avahi).
Now you've given me the courage to just nuke it.

@Hadeda,
The only part of that output you need to worry about is theline with your questionable port on it.

Try the same again but,

netstat -ln | grep 39878

Also, do you have a router and are you scanning from the internet or within your LAN. It's entirely possible that port isn't even on you system. If it's on the router then you would need to look there for what is using it.

---

### Post by noway2 on 2010-09-12
After reading the security links by Bodhi, I agree with your position on getting rid of it.  Not that it is anything inherently wrong with it, rather it is something that I would chose not to have on my system.

Unfortunately, it looks like much software is dependent on its presence.  For example see the following: [https://answers.launchpad.net/ubuntu/+question/29816](https://answers.launchpad.net/ubuntu/+question/29816).  I noticed that if I attempted to remove the AVAHI related applications (see attached screen shot) that it would remove many associated packages that I do want on my system, such as the Gnome Development Libraries.

So, this brings up the question of what is the best way to disable or remove this feature?  Turn the daemon off as suggested in the link above or remove the daemon-process only, which only wants to remove the avahi-utilities with it?  Correction it also gets rid of: libnss-mdns, padevchooser, and telepathy-salut.

---

### Post by Bachstelze on 2010-09-12
Hmm, guys?

> **Hadeda said:**
> 
unix  2      [ ACC ]     STREAM     LISTENING     4502     /var/run/avahi-daemon/socket

This is a UNIX socket, not a TCP port. It is local only and not opened to any other machine. To find out which process listens on TCP port 39878:

```
sudo fuser -n tcp 39878
```

It will give the PID of the process, look it up with ps.

---

### Post by wacky_sung on 2010-09-12
Avahi actually slow down my system performance.I simply disable it.

Edit the file
```
gedit /etc/avahi/avahi-daemon.conf
```

Change
```
use-ipv4=yes
```

to
```
use-ipv4=no
```

Then i restart run
```
/etc/init.d/avahi-daemon restart
```

Verify avahi is stop/disable.
```
service avahi-daemon status
```

it show
```
avahi-daemon stop/waiting
```

or 

Using netstat
```
netstat -tulanp
```

it will not show any listening port of avahi.

---

### Post by CharlesA on 2010-09-12
Thanks for the info on how to disable it. :)

---

### Post by The Cog on 2010-09-12
I know that avahi slows every incoming connection by several seconds, rendering the computer pretty useless as a web of file server. Even just ssh-ing to it occasionally is irritatingly slow. It took me a while to work out that avahi was the culprit. I disable it by editing /etc/init/avahi-daemon.conf and commenting out the lines:

#start on (filesystem
#         and started dbus)

---

### Post by Hadeda on 2010-09-12
Thanks for all of the great input! =D>

The plot thickens!

Before answering all of your excellent questions, some of your responses prompted us to do some research:

We ran trace route (in networktools) on several addresses, our domains included.

Results

1) All 6 initial hops are always identical. What is troubling us (lay people) is the 4th hop, labeled hop #2 namely   10.195.224.1   We are told it is/ could be AN**OTHER router address, certainly not ours.**

2) There is an **IP discrepancy** between our hosted IP address for the domain name (as per whois) and the address traceroute 'ends up' (hop 17). The address resolves to  MarkMonitor (wcg.net), who is NOT our registrar of our domain name.

Immediate questions:

1) Is it 'normal' to have an IP traceroute discrepancy, as explained above?

2) We are running on cable in a less than amiable and "bank-owned" neighborhood. This, in conjunction with Avahi and freedesktop.org (there seems to be a link), is the permanent 10.195.224.1 router address something 'knowledge workers' or Ubuntu users in general, need to be concerned about? :confused:

---

### Post by bodhi.zazen on 2010-09-12
> **noway2 said:**
> After reading the security links by Bodhi, I agree with your position on getting rid of it.  Not that it is anything inherently wrong with it, rather it is something that I would chose not to have on my system.

Unfortunately, it looks like much software is dependent on its presence.  For example see the following: [https://answers.launchpad.net/ubuntu/+question/29816](https://answers.launchpad.net/ubuntu/+question/29816).  I noticed that if I attempted to remove the AVAHI related applications (see attached screen shot) that it would remove many associated packages that I do want on my system, such as the Gnome Development Libraries.

So, this brings up the question of what is the best way to disable or remove this feature?  Turn the daemon off as suggested in the link above or remove the daemon-process only, which only wants to remove the avahi-utilities with it?  Correction it also gets rid of: libnss-mdns, padevchooser, and telepathy-salut.

That is one of the "problems" with Ubuntu - To make things "easier" often "excessive" packages are listed as dependencies.

IMO it is easier to start with a minimal install and build up, hopefully not pulling avahi in as a dependency. Debian has less dependencies sometimes.

The other option is to disable avahi, bu modifying the init script via one of the methods above.

---

### Post by rnerwein on 2010-09-12
> **Hadeda said:**
> A portscan reveals that port 39878 is 'open', service: 'unknown.
I deny service for this port in Firestarter FW 'policy'
Firestarter does not show any active connection.

I am not running any apps, so how can I close this port?
What does this mean? 
Many thanks.
hi
just a hint. --> firewall
here in germany all the connentions are be able to configure. but the most people never read the
sorry the " f**** manual". i think you can block every port on it take the roots, what i mean is block on where it comes from  (it is possible on my system) - if you know what you are doing.
for - i have 6 boxes with 6 operating systems and the only place to handle this is --> where it comes in.
ciao

---

### Post by CharlesA on 2010-09-12
> **Hadeda said:**
> 
Results

1) All 6 initial hops are always identical. What is troubling us (lay people) is the 4th hop, labeled hop #2 namely   10.195.224.1   We are told it is/ could be AN**OTHER router address, certainly not ours.**

2) There is an **IP discrepancy** between our hosted IP address for the domain name (as per whois) and the address traceroute 'ends up' (hop 17). The address resolves to  MarkMonitor (wcg.net), who is NOT our registrar of our domain name.

Immediate questions:

1) Is it 'normal' to have an IP traceroute discrepancy, as explained above?

2) We are running on cable in a less than amiable and "bank-owned" neighborhood. This, in conjunction with Avahi and freedesktop.org (there seems to be a link), is the permanent 10.195.224.1 router address something 'knowledge workers' or Ubuntu users in general, need to be concerned about? :confused:

10.x.x.x is a private IP address, so it's probably another router at your ISP. That's not unheard of (happens to me).

As for the the last hop. That's just the last router it goes thru before the destination. 

In any case, it's normal. :)

---

### Post by Hadeda on 2010-09-12
Bachstelze
got the PID (I guess that it stands for process ID)
As a newcomer to Ubuntu, what is ps?  :oops:
Thanks

---

### Post by Hadeda on 2010-09-12
Response to your suggestions/questions:

1) CharlesA
sudo service avahi-deamon stop returns:  
"avahi-deamon: unrecognized service"



2) BkkBonaza:
  a)  netstat -ln | grep 39878   returns:

tcp        0      0 0.0.0.0:39878           0.0.0.0:*     LISTEN     
udp        0      0 0.0.0.0:39878           0.0.0.0:*   

I don't know (yet) what this means...

  b)  See above post re: router   :-)


4) wacky_sung:
 gedit /etc/avahi/avahi-daemon.conf
the file pops up but it doesn't let me edit it   :-(

5) The Cog
 As for 4 above. I can open the file, but can't edit it

6) rnerwein
As beginners, yes, we don't know what we are doing. :-)

However, we are very interested in getting the original German source of Berthold's quote "What is the robbing of a bank compared to the FOUNDING of a bank?" Thanks!

7) CharlesA
 Thanks re: mysterious router. I/we (family) have to learn a bit more about how/why this is o.k.

Thanks for all of your efforts; looking forward to a reply to the outstanding issues:D.

---

### Post by CharlesA on 2010-09-12
It's ```
sudo service avahi-daemon stop
```

Darn those vowels!

Use need to use gksu, since it's a graphical app and the file is owned by root.

```
gksu gedit /etc/avahi/avahi-daemon.conf
```

---

### Post by The Cog on 2010-09-12
> **Hadeda said:**
> Bachstelze
got the PID (I guess that it stands for process ID)
As a newcomer to Ubuntu, what is ps?  :oops:
Thanks

from the command **man ps** : ps - report a snapshot of the current processes. 

**man** is the command to view the manual on a command. Use "q" to quit the manual.

---

