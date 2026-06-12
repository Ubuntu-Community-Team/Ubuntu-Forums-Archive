---
title: "Iptables issue after an upgrade"
date: 2010-07-05
forum: Security
---

### Post by andremta on 2010-07-05
I am using TomCat6 with Ubuntu Server 9.10 x64. 

I successfully configured to iptables to redirect the port "443" to "8443" (Tomcat SSL), using this command:

> 
iptables -A PREROUTING -t nat -i eth0 -p tcp --dport 443 -j REDIRECT --to-port 8443


After an automatic upgrade that needed a reboot, I reboot the system. 

Now the iptables redirection fails to redirect! The "8443" is up.
I've tried the same command again, but nothing.

> 
user@server:~$ sudo iptables -t nat -L -n -v
Chain PREROUTING (policy ACCEPT 562 packets, 48141 bytes)
 pkts bytes target     prot opt in     out     source               destination
    0     0 REDIRECT   tcp  --  eth0   *       0.0.0.0/0            0.0.0.0/0           tcp dpt:443 redir ports 8443
    0     0 REDIRECT   tcp  --  eth0   *       0.0.0.0/0            0.0.0.0/0           tcp dpt:443 redir ports 8443

Chain POSTROUTING (policy ACCEPT 305 packets, 18794 bytes)
 pkts bytes target     prot opt in     out     source               destination

Chain OUTPUT (policy ACCEPT 305 packets, 18794 bytes)
 pkts bytes target     prot opt in     out     source               destination
user@server:~$



**UFW**
> 443                        ALLOW       192.168.0.0/16
8443                       ALLOW       192.168.0.0/16


**Telnet**
> 
user@server:~$ telnet localhost 443
Trying ::1...
Trying 127.0.0.1...
telnet: Unable to connect to remote host: Connection refused
user@server:~$


How can I fix this issue?





---

### Post by wacky_sung on 2010-07-05
What kind of upgrade have you done?Iptables / Tomcats6 / Kernal?

---

### Post by andremta on 2010-07-13
> **wacky_sung said:**
> What kind of upgrade have you done?Iptables / Tomcats6 / Kernal?

I don't know! I am using the Ubuntu's the automatic updates.

---

### Post by bodhi.zazen on 2010-07-13
Are you managing your firewall with ufw (I assume) ?

How did you set the initial iptables rules ?

You need to edit the ufw config file.

```
sudo nano /etc/ufw/before.rules
```Add a section for nat, at the very bottom of the file, BELOW the COMMIT  line (shown at the top of the edits below):

The first "COMMIT" is the end/bottom of the existing file.

> # don&#8217;t delete the &#8216;COMMIT&#8217; line or these rules won&#8217;t be processed
COMMIT

[noparse]*nat
:PREROUTING ACCEPT [0:0]
:POSTROUTING ACCEPT [0:0]
:OUTPUT ACCEPT [0:0]
-A PREROUTING -i eth0 -p tcp --dport 443 -j REDIRECT --to-port  8443[/noparse]                      

# don&#8217;t delete the &#8216;COMMIT&#8217; line or these rules won&#8217;t be processed
COMMITThen restart ufw.

---

### Post by andremta on 2010-07-20
> **bodhi.zazen said:**
> Are you managing your firewall with ufw (I assume) ?

How did you set the initial iptables rules ?

You need to edit the ufw config file.

```
sudo nano /etc/ufw/before.rules
```Add a section for nat, at the very bottom of the file, BELOW the COMMIT  line (shown at the top of the edits below):

The first "COMMIT" is the end/bottom of the existing file.

Then restart ufw.

Why I need to make that adjustment after the upgrade?

---

### Post by bodhi.zazen on 2010-07-20
> **andremta said:**
> Why I need to make that adjustment after the upgrade?

I do not know. My guess is that one or another configuration file was updated as a part of the upgrade.

My second guess would be that you did not properly configure iptables.

How did you configure your firewall before the upgrade ? If you ran only the iptables command, Ubuntu does not save those changes when you reboot. So while the rule works, you need either a script, iptables-save, or in your case to configure ufw to save your changes when your reboot.

---

