---
title: "iptables =&gt; &quot;ip_conntrack_ftp&quot; and changing default port ftp (21) in proftpd"
date: 2011-11-09
forum: Server Platforms
---

### Post by dragonetti on 2011-11-09
This is driving me crazy I really really hope someone can help me out.
I had proftpd running and working (with the default port 21).
But now I want to use IPTABLES in combination with a different FTP port.
 
I read that "ip_conntrack_ftp" is essential for this? Is that correct?
 
 
 

I have the following
[LIST]
[*]ip_conntrack_ftp , modprobe ip_conntrack and ip_nat_ftp
I added these modules by in my "/etc/modules" file (1 module per line) and rebooted my UBUNTU VPS
[*]My iptables looks like this: [http://vpsbible.com/security/harden-ssh-create-firewall/](http://vpsbible.com/security/harden-ssh-create-firewall/)
```

*filter
#  Allows all loopback (lo0) traffic and drop all traffic to 127/8 that doesn't use lo0
-A INPUT -i lo -j ACCEPT
-A INPUT ! -i lo -d 127.0.0.0/8 -j REJECT
#  Accepts all established inbound connections
-A INPUT -m state --state ESTABLISHED,RELATED -j ACCEPT
#  Allows all outbound traffic
#  You can modify this to only allow certain traffic
-A OUTPUT -j ACCEPT
# Allows HTTP and HTTPS connections from anywhere (the normal ports for websites)
-A INPUT -p tcp --dport 80 -j ACCEPT
-A INPUT -p tcp --dport 443 -j ACCEPT
#  Allows SSH connections
# THE -dport NUMBER IS THE SAME ONE YOU SET UP IN THE SSHD_CONFIG FILE
-A INPUT -p tcp -m state --state NEW --dport 30000 -j ACCEPT
# Allow ping
-A INPUT -p icmp -m icmp --icmp-type 8 -j ACCEPT
# log iptables denied calls
-A INPUT -m limit --limit 5/min -j LOG --log-prefix "iptables denied: " --log-level 7
# Reject all other inbound - default deny unless explicitly allowed policy
-A INPUT -j REJECT
-A FORWARD -j REJECT
COMMIT

```
I added one extra rule (don't mind the below port number, I used another valid one)
```
 
-A INPUT -p tcp --dport 12345 -j ACCEPT

```
In my proftpd configuration file I have correctly changed the default port from 21 to 12345.
[*]My "/etc/network/interfaces" has the correct ipatables file: "pre-up iptables-restore < /etc/iptables.up.rules"
[/LIST]I seem to connect to my server to a certain degree but when the server connection procedure hits the following procedure
```
 
"Enerting passive mode" , "Get directory"

```
 
I get the below error
 
```
 
"get directory"
"500 Illegal port command"
"PORT command failed"

```
 
Because of the "500 Illegal port command" I tried several portnumbers e.g 843 , 6543, 50505 none of them working.
 
(I tried passive and active way in total commander I also tried in winscp but I also get errors there)
 
If I change back the default port to 21 (in the proftpd configuration file) I can not connect, which makes sense, because I havent made an exception in my firewall.
So if I add the port 21 in my iptables (see below) I can can connect AND upload/download files.
```
 
-A INPUT -p tcp --dport 21 -j ACCEPT

```
What am I missing? What am I doing wrong?
 
Thank you!!!!!

---

### Post by Dangertux on 2011-11-09
You have to state match -m conntrack --ctstate NEW,RELATED,ESTABLISHED if you want to use a dport other than 21.

so the rule would look like this

```

iptables -A INPUT -p tcp --sport 1024:65535 --dport 211 -m conntrack --ctstate NEW,RELATED,ESTABLISHED -j ACCEPT

```Where port 211 is the new FTP port.

Otherwise connection tracking will fail.

Hope this helps.

---

### Post by dragonetti on 2011-11-10
@Dangertux
 
Thanks for the info!
It still doesn't work, but at least I know that, that line must be added in my IPTABLES.
 
I still can't figure it though, I read somewhere that I have to add:
 
```

options nf_conntrack_ftp ports=21,3000

```
 
In a configuration file, but I do not know where to add the above.
My VPS provider also stated they don't filter anything so I should be able to ftp on any port.
 
edit:
 
 
 

It's working now!!:
[LIST]
[*]make sure your ftp server (proftpd, vsftp , ...) has the default port changed to the **new** port
[*]make sure you have a correct and working IPTABLES
[*]make sure that the "conntrack" modules are loaded (to load conntrack modules use "modprobe ip_conntrack_ftp" in terminal, and edit "/etc/rc.local" and add on 1 new line "modprobe ip_conntrack_ftp") the following modules **may** also be needed: 
ip_tables, iptable_filter, ip_conntrack , ip_conntrack_ftp, ip_conntrack_irc, iptable_nat, ip_nat_ftp, ip_nat_irc.
(to see what "ftp" modules are loaded use in terminal: "lsmod | grep ftp")
Maybe you don't need all the mentioned modules or the "lsmod | grep ftp" may not be the best way to find out which ftp modules are loaded, but it's a start i guess...

[/LIST]Then:
 
For ubuntu 10.04 LTS
You have create a file called "conntrack.conf" (any name will do, but it has to end with .conf and it is to be clear for you that it's a conntrack file, that's why the chosen name conntrack.conf). Add to the "conntrack.conf"
 
replace the "12345" with your new custom port
```

options ip_conntrack_ftp ports=21,12345

```
 
 
Put the "conntrack.conf" file in "/etc/modeprobe.d" 
 
Reboot
 
Make sure your ftp client (totalcommander, filezilla, ws_ftp, winscp...) uses the NEW ftp port and you should be able to connect with the NEW port!!!
 
Thanks @ linux community ... I'd never ever would have come this far with help!!!!!

---

