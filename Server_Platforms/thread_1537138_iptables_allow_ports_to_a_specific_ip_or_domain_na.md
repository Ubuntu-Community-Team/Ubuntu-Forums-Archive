---
title: "iptables allow ports to a specific ip or domain name"
date: 2010-07-23
forum: Server Platforms
---

### Post by Thyagaraj on 2010-07-23
How to configure iptables to allow only 22,80,3306 ports for only a dynamic public ip/dyn dns domain name on a ubuntu server?


Thank you all!

---

### Post by cdenley on 2010-07-23
Iptables only filters by IP address. If it had to resolve hostnames every time it processes a packet, this would be horribly inefficient. I think the only way to accomplish this would be to update your iptables rules every time dynamic IP changes. Also, I'm not sure how safe it is to connect to a mysql database over the internet.

---

### Post by Thyagaraj on 2010-07-24
Thanks a lot denley!

I want to drop all incoming traffic & want to allow only ssh from a specific ip. Others should not connect via ssh.

Please need step by step guide...

---

### Post by kevinthecomputerguy on 2010-07-24
Your talking about source IP address's, and IPtables can totally do that.
Webmin makes it very easy. See step by step guide at [http://woodel.com](http://woodel.com)
 
You will probably be most interested in page 5. (if you already have webmin)
 
When you make a rule, just fill out the first box that says "source address"
works awesome, i use it everyday.
-Kev

---

### Post by YesWeCan on 2010-07-24
starting with a blank iptables (no rules yet)

sudo iptables -A INPUT -i lo -j ACCEPT 
sudo iptables -A INPUT -m conntrack --ctstate RELATED,ESTABLISHED -j ACCEPT
sudo iptables -A INPUT -s a.b.c.d -p tcp -m tcp --dport 22 -j ACCEPT
sudo iptables -A INPUT -j DROP

where a.b.c.d is the ip address of your ssh client

---

### Post by Thyagaraj on 2010-07-25
Thanks a lot to both [kevinthecomputerguy]("http://ubuntuforums.org/member.php?u=1013263") , YesWeCan and denley

Actually my office has dynamic public ip address and dhcp is configured on the internet modem and all computers are assigned in the network 192.168.2.0.

They purchased some ubuntu clouds, each has static public ip addresses. I'm asked to configure iptables only to allow my office network(dynamic public ip) to SSH to clouds.

If I use the ip table rule "iptables -A INPUT -s <public-ip> -p tcp -m tcp --dport 22 -j ACCEPT", I could not access my clouds via ssh if my dynamic public ip changes and requires restarting clouds to reset iptables. 

So I registered with dyndns and now I've a domain name "mycompany.dyndns.org" for my public ip. It is resolving fine ( checked 'nslookup mycompany.dyndns.org' but if I type 'nslookup <public-ip> it resolves to my airtel broadband domain).

I used the following iptables rules on my clouds

1 :INPUT DROP [598:41912]
2 :FORWARD ACCEPT [0:0]
3 :OUTPUT ACCEPT [456:35354]
4 -A INPUT -i lo -j ACCEPT
5 -A INPUT -p tcp -m tcp --dport 22 -j ACCEPT
6 -A INPUT -s mycompany.dyndns.org -p tcp -m tcp --dport 22 -j ACCEPT
7 -A INPUT -m state --state RELATED,ESTABLISHED -j ACCEPT

If I remove line no:5 I could not ssh to my clouds and will ask to restart my clouds to reset ip tables
I don't know the reason why I couldn't connect with my dyndns domain name.

I could not able to resolve/meet this requirement since I joined as sys admin. And I'm even asked to grant mysql permissions to dyndns domain name instead of dynamicall changing public ip. Lot of pressure on me

Please need help from you all.. and thank you all for spending your time for me.

---

### Post by koenn on 2010-07-25
if you want rules with hostnames to work, you also have to allow DNS, so the names can be resolved to addresses

---

### Post by YorYor on 2010-07-25
A better solution would be to:
1. add to /etc/hosts.allow
```
sshd: mycompany.dyndns.org
```
2. add to /etc/hosts.deny
```
sshd: ALL
```

Would be slow because of lookups, but should work fine.
I would also suggest adding to /etc/hosts.allow and allowing SSH from all other static IP hosts.
This gives you a "backdoor" to access one cloud node from another node in case one of them has a bad DNS cache for your dyndns name.

---

