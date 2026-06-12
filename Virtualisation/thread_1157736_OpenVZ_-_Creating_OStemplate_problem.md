---
title: "OpenVZ - Creating OStemplate problem"
date: 2009-05-13
forum: Virtualisation
---

### Post by satimis on 2009-05-13
Hi folks,


OpenVZ


On creating ostemplate I encountered following error;

Disable sync() for syslog 
[http://wiki.openvz.org/Debian_template_creation#Disable_sync.28.29_for_syslog](http://wiki.openvz.org/Debian_template_creation#Disable_sync.28.29_for_syslog)


# sed -i -e 's@\([[:space:]]\)\(/var/log/\)@\1-\2@' /etc/syslog.conf```

sed: can't read /etc/syslog.conf: No such file or directory

```

# updatedb 

# locate syslog.conf```

/etc/rsyslog.conf
/usr/share/man/man5/rsyslog.conf.5.gz
/var/lib/dpkg/info/rsyslog.conffiles

```

Please advise how to fix the problem.  TIA


B.R.
satimis

---

### Post by bodhi.zazen on 2009-05-13
Well your syntax is off.

The command is :

> sed -i -e 's@\([[:space:]]\)\(/var/log/\)@\1-\2@' /etc/*syslog.confNotice the * in /etc/*syslog.conf ?

The output of your locate command shows :

/etc/rsyslog.conf

See the r in /etc/rsyslog.conf ?

So, either add the * or change to an r

```
sed -i -e 's@\([[:space:]]\)\(/var/log/\)@\1-\2@' /etc/rsyslog.conf
```

If you prefer, here is my template (it is 32 bit, I have a 64 bit template if you like)

[http://bodhizazen.net/adblock/ubuntu-9.04-i386-minimal.tar.gz](http://bodhizazen.net/adblock/ubuntu-9.04-i386-minimal.tar.gz)

---

### Post by satimis on 2009-05-13
> **bodhi.zazen said:**
> Well your syntax is off.

The command is :

Notice the * in /etc/*syslog.conf ?

The output of your locate command shows :

/etc/rsyslog.conf

See the r in /etc/rsyslog.conf ?

So, either add the * or change to an r

```
sed -i -e 's@\([[:space:]]\)\(/var/log/\)@\1-\2@' /etc/rsyslog.conf
```


Hi bodhi.zazen,

Noted.  Thanks.  Got it fixed.


> 
If you prefer, here is my template (it is 32 bit, I have a 64 bit template if you like)

[http://bodhizazen.net/adblock/ubuntu-9.04-i386-minimal.tar.gz](http://bodhizazen.net/adblock/ubuntu-9.04-i386-minimal.tar.gz)

Oh, thanks.  You came in the right time.  Just finished creating a Debian 5.0 template.  I was looking around the URL for downloading Ubuntu 9.04 to create Ubuntu 9.04 template.

Have Ubuntu 9.04 container created.  Do I need adding;```

deb-src http://us.archive.ubuntu.com/ubuntu/ jaunty main universe multiverse

deb-src http://us.archive.ubuntu.com/ubuntu/ jaunty-security main universe multiverse
```

on /etc/apt/sources.list ?  TIA


B.R.
satimis

---

### Post by bodhi.zazen on 2009-05-13
Only if you wish to compile from source. (deb-src are for source code).

---

### Post by satimis on 2009-05-13
> **bodhi.zazen said:**
> Only if you wish to compile from source. (deb-src are for source code).
Thanks.

I can't make iptables working properly on VE because OpenVZ kernel has limited support on it. 

I'll try to install APF;
[http://www.rfxn.com/projects/](http://www.rfxn.com/projects/)

on Ubuntu 9.04 to check whether I can make APF work on it.  If NOT I'll forget OpenVZ.  


My personal preference on building virtual machine;

for container type Virtual Machine - Xen
for full virtualization - KVM

I tested both of them before.  They are quite mature.


B.R.
satimis

---

### Post by bodhi.zazen on 2009-05-13
Iptables works in openvz containers.

There are several methods, dpeneding on what you want :

[http://wiki.openvz.org/Setting_up_an_iptables_firewall](http://wiki.openvz.org/Setting_up_an_iptables_firewall)

I use this in /etc/vz/vz.conf :

> IPTABLES="ipt_REJECT ipt_tos ipt_TOS ipt_limit ipt_multiport iptable_filter iptable_mangle ipt_TCPMSS ipt_tcpmss ipt_ttl ipt_length ipt_state ipt_LOG ip_conntrack iptable_nat ip_nat_ftp ipt_recent"You may need to install it on your template :

```
apt-get install iptables
```Demo :

```
 vzctl exec 102 iptables -L
Warning: Unknown iptable module: ipt_recent, skipped
Chain INPUT (policy ACCEPT)
target     prot opt source               destination         

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination
 
[COLOR=green]root:~# vzctl exec 102 iptables -A INPUT -p tcp --sport 53 -j ACCEPT[/COLOR]
Warning: Unknown iptable module: ipt_recent, skipped

[COLOR=green]root:~# vzctl exec 102 iptables -L[/COLOR]
Warning: Unknown iptable module: ipt_recent, skipped
Chain INPUT (policy ACCEPT)
target     prot opt source               destination         
[COLOR=navy]ACCEPT     tcp  --  anywhere             anywhere            tcp spt:domain [/COLOR]

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination
```

---

### Post by satimis on 2009-05-14
> **bodhi.zazen said:**
> Iptables works in openvz containers.

There are several methods, dpeneding on what you want :

[http://wiki.openvz.org/Setting_up_an_iptables_firewall](http://wiki.openvz.org/Setting_up_an_iptables_firewall)

I use this in /etc/vz/vz.conf :

You may need to install it on your template :

```
apt-get install iptables
```Demo :

```
 vzctl exec 102 iptables -L
Warning: Unknown iptable module: ipt_recent, skipped
Chain INPUT (policy ACCEPT)
target     prot opt source               destination         

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination
 
[COLOR=green]root:~# vzctl exec 102 iptables -A INPUT -p tcp --sport 53 -j ACCEPT[/COLOR]
Warning: Unknown iptable module: ipt_recent, skipped

[COLOR=green]root:~# vzctl exec 102 iptables -L[/COLOR]
Warning: Unknown iptable module: ipt_recent, skipped
Chain INPUT (policy ACCEPT)
target     prot opt source               destination         
[COLOR=navy]ACCEPT     tcp  --  anywhere             anywhere            tcp spt:domain [/COLOR]

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination
```

On host run;

satimis@vz0:~$ cat /etc/vz/vz.conf | grep IPTABLES```

IPTABLES="ipt_REJECT ipt_tos ipt_limit ipt_multiport iptable_filter iptable_mangle ipt_TCPMSS ipt_tcpmss ipt_ttl ipt_length"
#IPTABLES="ipt_REJECT ipt_tos ipt_TOS ipt_limit ipt_multiport iptable_filter iptable_mangle ipt_TCPMSS ipt_tcpmss ipt_ttl ipt_length ipt_state ipt_LOG ip_conntrack iptable_nat ip_nat_ftp ipt_recent"
```

The 2nd line commented out is similar to yours.  

Comment out the 1st and uncomment the 2nd line.


On guest (VE 102)

root@vz2:/# apt-cache policy iptables```

iptables:
  Installed: 1.3.8.0debian1-1ubuntu2
  Candidate: 1.3.8.0debian1-1ubuntu2
  Version table:
 *** 1.3.8.0debian1-1ubuntu2 0
        500 http://archive.ubuntu.com hardy/main Packages
        100 /var/lib/dpkg/status

```

Iptables is running.


root@vz2:/# iptables -L```

Chain INPUT (policy ACCEPT)
target     prot opt source               destination         

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination         

```

No rules set up


root@vz2:/# iptables -A INPUT -p tcp --sport 53 -j ACCEPT
No complaint


root@vz2:/# iptables -L```

Chain INPUT (policy ACCEPT)
target     prot opt source               destination         
ACCEPT     tcp  --  anywhere             anywhere            tcp spt:domain 

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination    

```


Reboot the PC.


satimis@vz0:~$ sudo vzctl enter 102```

[sudo] password for satimis: 
Warning: Unknown iptable module: ipt_recent, skipped
entered into VE 102

```

It complains.  Before there is no complaint.


root@vz2:/# iptables -L```

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


root@vz2:/# /etc/init.d/shorewall stop```

Stopping "Shorewall firewall": done.

```


root@vz2:/# /etc/init.d/shorewall start```

Starting "Shorewall firewall": not done (check /var/log/shorewall-init.log).

```


root@vz2:/# tail /var/log/shorewall-init.log```

06:19:50    Rule "DROP - - udp 1900 -  - " added.
06:19:50    Rule "dropNotSyn - - tcp     " added.
06:19:50    Rule "DROP - - udp - 53  - " added.
06:19:50 Creating action chain dropBcast
06:19:50 Creating action chain dropInvalid
06:19:50 Creating action chain dropNotSyn
06:19:50 Applying Policies...
iptables: Memory allocation problem
   ERROR: Command "/sbin/iptables -N net2all" Failed
Terminated

```


Any suggestion to fix the problem?  TIA


B.R.
satimis

---

### Post by bodhi.zazen on 2009-05-14
For some reason shorewall does not work in the containers.

If you can run shorewall, you can manually configure iptables (honestly, other then familiarity, shorewall is not so easy to configure).

You can also firewall using the host. See the link I gave you already.

You can get more complex if you wish.

[VM-firewall - Virtualization firewall]("http://www.fridu.org/fulup-posts/40-hosting-a-sysadmin/79-virtualization-firewall")

---

