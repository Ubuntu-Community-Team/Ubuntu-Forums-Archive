---
title: "iptables problem"
date: 2009-05-04
forum: Security
---

### Post by satimis on 2009-05-04
Hi folks,

Ubuntu 8.10

On running following command;

# iptables -A INPUT -m state --state ESTABLISHED,RELATED -j ACCEPT```

iptables: No chain/target/match by that name

```

I have been googling a while unable to solve the problem.  Please help.  TIA

B.R.
satimis

---

### Post by bodhi.zazen on 2009-05-04
what guest are you running that command on ? Are you using virtualization ?

---

### Post by HermanAB on 2009-05-04
Howdy,

As the error message indicates, the target is missing.

You should at least add something like '-i eth0' to that command.

---

### Post by bodhi.zazen on 2009-05-04
That command is nonetheless valid :

```
root@server:~#iptables -A INPUT -m state --state ESTABLISHED,RELATED -j ACCEPT

root@server:~#iptables -L -v
Chain INPUT (policy ACCEPT 35806 packets, 38M bytes)
 pkts bytes target     prot opt in     out     source               destination 
   26  1820 ACCEPT     all  --  any    any     anywhere             anywhere            state RELATED,ESTABLISHED

Chain FORWARD (policy ACCEPT 1868 packets, 1699K bytes)
 pkts bytes target     prot opt in     out     source               destination 

Chain OUTPUT (policy ACCEPT 28040 packets, 4444K bytes)
 pkts bytes target     prot opt in     out     source               destination 


```

---

### Post by uljanow on 2009-05-04
Is the xt_state module enabled in your kernel ?

```
grep -ri state /boot/config-$(uname -r)
```

---

### Post by satimis on 2009-05-04
Hi folks,

Thanks for your advice.

This is a fresh installed 8.10 under OpenVZ as VE (guest). I'm searching around to find out whether it is the problem of OpenVZ kernel. 


I found this problem on 8.04 running on another VE of this VM.  On running shorewall;

# /etc/init.d/shorewall restart```

Restarting "Shorewall firewall": not done (check /var/log/shorewall-init.log).

```


# tail /var/log/shorewall-init.log```

   Shorewall is not running
22:34:10 Starting Shorewall....
22:34:10 Initializing...
22:34:10 Clearing Traffic Control/QOS
22:34:10 Deleting user chains...
iptables: No chain/target/match by that name
   ERROR: Command "/sbin/iptables -A FORWARD -m state --state ESTABLISHED,RELATED -j ACCEPT" Failed
iptables: No chain/target/match by that name
iptables: No chain/target/match by that name
Terminated

```

I wonder whether I have to disable ip6tables. I have no idea how to disable it. Googling brought me some suggestion.


On VE running 8.04

# grep -ri state /boot/config-$(uname -r)```

grep: /boot/config-2.6.24-23-openvz: No such file or directory

```


On VE running 8.10

# /# grep -ri state /boot/config-$(uname -r)```

-bash: /#: No such file or directory

```


Any advice.  TIA


B.R.
satimis

---

### Post by bodhi.zazen on 2009-05-04
Just as I suspected :twisted:

I can post the exact line later tonight, but basically you need to edit 

/etc/vz/vz.conf

and add in a few kernel modules.

First stop your guest ...

On the host ```
lsmod | grep iptables
```

Then, on the host, open /etc/vz/vz.conf

Look for the line IPTABLES="ip_tables ipt_limit iptable_filter ..."

add in the missing kernel modules (I can not recall which one you need to add at the moment).

Re-start your guest.

See my post in this thread (second to last) :

[http://forum.openvz.org/index.php?t=msg&goto=28807&](http://forum.openvz.org/index.php?t=msg&goto=28807&)

gotta love google ;)

---

### Post by satimis on 2009-05-05
Hi bodhi.zazen,


Thanks for your advice.

> **bodhi.zazen said:**
> Just as I suspected :twisted:

I can post the exact line later tonight, 


Thanks


> 
but basically you need to edit 

/etc/vz/vz.conf

and add in a few kernel modules.

First stop your guest ...

On the host ```
lsmod | grep iptables
```

Then, on the host, open /etc/vz/vz.conf

Look for the line IPTABLES="ip_tables ipt_limit iptable_filter ..."

add in the missing kernel modules (I can not recall which one you need to add at the moment).

Re-start your guest.


$ sudo lsmod | grep iptables
$ sudo lsmod | grep ipt_recent
Both without printout

$ cat /etc/vz/vz.conf | grep IPTABLES```