### Post by spynappels on 2010-07-25
You could also look at placing the cloud instances on a VPN, and using their VPN address for SSH access and denying all ssh on the eth0 interface. You can even filter SSH to only be allowed from the VPN IP address you will be working from, which you can set as static also. No messing about with DNS or DynDNS URLs then.

---

### Post by kevinthecomputerguy on 2010-07-25
Thyagaraj-
 
Try at the least these settings. Some of these other replies are good as well. 
 
The bottom two are what you are interested in.
 
 
The first one allows a hostname, the second one allows a network, like the public IP
of your office or small buisness (assuming you have a need for "that many" public IP's)
 
#-------------------------------------------------------------------
# 
:FORWARD DROP [0:0]
:INPUT DROP [0:0]
:OUTPUT ACCEPT [0:0]
# Loopback
-A INPUT -p tcp -m tcp -i lo -j ACCEPT
 
# in and out if established eth0
-A INPUT -m state -i eth0 --state ESTABLISHED,RELATED -j ACCEPT
 
# 22 incoming eth0 allowed hostname
-A INPUT -p tcp -m tcp -m multiport -s example.dyndns.com -i eth0 --ports 22 -j ACCEPT
 
 
# 22 incoming eth0 allowed network 7.7.7.xxx
-A INPUT -p tcp -m tcp -m multiport -s 7.7.7.0/24 -i eth0 --ports 22 -j ACCEPT

---

### Post by cdenley on 2010-07-26
> **kevinthecomputerguy said:**
> 
# 22 incoming eth0 allowed hostname
-A INPUT -p tcp -m tcp -m multiport -s example.dyndns.com -i eth0 --ports 22 -j ACCEPT

I'm pretty sure the hostname would be resolved when the hostname is added. If the dynamic IP changes after the rule is added, you will be allowing the wrong IP.

---

### Post by Thyagaraj on 2010-07-26
Thank you all!

Yes iptables are not updated when the ip changes. I just tried allowing webmin port and mysql ports only for my dnydns domain. webmin worked but mysql doesn't. I thought I dont want to take risk trying ssh in iptables. If iptables expires we could not connect.

---

### Post by kevinthecomputerguy on 2010-07-27
[FONT=Calibri][SIZE=3]I&#8217;m going to look deeper into this, I was able to watch IPtables not update yesterday on a test bank at home. But I use hostnames all the time in IPtables without issue. Weird. [/SIZE][/FONT]
[FONT=Calibri][SIZE=3]I wonder if the name resolution is updated because my servers all talk to each other every day, over a scheduled ssh offsite backup task. I guess it&#8217;s possible the IP addresses haven&#8217;t changed, but it&#8217;s been years, and 6 networks involved. Well, always have a backdoor in :- ) and I will let you guys know if that backup job is updating the hostname resolution(s)[/SIZE][/FONT]
[FONT=Calibri][SIZE=3]Give me a few days[/SIZE][/FONT]
[FONT=Calibri][SIZE=3]-Kev[/SIZE][/FONT]

---

### Post by cdenley on 2010-07-27
Don't change the font size. It is really annoying. Also, as I already explained, when you refer to a hostname while using the iptables command, the hostname is resolved before the rule is created. There are no iptables rules with hostnames, only IP's.

---

### Post by kevinthecomputerguy on 2010-07-27
[FONT=Calibri][SIZE=3]cdenley-[/SIZE][/FONT]
[FONT=Calibri][SIZE=3]One: Are you talking to me? I didn&#8217;t change any font size.[/SIZE][/FONT]
[FONT=Calibri][SIZE=3]Two: I&#8217;m looking at a rule right now that has a hostname in the code. You may be right in the end, but you&#8217;re making it sound like it is resolved already in the rule during creation, that would not be accurate.[/SIZE][/FONT]
[FONT=Calibri][SIZE=3]-Kevin[/SIZE][/FONT]

---

### Post by cdenley on 2010-07-27
> **kevinthecomputerguy said:**
> [FONT=Calibri][SIZE=3]cdenley-[/SIZE][/FONT]
[FONT=Calibri][SIZE=3]One: Are you talking to me? I didn&#8217;t change any font size.[/SIZE][/FONT]
[FONT=Calibri][SIZE=3]Two: I&#8217;m looking at a rule right now that has a hostname in the code. You may be right in the end, but you&#8217;re making it sound like it is resolved already in the rule during creation, that would not be accurate.[/SIZE][/FONT]
[FONT=Calibri][SIZE=3]-Kevin[/SIZE][/FONT]

1. Your font is size 3.
[NOPARSE]
[FONT=Calibri][SIZE=3]One: Are you talking to me? I didn&#8217;t change any font size.[/SIZE][/FONT]
[/NOPARSE]

2. How are you looking at the rule? The iptables command attempts to resolve all IP's to hostnames when displaying rules regardless of whether it was originally given as an IP or hostname, unless the "-n" option is used. The source or destination address is always stored as an IP, not a hostname.
```

cdenley@ubuntu:~$ sudo iptables -A INPUT -p tcp -d ubuntu.com -j ACCEPT
cdenley@ubuntu:~$ sudo iptables -A INPUT -p tcp -d 91.189.94.156 -j ACCEPT
cdenley@ubuntu:~$ sudo iptables -L INPUT
Chain INPUT (policy ACCEPT)
target     prot opt source               destination         
ACCEPT     tcp  --  anywhere             vostok.canonical.com 
ACCEPT     tcp  --  anywhere             vostok.canonical.com 
cdenley@ubuntu:~$ sudo iptables -n -L INPUT
Chain INPUT (policy ACCEPT)
target     prot opt source               destination         
ACCEPT     tcp  --  0.0.0.0/0            91.189.94.156       
ACCEPT     tcp  --  0.0.0.0/0            91.189.94.156

```

---

### Post by kevinthecomputerguy on 2010-07-27
[FONT=Calibri][SIZE=3]I didn&#8217;t change any font size, so I don&#8217;t know what else you want me to say. I am replying from a blackberry, and the fonts all looks the same to me. [/SIZE][/FONT]
[FONT=Calibri][SIZE=3]I&#8217;m viewing my rule(s)  from /etc/iptables.up.rules[/SIZE][/FONT]
[FONT=Calibri][SIZE=3]Which is loaded every time the system starts, and the hostname is there,  just how I typed it during creation.[/SIZE][/FONT]
[FONT=Calibri][SIZE=3]But you&#8217;re going to wind up being right, as I saw this happen yesterday in a small test. And your last reply is pretty damn convincing  too :- )[/SIZE][/FONT]

---

### Post by cdenley on 2010-07-27
> **kevinthecomputerguy said:**
> 
[FONT=Calibri][SIZE=3]I’m viewing my rule(s)  from /etc/iptables.up.rules[/SIZE][/FONT]
[FONT=Calibri][SIZE=3]Which is loaded every time the system starts, and the hostname is there,  just how I typed it during creation.[/SIZE][/FONT]

Yes, and as soon as those rules are loaded by iptables, any hostnames are resolved to IP's. That file you created does not indicate how iptables references destination and source addresses after the rules are loaded.

---

### Post by kevinthecomputerguy on 2010-07-27
That file is read at startup. So a Reboot would load the rules again and would re-resolve the right name. That must be why it appears to be working. A few reboots teamed with IP addresses that hardly ever change.

---

### Post by kevinthecomputerguy on 2010-07-27
[FONT=Calibri][SIZE=3]You guys are right, it is totally IP based. Above and beyond a scheduled reboot, or a scheduled flushing and reloading of the rules (not a good idea) I can&#8217;t think of a changing IP fix. Unless you can get away with 7.7.7.xxx (7.7.7.0/24) but you&#8217;re probably not ever going to be in that sweet of a scenario.[/SIZE][/FONT]

---

### Post by Thyagaraj on 2010-07-28
Hey guys somehow it is made to work by my HR & Technical coordinator. I felt bad.

ports are allowed only to my dyndns domain name, even mysql connects and a script is used to update iptables ever 5min as the public ip changes. I did not try with ssh, it will also work.

If it could be useful for any one I'll post it.

---

### Post by kevinthecomputerguy on 2010-07-28
Totally post it. (thanks!)
Its scary to reload iptables in a cron job, You risk being exposed during and after (if it fails) i would love to see their approach. But all knowledge is power, lets see it.
thanks again

---

### Post by cdenley on 2010-07-29
> **kevinthecomputerguy said:**
> Totally post it. (thanks!)
Its scary to reload iptables in a cron job, You risk being exposed during and after (if it fails) i would love to see their approach. But all knowledge is power, lets see it.
thanks again

I have an iptables script which re-writes the rules by piping input to the "iptables-restore" command. No changes take effect until you use "COMMIT", I think. Something like this:
```

#!/usr/bin/env python
import subprocess,socket

whitelist=['mydomain1.com','mydomain2.com','mydomain3.com']

p=subprocess.Popen(["/sbin/iptables-restore"],stdin=subprocess.PIPE)
rules="*filter\n"
rules+=":INPUT DROP [0:0]\n"
rules+=":FORWARD ACCEPT [0:0]\n"
rules+=":OUTPUT ACCEPT [0:0]\n"
rules+="-A INPUT -m state --state NEW,ESTABLISHED -j ACCEPT\n"
for host in whitelist:
	try:
		hostname,aliaslist,ipaddrlist=socket.gethostbyname_ex(host)
		for ip in ipaddrlist:
			rules+="-A INPUT -s "+ip+"/32 -j ACCEPT\n"
	except socket.gaierror:
		print "failed to resolve "+host
rules+="COMMIT\n"
p.stdin.write(rules)
p.stdin.close()

```

---

### Post by Thyagaraj on 2010-07-29
Hai kevin, denley

Yes but its something different script and it doesn't even requires any modification . I'll post here clearly on saturday and whenever any one post, they will create boxes for the code, how to create that box like you did?

---

### Post by cdenley on 2010-07-30
> **Thyagaraj said:**
> how to create that box like you did?
[NOPARSE]```

code goes here

```[/NOPARSE]

---

### Post by Thyagaraj on 2010-07-30
Hey guys here it's the iptables rules to allow only specific ports to a  dyndns domain name or to a specific ips.

First of all create an  account in [http://www.dyndns.org/](http://www.dyndns.org/) signing up with new account name &  password and choose the domain name. Let the domain name be  "mycompany.dyndns.com"
After registering check whether it resolves to  your dynamic public ip address using
#nslookup mycompany.dyndns.org

The  iptable rules are know to everyone, to me following iptable rules  worked.

I don't know the proper way of applying iptable rules,  but only the mandatory things(any one can suggest me after this). Copy  and paste the below code to /etc/iptables.rules

In the following  iptables 22 and 80 is allowed for all and again 22, 21, webmin(10000),  mysql(3306) are allowed only for dyndns domain name  "mycompany.dyndns.com" and change this domain name to your own domain  name
You can remove the rule "-A INPUT -p tcp -m tcp --dport 22 -j  ACCEPT" and ssh is only allowed to dyndns domain name. I removed it,  it's working.

#vim /etc/iptables.rules
copy the below and  paste in this file

*filter
:INPUT DROP [0:0]
:FORWARD  ACCEPT [0:0]
:OUTPUT ACCEPT [0:0]
-A INPUT -i lo -j ACCEPT
-A  INPUT -m state -i eth0 --state ESTABLISHED,RELATED -j ACCEPT
-A INPUT  -p tcp -m tcp --dport 22 -j ACCEPT
-A INPUT -p tcp -m tcp --dport 80  -j ACCEPT
-A INPUT -s mycompany.dyndns.com -p tcp -m tcp --dport 22  -j ACCEPT
-A INPUT -s mycompany.dyndns.com -p tcp -m tcp --dport 21  -j ACCEPT
-A INPUT -s mycompany.dyndns.com -p tcp -m tcp --dport  10000 -j ACCEPT
-A INPUT -s mycompany.dyndns.com -p tcp -m tcp  --dport 3306 -j ACCEPT
COMMIT

#chmod 755 /etc/iptables.rules
#iptables-restore  < /etc/iptables.rules
check the rules applied by
#iptables -L

This  is for only Mysql:

But now you could not connect to mysql even  after allowing dyndns domain name if '%' is removed in mysql.
Yes '%'  is to allow all to connect mysql server, only then you are allowed to  connect via dyndns domain name apart from ip and iptable rules will help  blocking all except the domain name you specified/allowed.

If  you have GUI tools "Mysql Administrator" and "Mysql Query Browser"  installed, navigate to something like open Mysql administrator
 >  User administartion
> select the user
> right click the  user, select add host
> select the 3rd option which may specify ip  or hostname, just enter %, ok
Now under that user, select the '%'  added and at the right side select the tab "schema privileges' apply  permissions selecting the databases.

Similarly add 'localhost'  how you added '%' and give schema privileges and remove if any ip  address/hostname under that user---"Be sure to remove "right click  >remove host" NOT "remove user"
make sure only % and localhost is  present under that user
                                                       (or)

Instead of gui you can do this in command line.
connect  to mysql server
#ssh username@serverip

switch to root user
#su

#mysql  -u root -p (enter mysql root password)
#GRANT ALL ON *.* TO  username@'%' IDENTIFIED BY 'userpassword';
#GRANT ALL ON *.* TO  username@'localhost' IDENTIFIED BY 'userpassword';

The follwoing  is the script needed to update iptable rules as the ip changes every  time when modem restarts.

create a file

#vim  /root/firewall-dynhosts.sh
Paste the following code as it is 


#!/bin/bash
#  filename: firewall-dynhosts.sh
#
# A script to update iptable  records for dynamic dns hosts.
# Written by: Dave Horner  ([http://dave.thehorners.com](http://dave.thehorners.com))
# Released into public domain.
#
#  Run this script in your cron table to update ips.
#
# You might  want to put all your dynamic hosts in a sep. chain.
# That way you  can easily see what dynamic hosts are trusted.
#
# create the  chain in iptables.
 /sbin/iptables -N dynamichosts
# insert the  chain into the input chain @ the head of the list.
 /sbin/iptables -I  INPUT 1 -j dynamichosts
# flush all the rules in the chain
 /sbin/iptables  -F dynamichosts

HOST=$1
HOSTFILE="/root/host-$HOST"
CHAIN="dynamichosts"   # change this to whatever chain you want.
IPTABLES="/sbin/iptables"
 
#  check to make sure we have enough args passed.
if [ "${#@}" -ne "1"  ]; then
    echo "$0 hostname"
    echo "You must supply a  hostname to update in iptables."
    exit
fi
 
# lookup host  name from dns tables
IP=`/usr/bin/dig +short $HOST | /usr/bin/tail  -n 1`
if [ "${#IP}" = "0" ]; then
    echo "Couldn't lookup  hostname for $HOST, failed."
    exit
fi
 
OLDIP=""
if [  -a $HOSTFILE ]; then
    OLDIP=`cat $HOSTFILE`
    # echo "CAT  returned: $?"
fi
 
# save off new ip.
echo $IP>$HOSTFILE
 
echo  "Updating $HOST in iptables."
if [ "${#OLDIP}" != "0" ]; then
     echo "Removing old rule ($OLDIP)"
    `$IPTABLES -D $CHAIN -s  $OLDIP/32 -j ACCEPT`
fi
echo "Inserting new rule ($IP)"
`$IPTABLES  -A $CHAIN -s $IP/32 -j ACCEPT`


save and quit the file.

#chmod  755 /root/firewall-dynhosts.sh

Create a file as follows 
#vim  /root/host-mycompany.dyndns.com
#chmod 755  /root/host-mycompany.dyndns.com
After the script executes, this file  holds the dynamic ip address. 
    

Again create a file and  this file should be included in the cron job
#vim  /root/dynamic-firewall 
paste the following code

#!/bin/bash 
#example  of using the firewall-dynhosts.... write something like this and add a  cron.d entry to run it. 
# [http://dave.thehorners.com](http://dave.thehorners.com) 

/root/firewall-dynhosts.sh  mycompany.dyndns.com

save and exit
#chmod  /root/dynamic-firewall


To add this script in Cron job :
#vim  /etc/cron.d/dyndns
edit as follows

# Run the dynamic firewall  script every 5 minutes
*/5 * * * * root /root/dynamic-firewall >  /dev/null  2>&1

save and exit
#chmod 755  /etc/cron.d/dyndns

check the log file /var/log/syslog to make sure if it is running at every 5 minutes

That's it!

If your modem/router  supports ddns(dynamic dns/dyndns) option, you would have to add your  dyndns domain name in the 'hostname' field and should supply dyndns  account name and password to properly resolve your domain name to your  dynamically changing public ip


Let me know guys if any  suggestions, modifications, tips, tricks...

---

### Post by wltj on 2011-01-10
> **Thyagaraj said:**
> How to configure iptables to allow only 22,80,3306 ports for only a dynamic public ip/dyn dns domain name on a ubuntu server?

for ppl arriving from google searches, another option for a script that's roughly based on the "dave.thehorners.com" script shown above is at [http://ubuntuforums.org/showthread.php?t=1655443]("http://ubuntuforums.org/showthread.php?t=1655443") 

to open those ports in quote for dynamic host (eg host.dyndns.org), run
```
bash dyn-iptables.sh -H host.dyndns.org -P 22,80,3306
```

---

