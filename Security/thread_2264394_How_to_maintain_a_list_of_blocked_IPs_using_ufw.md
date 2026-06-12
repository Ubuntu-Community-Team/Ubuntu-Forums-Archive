---
title: "How to maintain a list of blocked IPs using ufw"
date: 2015-02-07
forum: Security
---

### Post by shersk on 2015-02-07
I'm looking for an easy way to maintain a list of blocked IPs to be loaded by ufw. Manually writing each address into ufw, and removing when cleared, is too time-consuming. I want a text file with only the blocked IPs that gets loaded into the firewall automatically. I have searched the web for this, but can't find it. Does anyone have any idea where to put such a file and how to make ufw load it?

---

### Post by sandyd on 2015-02-07
> **shersk said:**
> I'm looking for an easy way to maintain a list of blocked IPs to be loaded by ufw. Manually writing each address into ufw, and removing when cleared, is too time-consuming. I want a text file with only the blocked IPs that gets loaded into the firewall automatically. I have searched the web for this, but can't find it. Does anyone have any idea where to put such a file and how to make ufw load it?

You can loop over ip addresses in a file (seperated by newlines) using the following format. Just replace 'echo' with the command to add the ip address to UFW
```

while read IPADDR
do
    echo "$IPADDR"
done < ipaddrlist.txt
```

Aside:

If you are looking for additional advanced blocking, check out [CSF Firewall]("http://configserver.com/cp/csf.html") (which is really a beautiful frontend to iptables). It supports blocklists, ssh brute-force detection, rate limiting/etc

---

### Post by wannabe user on 2015-02-09
You can do it with ufw if that's what you want, but maybe you can elaborate on when an IP should be cleared, as you could also automate this, e.g. if an IP should be banned for X amount of minutes.

Anyway, as said you could loop through a file, bear in mind it's a chain so to take effect you'll want to insert them at the top for example:
> 
wannabe:~$ sudo ufw deny from 1.1.1.1
Rule added
wannabe:~$ sudo ufw status
Status: active


To                         Action      From
--                         ------      ----
80/tcp                     ALLOW       Anywhere
Anywhere                   DENY        1.1.1.1
80/tcp                     ALLOW       Anywhere (v6)



The deny rule won't actually block 1.1.1.1 to port 80/tcp, you need to insert it into the top. Anyway, here's an example:
```

#!/bin/bash


if [ $UID -ne "0" ];then
        echo "Run with sudo - sudo $0"
        exit 2
fi


for IP in $(cat ./ip-ban.ls);do
        sudo /usr/sbin/ufw insert 1 deny  from $IP
done

```

You could do a lot with it, but here's a sample output from it:
> 
wannabe:~$ ./ufw-ban.sh 
Run with sudo - sudo ./ufw-ban.sh
wannabe:~$ sudo ./ufw-ban.sh 
Rule inserted
Rule inserted
Rule inserted

wannabe:~$ sudo ufw status
Status: active


To                         Action      From
--                         ------      ----
Anywhere                   DENY        3.3.3.3
Anywhere                   DENY        2.2.2.2
Anywhere                   DENY        1.1.1.1
80/tcp                     ALLOW       Anywhere
80/tcp                     ALLOW       Anywhere (v6)




You could check to see if the IP is already banned, however UFW will happily ignore with "Skipping inserting existing rule".

---

### Post by shersk on 2015-02-11
Thank you both! 

What I have now is a script based on what sandyd wrote that first removes all ufw rules, then reads each banned ip from a separat file, and finally applies the standard rules. Like this:

```
ufw --force reset
while read address; do
ufw deny from $address
done < /etc/ufw/banned-ips-list
ufw allow 22
ufw allow 25/tcp
ufw allow 80/tcp
ufw allow 443/tcp
ufw --force enable

```

It seems to work alright when I run it with sudo. I think of installing it as a cronjob. Then all I need to do is maintain the list of blocked ips, and the script will check regularly and update the rules.

A few FIXMEs: There should be added comments in the list. And I am currently blocking China, using a separate script which works with iptables directly. Since it works, I can just add the China script to startup procedures.

So far so good, but the brunt of my question was really: Isn't there a standardized way of maintaining a blocked IPs list in Ubuntu? What is the recommended way, standard location of files, cronjobs?

---

### Post by fugu2 on 2015-02-11
ufw is using iptables to do everything. iptables has an extension called "recent" which handles reading a list of ip addresses you might just be able to use. (i think this is what your talking about and ityou dont have to add in each ip address using ufw which in know can be very slow)

```
**EXCERT** man iptables-extensions
   recent
       Allows you to dynamically create a list of IP addresses and then match against that list in a few different ways.

       For example, you can create a "badguy" list out of people attempting to connect to port 139 on your firewall and then DROP all future pack&#8208;
       ets from them without considering them.
****
       Examples:

              iptables -A FORWARD -m recent --name badguy --rcheck --seconds 60 -j DROP

              iptables -A FORWARD -p tcp -i eth0 --dport 139 -m recent --name badguy --set -j DROP

       Each file in /proc/net/xt_recent/ can be read from to see the current list or written two using the following commands to modify the list:

       echo +addr >/proc/net/xt_recent/DEFAULT
              to add addr to the DEFAULT list

       echo -addr >/proc/net/xt_recent/DEFAULT
              to remove addr from the DEFAULT list

```

---

### Post by shersk on 2015-02-14
This is not user friendly. Do the files in xt_recent remain there after a reboot? I tried to create a file there as sudo, but was refused. What iptables command do I use to block all IPs in the badguy list, and lift the ban on IPs that have disappeared from the list since last?

I don't want to tinker "under the hood" of the ubuntu. I just want the standard way to place a list of IPs that are completely banned from accessing the server in any way. Now I made such a list with ufw, but I am convinced that there is a standard, prescribed way of doing it instead of trying to reinvent the wheel.

---