IPTABLES="ipt_REJECT ipt_tos ipt_limit ipt_multiport iptable_filter iptable_mangle ipt_TCPMSS ipt_tcpmss ipt_ttl ipt_length"

```

$ uname -r```

2.6.24-23-openvz

```
Whether add "2.6.24-23-openvz" ?

> 
See my post in this thread (second to last) :

[http://forum.openvz.org/index.php?t=msg&goto=28807&](http://forum.openvz.org/index.php?t=msg&goto=28807&)

Whether start from "message #28759" until the end?


Edit:

On host;

$ sudo iptables -L```

[sudo] password for satimis: 
Chain INPUT (policy ACCEPT)
target     prot opt source               destination         

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination     

```


B.R.
satimis

---

### Post by bodhi.zazen on 2009-05-05
Put the line I posted in the openvz thread into /etc/vz.conf (comment out or edit the current line).

Then re-start your guest.

---

### Post by satimis on 2009-05-05
> **bodhi.zazen said:**
> Put the line I posted in the openvz thread into /etc/vz.conf (comment out or edit the current line).

Then re-start your guest.
Performed following steps;

On host:-

Edited /etc/vz/vz.conf

commenting out following line;```

#IPTABLES="ipt_REJECT ipt_tos ipt_limit ipt_multiport iptable_filter iptable_mangle ipt_TCPMSS ipt_tcpmss ipt_ttl ipt_length"

```

adding following line;```

IPTABLES="ipt_REJECT ipt_tos ipt_TOS ipt_limit ipt_multiport iptable_filter iptable_mangle ipt_TCPMSS ipt_tcpmss ipt_ttl ipt_length ipt_state ipt_LOG ip_conntrack iptable_nat ip_nat_ftp ipt_recent"

```

$ cat /etc/vz/vz.conf | grep IPTABLES```

#IPTABLES="ipt_REJECT ipt_tos ipt_limit ipt_multiport iptable_filter iptable_mangle ipt_TCPMSS ipt_tcpmss ipt_ttl ipt_length"
IPTABLES="ipt_REJECT ipt_tos ipt_TOS ipt_limit ipt_multiport iptable_filter iptable_mangle ipt_TCPMSS ipt_tcpmss ipt_ttl ipt_length ipt_state ipt_LOG ip_conntrack iptable_nat ip_nat_ftp ipt_recent"

```

$ sudo vzctl restart 102```

Warning: Unknown iptable module: ipt_recent, skipped
Restarting VE
Stopping VE ...
VE was stopped
VE is unmounted
Starting VE ...
VE is mounted

```

$ sudo vzctl enter 102```

Warning: Unknown iptable module: ipt_recent, skipped
entered into VE 102

```

On guest;

# /etc/init.d/shorewall restart```

Restarting "Shorewall firewall": not done (check /var/log/shorewall-init.log).

```

# tail /var/log/shorewall-init.log```

   Shorewall is not running
23:39:12 Starting Shorewall....
23:39:12 Initializing...
23:39:12 Clearing Traffic Control/QOS
23:39:12 Deleting user chains...
iptables: No chain/target/match by that name
   ERROR: Command "/sbin/iptables -A FORWARD -m state --state ESTABLISHED,RELATED -j ACCEPT" Failed
iptables: No chain/target/match by that name
iptables: No chain/target/match by that name
Terminated

