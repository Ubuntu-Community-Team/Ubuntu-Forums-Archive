---
title: "[SOLVED] Closing ports."
date: 2008-10-27
forum: Security
---

### Post by Bruce M. on 2008-10-27
Hi Folks,

Normally Ubuntu has all ports "**Closed**" and that's OK for me, but recently something has changed all my ports to read "**Stealth**". See attached. Two weeks ago there were three stealthed and I started to have connection problems, now this and my connection problems are worse.

I've been through the "Closed vs Stealth" argument / opinions / discussion and don't want to get into that here. I simply want them **Closed**.

Any help out there on how to **Close** these ports again?

I have installed Firestarter to see if I can "Close" them and don't see anything in it's Preferences as to Open, Closed or Stealth settings.

Please help.

Chimo!
Bruce

---

### Post by hyper_ch on 2008-10-27
who made that graphic?

---

### Post by Bruce M. on 2008-10-27
> **hyper_ch said:**
> who made that graphic?

[https://www.grc.com/x/ne.dll?bh0bkyd2](https://www.grc.com/x/ne.dll?bh0bkyd2)

---

### Post by hyper_ch on 2008-10-27
are you behind a router?

---

### Post by Bruce M. on 2008-10-27
> **hyper_ch said:**
> are you behind a router?

No, no router here, CPU direct to Internet via Cable Modem.

---

### Post by hyper_ch on 2008-10-27
and what bothers you now between ports closed and stealtehd ports?

---

### Post by Bruce M. on 2008-10-27
> **hyper_ch said:**
> and what bothers you now between ports closed and stealtehd ports?

You have posted three times, asking three questions, destroying my "no response" status and not offered any help.

Like I said:
> I've been through the "Closed vs Stealth" argument / opinions / discussion and don't want to get into that here. I simply want them **Closed**.

**Any help out there on how to Close these ports again?**

Do you know how I can close those ports!

Thanks
Bruce

---

### Post by nubdora on 2008-10-27
1. Remove Firestarter

2. [https://help.ubuntu.com/community/IptablesHowTo](https://help.ubuntu.com/community/IptablesHowTo)

---

### Post by brian_p on 2008-10-27
> **Bruce M. said:**
> 

Any help out there on how to **Close** these ports again?


The output of

```
sudo iptables -L
```

please.

---

### Post by cariboo on 2008-10-27
The way to close ports is to close the service that open them for instance this is the output of a quick port scan of my server:

```
 nmap willy

Starting Nmap 4.62 ( http://nmap.org ) at 2008-10-27 12:14 PDT
Interesting ports on willy (192.168.1.200):
Not shown: 1706 closed ports
PORT      STATE SERVICE
21/tcp    open  ftp
22/tcp    open  ssh
80/tcp    open  http
139/tcp   open  netbios-ssn
445/tcp   open  microsoft-ds
631/tcp   open  ipp
3306/tcp  open  mysql
8888/tcp  open  sun-answerbook
10000/tcp open  snet-sensor-mgmt
```

This is the result of the same port scan with all the services but ssh stopped (I need ssh to access the server). 

```
nmap willy

Starting Nmap 4.62 ( http://nmap.org ) at 2008-10-27 12:17 PDT
Interesting ports on willy (192.168.1.200):
Not shown: 1713 closed ports
PORT    STATE SERVICE
22/tcp  open  ssh
631/tcp open  ipp
```


Port 631 is cups, and it is only accessible from the computer it is running on.

Jim

---

### Post by Bruce M. on 2008-10-27
> **brian_p said:**
> The output of

```
sudo iptables -L
```

please.

Oh OH!!!!!!  This looks scary!
WARNING: I'm green behind the ears here!
```
bruloo@bruloo:~$ sudo iptables -L
[sudo] password for bruloo: 
Chain INPUT (policy DROP)
target     prot opt source               destination         
ACCEPT     tcp  --  rdns01.fibertel.com.ar  anywhere            tcp flags:!FIN,SYN,RST,ACK/SYN 
ACCEPT     udp  --  rdns01.fibertel.com.ar  anywhere            
ACCEPT     tcp  --  rdns02.fibertel.com.ar  anywhere            tcp flags:!FIN,SYN,RST,ACK/SYN 
ACCEPT     udp  --  rdns02.fibertel.com.ar  anywhere            
ACCEPT     tcp  --  rdns13.fibertel.com.ar  anywhere            tcp flags:!FIN,SYN,RST,ACK/SYN 
ACCEPT     udp  --  rdns13.fibertel.com.ar  anywhere            
ACCEPT     all  --  anywhere             anywhere            
ACCEPT     icmp --  anywhere             anywhere            limit: avg 10/sec burst 5 
DROP       all  --  anywhere             255.255.255.255     
DROP       all  --  anywhere             255.255.255.255     
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
ACCEPT     tcp  --  136-244-126-200.fibertel.com.ar  rdns01.fibertel.com.ar tcp dpt:domain 
ACCEPT     udp  --  136-244-126-200.fibertel.com.ar  rdns01.fibertel.com.ar udp dpt:domain 
ACCEPT     tcp  --  136-244-126-200.fibertel.com.ar  rdns02.fibertel.com.ar tcp dpt:domain 
ACCEPT     udp  --  136-244-126-200.fibertel.com.ar  rdns02.fibertel.com.ar udp dpt:domain 
ACCEPT     tcp  --  136-244-126-200.fibertel.com.ar  rdns13.fibertel.com.ar tcp dpt:domain 
ACCEPT     udp  --  136-244-126-200.fibertel.com.ar  rdns13.fibertel.com.ar udp dpt:domain 
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
bruloo@bruloo:~$ 

```
CHIMO!
Bruce

---

### Post by Bruce M. on 2008-10-27
> **nubdora said:**
> 1. Remove Firestarter

2. [https://help.ubuntu.com/community/IptablesHowTo](https://help.ubuntu.com/community/IptablesHowTo)

Thanks for this.

Why can't they simply have an: [Open] [Close] [Stealth] switch.  :)
Time to read...

Chimo!
Bruce

---

### Post by Bruce M. on 2008-10-27
Just as an added note:

My wife has been playing a lot of "flash" games online.

Would this affect anything?

I have FF set to accept cookies "until I close FF" then it cleans them out!

Chimo!
Bruce

---

### Post by brian_p on 2008-10-27
> **Bruce M. said:**
> 

Oh OH!!!!!!  This looks scary!
WARNING: I'm green behind the ears here!

[List of iptables rules snipped]

I don't know how you feel about the importance of all these rules (the DROP ones are probably causing GRC to indicate stealthed ports) but if removing firestarter does not delete them you will find plenty of advice from Google with 'iptables delete all rules'. Then retest at GRC.

For me

```
sudo iptables -L
```

gives a nice sensible output of:

```
Chain INPUT (policy ACCEPT)
target     prot opt source              destination         

Chain FORWARD (policy ACCEPT)
target     prot opt source              destination         

Chain OUTPUT (policy ACCEPT)
target     prot opt source              destination
```

---

### Post by brian_p on 2008-10-27
> **Bruce M. said:**
> Just as an added note:

My wife has been playing a lot of "flash" games online.

Would this affect anything?

Not to the extent of altering iptables rules. It could affect her libido.

---

### Post by koenn on 2008-10-27
> **brian_p said:**
> 
I don't know how you feel about the importance of all these rules (the DROP one are probably causing GRC to indicate stealthed ports) but if removing firestarter does not delete them you will find plenty of advice from Google with 'iptables delete all rules'. Then retest at GRC.



You're right that it's the DROP rules that result in "Stealthed" ports : any connection attempt to these ports will be ignored, so they are invisible (stealth), and if all ports are invisible, so is your computer.

If you change the DROP to DENY, connection attempts will receive "connection denied" and GRC Shields Up will report them as "Closed"

---

### Post by Bruce M. on 2008-10-27
> **cariboo907 said:**
> The way to close ports is to close the service that open them for instance this is the output of a quick port scan of my server:

I don't have **nmap**.  I'm not running a server, just a lone desktop.

Chimo!
Bruce

---

### Post by Bruce M. on 2008-10-27
> **koenn said:**
> You're right that it's the DROP rules that result in "Stealthed" ports : any connection attempt to these ports will be ignored, so they are invisible (stealth), and if all ports are invisible, so is your computer.

If you change the DROP to DENY, connection attempts will receive "connection denied" and GRC Shields Up will report them as "Closed"

OK, now I have to read up on that link for IPtables on how to do that.

Strange thing is when I first installed Ubuntu all ports were closed except one. It was stealth. Last week I saw 3 - stealth, now all of them.

Something changed them and it wasn't me.  :(

Chimo!
Bruce

---

### Post by santiagoward2000 on 2008-10-27
Hi!
I'm not really sure about this, but wouldn't ```
sudo ufw default deny
``` do the trick?
If I'm completely wrong, please ignore me!

---

### Post by brian_p on 2008-10-27
> **Bruce M. said:**
> 

Something changed them and it wasn't me.  :(


Sorry to disagree here, but you have control of your machine and that fistful of iptables rules could only have come about with your permission.

I'll suggest again you delete all of them and have sane ACCEPT policies.

---

### Post by koenn on 2008-10-27
> **Bruce M. said:**
> 
Strange thing is when I first installed Ubuntu all ports were closed except one. It was stealth. Last week I saw 3 - stealth, now all of them.

Something changed them and it wasn't me.  :(

"Connection Denied" is the OS's normal reply to a connection attempt to a port where no service is listening, so normally you should get all ports "Closed" in a port scan such as GRC's. 
It's part of the TCP/IP handshake. To make your TCP/IP stack ignore connection attempts, you explicetly have to tell it to do so.
So something or somebody changed that, whether it was you or not :)

---

### Post by koenn on 2008-10-27
> **brian_p said:**
> 
I'll suggest again you delete all of them and have sane ACCEPT policies.
this needs a few grains of salt:

Having ACCEPT policies across the board is equivalent to having no firewall at all, and is only sane if you're absolutely sure you're not running any listening services, don't want to limit outgoing connections, and the PC in question is not set up to do routing.
That happens to be the case for a default ubuntu desktop, but stops being the case as soon as you start sharing folders, enable remote desktops, etc.

---

### Post by Bruce M. on 2008-10-27
> **brian_p said:**
> [List of iptables rules snipped]

I don't know how you feel about the importance of all these rules (the DROP ones are probably causing GRC to indicate stealthed ports) but if removing firestarter does not delete them you will find plenty of advice from Google with 'iptables delete all rules'. Then retest at GRC.

If those "rules" are what changed my set up I want them "GONE" that's how I feel about them.

I have never changed my iptables and have a default setup with Firestarter. In other words, I have not "conscientiously" changed anything for two reasons:
[LIST=1]
[*]I don't know a thing about iptables - therefore I've never touched it.
[*]I liked the "Closed" status my ports had by Ubuntus default.
[/LIST]

> **brian_p said:**
> For me

```
sudo iptables -L
```

gives a nice sensible output of:

```
Chain INPUT (policy ACCEPT)
target     prot opt source              destination         

Chain FORWARD (policy ACCEPT)
target     prot opt source              destination         

Chain OUTPUT (policy ACCEPT)
target     prot opt source              destination
```

WoW! That looks nice an clean, wish mine was like that.

Chimo!
Bruce

---

### Post by Bruce M. on 2008-10-27
> **brian_p said:**
> Not to the extent of altering iptables rules. It could affect her libido.

That's a relief and a :lolflag:

---

### Post by Bruce M. on 2008-10-27
> **koenn said:**
> If you change the DROP to DENY, connection attempts will receive "connection denied" and GRC Shields Up will report them as "Closed"

OK, now to figure out how to change DROP to DENY.

And just as important now, *what caused them to change?*

The only program I've added in the past little while is Pidgin and got a gmail account to use with it.

Chimo!
Bruce

---

### Post by cariboo on 2008-10-27
You don't need a server to run nmap, it is in the repositories and there is even a gui called zenmap for the keyboard challenged.

Jim

---

### Post by koenn on 2008-10-27
> **Bruce M. said:**
> OK, now to figure out how to change DROP to DENY.

And just as important now, *what caused them to change?*

The only program I've added in the past little while is Pidgin and got a gmail account to use with it.

Chimo!
Bruce

Maybe you can change DENY to DROP with firestarter ?
And maybe firestarter put those DENY policies and rules to begin with - by default the moment you installed it ?

---

### Post by Bruce M. on 2008-10-27
> **santiagoward2000 said:**
> Hi!
I'm not really sure about this, but wouldn't ```
sudo ufw default deny
``` do the trick?
If I'm completely wrong, please ignore me!

Hola Santiago

Never heard of ufw before so I checked the man page and found it had a --dry-run command and tried that.

```
Usage: ufw COMMAND

Commands:
  enable			Enables the firewall
  disable			Disables the firewall
  default ARG			set default policy to ALLOW or DENY
  logging ARG			set logging to ON or OFF
  allow|deny RULE		allow or deny RULE
  delete allow|deny RULE	delete the allow/deny RULE
  status			show firewall status
  version			display version information

bruloo@bruloo:~$ sudo ufw --dry-run default deny
Default policy changed to 'deny'
(be sure to update your rules accordingly)
bruloo@bruloo:~$
``` 

Now how would one "update your rules"?

Chimo!
Bruce

---

### Post by Bruce M. on 2008-10-27
> **cariboo907 said:**
> You don't need a server to run nmap, it is in the repositories and there is even a gui called zenmap for the keyboard challenged.

Jim

But it looks like it's for a server... which I'm not running.

:(
Chimo!
Bruce

---

### Post by Bruce M. on 2008-10-27
> **brian_p said:**
> Sorry to disagree here, but you have control of your machine and that fistful of iptables rules could only have come about with your permission.

I'll suggest again you delete all of them and have sane ACCEPT policies.

OK, in one respect you are right, my machine, my responsibility, but I did not consciously make any change (I don't know how) and wouldn't have if I had known, because I prefer the "Closed" status.

*ROCK* **-> ME <-** *HARDPLACE*
If I had hair left I'd be pulling it out!

Chimo!
Bruce

---

### Post by Bruce M. on 2008-10-27
> **koenn said:**
> this needs a few grains of salt:

OK, I'll take a few grains.

> **koenn said:**
> Having ACCEPT policies across the board is equivalent to having no firewall at all, and is only sane if you're absolutely sure you're not running any listening services, don't want to limit outgoing connections, and the PC in question is not set up to do routing.

Listening services? What are those?

No router here, just a desktop connected to a cable modem for the net.

> **koenn said:**
> That happens to be the case for a default ubuntu desktop, but stops being the case as soon as you start sharing folders, enable remote desktops, etc.

not sharing folders, nor remote desktop.  {sigh}

Chimo!
Bruce

---

### Post by santiagoward2000 on 2008-10-27
> **Bruce M. said:**
> Hola Santiago

Never heard of ufw before so I checked the man page and found it had a --dry-run command and tried that.

Now how would one "update your rules"?

Chimo!
Bruce

Hola Bruce! :)
Now if you've already set the default policy to deny, you've got to enable ufw by doing:
```
sudo ufw enable
```
Then, if you want to open a certain port, all you need to do is:
```
sudo ufw allow PORT
``` (changing PORT for the port you want, of course).
In case you want to delete a rule, just:
```
sudo ufw delete allow PORT
```
Cheers!

_EDIT:_
Just in case you want to check it:
```
sudo ufw status
``` shows if ufw is enabled/disabled and all the rules you've set.

---

### Post by koenn on 2008-10-27
> **Bruce M. said:**
> 
Listening services? What are those?

it's a servive (piece of softwrare, program, a process) that "listens" i.e. waits for incoming connections, 
like:
apache listens and waits till it "hears" a request for a web page
samba listens and waits till it "hears" a request for a shared file
vnc listens and waits till it "hears" a request for (remote) access to the desktop
and so on.

---

### Post by The Cog on 2008-10-27
You say you didn't change the iptables rules yourself. I'm finding that hard to believe. Since the default install leaves the iptables rules allowing all traffic in and out, the most likely explanation is that you installed a firewall which made the changes. I think the default firestarter config is to drop (stealth) all incoming connections. Are you sure you didn't install firestarter during that time?

Completely removing firestarter should also remove the config files, including the one that sets the iptables rules on boot-up.

---

### Post by brian_p on 2008-10-27
> **koenn said:**
> this needs a few grains of salt:

As many as there are in a litre of distilled water would be a good estimate.

---

### Post by Bruce M. on 2008-10-27
> **The Cog said:**
> You say you didn't change the iptables rules yourself. I'm finding that hard to believe. Since the default install leaves the iptables rules allowing all traffic in and out, the most likely explanation is that you installed a firewall which made the changes. I think the default firestarter config is to drop (stealth) all incoming connections. Are you sure you didn't install firestarter during that time?

Believe it as I said it before and I'll say once more: *I changed nothing, I don't know how.*

I did install Firestarter and left it at it's defaults.

> **The Cog said:**
> Completely removing firestarter should also remove the config files, including the one that sets the iptables rules on boot-up.

Now if Firestarter did that I'll do a complete-remove it and do a reboot to see.

CHIMO!
Bruce

---

### Post by Bruce M. on 2008-10-27
> **koenn said:**
> it's a servive (piece of softwrare, program, a process) that "listens" i.e. waits for incoming connections, 
like:
apache listens and waits till it "hears" a request for a web page
samba listens and waits till it "hears" a request for a shared file
vnc listens and waits till it "hears" a request for (remote) access to the desktop
and so on.

I run none of those...
Does Pidgin fit in there somewhere?

Thanks for the explanation
Bruce

---

### Post by Bruce M. on 2008-10-27
> **Bruce M. said:**
> Now if Firestarter did that I'll do a complete-remove it and do a reboot to see.

MUCH Better - Firestarter!!!!!! GRRRRRRRRRRRRRRRR!!!!!!!!!!

Now I only have a few ports to find.  :)

CHIMO!
Bruce

---

### Post by jerome1232 on 2008-10-28
No matter what you do a few ports may be 'stealthed' because some isp's filter them to prevent you from running certain types of server's on the connection, namely ports 25 and 80 are the most common (that's email and web traffic)

I just can't help to toss in that having ports closed/stealthed against incoming traffic shouldn't have any affect what-so-ever on your connection, the program that edited iptables (firestarter) probably put some outgoing rules that were causing the problems, I did see some outgoing rules in that output you posted but didn't feel like mowing it over to see what they were doing.

Glad you were able to get it fixed. :)

---

### Post by Bruce M. on 2008-10-28
Yours:

> **brian_p said:**
> 
```
Chain INPUT (policy ACCEPT)
target     prot opt source              destination         

Chain FORWARD (policy ACCEPT)
target     prot opt source              destination         

Chain OUTPUT (policy ACCEPT)
target     prot opt source              destination
```

mine today:
```
bruloo@bruloo:~$ sudo iptables -L
Chain INPUT (policy ACCEPT)
target     prot opt source               destination         

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination         
bruloo@bruloo:~$
```

Colour Me Happy :biggrin:
CHIMO!
Bruce

---

### Post by Bruce M. on 2008-10-28
> **jerome1232 said:**
> No matter what you do a few ports may be 'stealthed' because some isp's filter them to prevent you from running certain types of server's on the connection, namely ports 25 and 80 are the most common (that's email and web traffic)

That I can live with.

> **jerome1232 said:**
> I just can't help to toss in that having ports closed/stealthed against incoming traffic shouldn't have any affect what-so-ever on your connection, the program that edited iptables (firestarter) probably put some outgoing rules that were causing the problems, I did see some outgoing rules in that output you posted but didn't feel like mowing it over to see what they were doing.

Glad you were able to get it fixed. :)

That's the last this computer will ever see of firestarter. I have the links to the iptables from here and will read.

I had no idea what those rules were, but glad they are done with.

CHIMO!
Bruce

---