```

Still the same.


B.R.
satimis

---

### Post by bodhi.zazen on 2009-05-05
OUCH !!

Well it "works for me".

I suggest you enter the guest and run the command manually :

```
iptables -A FORWARD -m state --state ESTABLISHED,RELATED -j ACCEPT
```

and test it ...

If it FAILS to work from the command line, I assume, as per the thread on OpenVZ, the problem is with vzctrl. So update vzctrl ...

If you are on an updated vzctrl, then you should fiel a bug report with openzv (as I said, it works on Proxmox).

It it WORKS on the command line, then the but is with shorewall and I suggest you configure your firewall manually. If it is a shorewall bug you can post a bug report with shorewall, not sure of the interest they will have in fixing it ;)

As you can see, I do get error messages :

```
[color=darkred]root@Proxmox:~# vzctl enter 101[/color]
Warning: Unknown iptable module: ipt_recent, skipped
entered into CT 101

[color=green]VPS Guest:/# iptables -L[/color]
Chain INPUT (policy ACCEPT)
target     prot opt source               destination

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination


[color=green]VPS Guest:/# iptables -A FORWARD -m state --stateESTABLISHED,RELATED -j ACCEPT[/color]

[color=green]VPS Guest:/# iptables -L[/color]
Chain INPUT (policy ACCEPT)
target     prot opt source               destination

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination
ACCEPT     all  --  anywhere             anywhere            state RELATED,ESTABLISHED

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination
```

So even though I have error messages, iptables works.

And from /etc/vz/vc.conf :

> IPTABLES="ipt_REJECT ipt_tos ipt_TOS ipt_limit ipt_multiport iptable_filter iptable_mangle ipt_TCPMSS ipt_tcpmss ipt_ttl ipt_length ipt_state ipt_LOG ip_conntrack iptable_nat ip_nat_ftp ipt_recent"

---

### Post by satimis on 2009-05-06
> **bodhi.zazen said:**
> OUCH !!

Well it "works for me".

I suggest you enter the guest and run the command manually :

```
iptables -A FORWARD -m state --state ESTABLISHED,RELATED -j ACCEPT
```

and test it ...

If it FAILS to work from the command line, I assume, as per the thread on OpenVZ, the problem is with vzctrl. So update vzctrl ...

If you are on an updated vzctrl, then you should fiel a bug report with openzv (as I said, it works on Proxmox).

It it WORKS on the command line, then the but is with shorewall and I suggest you configure your firewall manually. If it is a shorewall bug you can post a bug report with shorewall, not sure of the interest they will have in fixing it ;)

As you can see, I do get error messages :

```
[color=darkred]root@Proxmox:~# vzctl enter 101[/color]
Warning: Unknown iptable module: ipt_recent, skipped
entered into CT 101

[color=green]VPS Guest:/# iptables -L[/color]
Chain INPUT (policy ACCEPT)
target     prot opt source               destination

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination


[color=green]VPS Guest:/# iptables -A FORWARD -m state --stateESTABLISHED,RELATED -j ACCEPT[/color]

[color=green]VPS Guest:/# iptables -L[/color]
Chain INPUT (policy ACCEPT)
target     prot opt source               destination

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination
ACCEPT     all  --  anywhere             anywhere            state RELATED,ESTABLISHED

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination
```

So even though I have error messages, iptables works.

And from /etc/vz/vc.conf :

On host;

$ sudo vzctl enter 102
[sudo] password for satimis: ```

Warning: Unknown iptable module: ipt_recent, skipped
entered into VE 102

```


On guest;

# iptables -A FORWARD -m state --state ESTABLISHED,RELATED -j ACCEPT

No complaint


# /etc/init.d/shorewall restart```

Restarting "Shorewall firewall": not done (check /var/log/shorewall-init.log).

```


# /etc/init.d/shorewall stop   ```

Stopping "Shorewall firewall": done.

```


# /etc/init.d/shorewall start```

Starting "Shorewall firewall": not done (check /var/log/shorewall-init.log).

```


# tail /var/log/shorewall-init.log```

08:49:46    Rule "DROP - - udp 1900 -  - " added.
08:49:46    Rule "dropNotSyn - - tcp     " added.
08:49:46    Rule "DROP - - udp - 53  - " added.
08:49:46 Creating action chain dropBcast
08:49:46 Creating action chain dropInvalid
08:49:46 Creating action chain dropNotSyn
08:49:46 Applying Policies...
iptables: Memory allocation problem
   ERROR: Command "/sbin/iptables -N net2all" Failed
Terminated

```


# iptables -L```

Chain INPUT (policy DROP)
target     prot opt source               destination         
ACCEPT     all  --  anywhere             anywhere            state RELATED,ESTABLISHED 
ACCEPT     all  --  0.0.0.0              anywhere            
ACCEPT     all  --  anywhere             anywhere            

Chain FORWARD (policy DROP)
target     prot opt source               destination         
ACCEPT     all  --  anywhere             anywhere            state RELATED,ESTABLISHED 
ACCEPT     all  --  0.0.0.0              0.0.0.0             

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination         

```


# apt-get update```

Hit http://archive.canonical.com hardy Release.gpg                             
Get:1 http://security.ubuntu.com hardy-security Release.gpg [189B]             

.....
......
Fetched 588kB in 5s (98.3kB/s)                      
Reading package lists... Done

```
No complaint.


# apt-get upgrade```

Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

```
No package updated


Again on host;

# apt-get update
No complaint


# apt-get upgrade```

Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

```

No package upgraded.


$ cat /etc/vz/vz.conf | grep IPTABLES```

#IPTABLES="ipt_REJECT ipt_tos ipt_limit ipt_multiport iptable_filter iptable_mangle ipt_TCPMSS ipt_tcpmss ipt_ttl ipt_length"
IPTABLES="ipt_REJECT ipt_tos ipt_TOS ipt_limit ipt_multiport iptable_filter iptable_mangle ipt_TCPMSS ipt_tcpmss ipt_ttl ipt_length ipt_state ipt_LOG ip_conntrack iptable_nat ip_nat_ftp ipt_recent"

```


B.R.
satimis

---

### Post by bodhi.zazen on 2009-05-06
From what you have posted it appears Shorewall does not like being run in your VPS.

I get the same "Warning" and to be honest I do not know what it means and iptables , as you can see, is working.

To be honest, I found learning iptables was about as difficult as learning shorewall and my advice is to use iptables directly.

In this case I would imagine the rules you wish to use would be very straight forward.

along those lines, IMO it is not so good to set a default policy of DROP. This is because if you do and you run "iptables -F" you will lose remote connectivity.

I just add a line at the end of my rules to drop all traffic. This is the same as setting a default policy, but is cleared when you -F .

iptables -a INPUT -j DROP

Just my 2c.

---

### Post by satimis on 2009-05-06
> **bodhi.zazen said:**
> From what you have posted it appears Shorewall does not like being run in your VPS.

I get the same "Warning" and to be honest I do not know what it means and iptables , as you can see, is working.

To be honest, I found learning iptables was about as difficult as learning shorewall and my advice is to use iptables directly.

In this case I would imagine the rules you wish to use would be very straight forward.

along those lines, IMO it is not so good to set a default policy of DROP. This is because if you do and you run "iptables -F" you will lose remote connectivity.

I just add a line at the end of my rules to drop all traffic. This is the same as setting a default policy, but is cleared when you -F .

iptables -a INPUT -j DROP

Hi bodhi.zazen,

I have another Virtual Machine running Xen with Debian 4.0 as OS running on host and guests.  Shorewall is running on guest without problem.  However Shorewall is the front end.  The backend is iptables.

I'll leave it as it is.  The box is for testing NOT for production.

Thanks again for your assistance.


B.R.
satimis

---

