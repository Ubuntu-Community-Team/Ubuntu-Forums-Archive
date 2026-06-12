---
title: "Port  forwarding help related to security"
date: 2008-10-29
forum: Security
---

### Post by ravi.786 on 2008-10-29
Hi Team,
I want to start my own website from my home server. I am using a modem and linksys wireless router WRT54GS. I logged in to router console and went to Application & gaming, there is a port forwarding option in Application section i put i.p 62.**.**.***. which i assume is static i.p. In Port range section i put 6880 to 6880. I am running my php pages on Apache webserver 2.2, whic is on ubuntu 7.x. 
Now here is my Question --> i am able to make my website public if i set port range from 443 to 443 as i have enabled SSL with weblogic and i was able to access my site using https. But if i set port range to anything else like 3434 for ex: how can someone access it? Also if i set port forwarding with 443 range is it be a security bottleneck. How can i start my website without security issues ? please help me with the complete steps to solve this issue, as i am struggling from long time.

---

### Post by Sarmacid on 2008-10-29
If you want people to be able to access your http server, you have to set up your router to forward port 80, as 443 is the default for https.

As for security on your server, I'd recommend setting up a firewall with iptables and always update apache.

---

### Post by ravi.786 on 2008-10-29
Thanks for a quick reply. So if port my apache is just listning to 443 throught virtual hosting setup and will not accept any request which comes via http or port 80. That still be a security bottle neck.

---

### Post by Sarmacid on 2008-10-29
Um, sorry but I don't understand the question :x

---

### Post by ravi.786 on 2008-10-29
Oops my My Firewall was disabled. Thanks for pointing me towards the iptable configuration.
I enabled the firewall. Here is my iptable configuration, Please let me know if this is correct configuration or i do need to change something in /etc/sysconfig/iptables files

****************************************************************
*filter
:INPUT ACCEPT [0:0]
:FORWARD ACCEPT [0:0]
:OUTPUT ACCEPT [0:0]
:RH-Firewall-1-INPUT - [0:0]
-A INPUT -j RH-Firewall-1-INPUT
-A FORWARD -j RH-Firewall-1-INPUT
-A RH-Firewall-1-INPUT -i lo -j ACCEPT
-A RH-Firewall-1-INPUT -i eth0 -j ACCEPT
-A RH-Firewall-1-INPUT -i sit0 -j ACCEPT
-A RH-Firewall-1-INPUT -p icmp --icmp-type any -j ACCEPT
-A RH-Firewall-1-INPUT -p 50 -j ACCEPT
-A RH-Firewall-1-INPUT -p 51 -j ACCEPT
-A RH-Firewall-1-INPUT -p udp --dport 5353 -d 224.0.0.251 -j ACCEPT
-A RH-Firewall-1-INPUT -p udp -m udp --dport 631 -j ACCEPT
-A RH-Firewall-1-INPUT -m state --state ESTABLISHED,RELATED -j ACCEPT
-A RH-Firewall-1-INPUT -m state --state NEW -m tcp -p tcp --dport 80 -j ACCEPT
-A RH-Firewall-1-INPUT -m state --state NEW -m tcp -p tcp --dport 443 -j ACCEPT
-A RH-Firewall-1-INPUT -m state --state NEW -m tcp -p tcp --dport 22 -j ACCEPT
-A RH-Firewall-1-INPUT -m state --state NEW -m tcp -p tcp --dport 23 -j ACCEPT
-A RH-Firewall-1-INPUT -m state --state NEW -m tcp -p tcp --dport 25 -j ACCEPT
-A RH-Firewall-1-INPUT -j REJECT --reject-with icmp-host-prohibited
COMMIT
*****************************************************************
Here is thr ouput for iptables status as well..
*****************************************************************
[root@weblogiclive ~]# /etc/init.d/iptables status
Table: filter
Chain INPUT (policy ACCEPT)
target     prot opt source               destination
RH-Firewall-1-INPUT  all  --  0.0.0.0/0            0.0.0.0/0

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination
RH-Firewall-1-INPUT  all  --  0.0.0.0/0            0.0.0.0/0

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination

Chain RH-Firewall-1-INPUT (2 references)
target     prot opt source               destination
ACCEPT     all  --  0.0.0.0/0            0.0.0.0/0
ACCEPT     all  --  0.0.0.0/0            0.0.0.0/0
ACCEPT     all  --  0.0.0.0/0            0.0.0.0/0
ACCEPT     icmp --  0.0.0.0/0            0.0.0.0/0           icmp type 255
ACCEPT     esp  --  0.0.0.0/0            0.0.0.0/0
ACCEPT     ah   --  0.0.0.0/0            0.0.0.0/0
ACCEPT     udp  --  0.0.0.0/0            224.0.0.251         udp dpt:5353
ACCEPT     udp  --  0.0.0.0/0            0.0.0.0/0           udp dpt:631
ACCEPT     all  --  0.0.0.0/0            0.0.0.0/0           state RELATED,ESTABLISHED
ACCEPT     tcp  --  0.0.0.0/0            0.0.0.0/0           state NEW tcp dpt:80
ACCEPT     tcp  --  0.0.0.0/0            0.0.0.0/0           state NEW tcp dpt:443
ACCEPT     tcp  --  0.0.0.0/0            0.0.0.0/0           state NEW tcp dpt:22
ACCEPT     tcp  --  0.0.0.0/0            0.0.0.0/0           state NEW tcp dpt:23
ACCEPT     tcp  --  0.0.0.0/0            0.0.0.0/0           state NEW tcp dpt:25
REJECT     all  --  0.0.0.0/0            0.0.0.0/0           reject-with icmp-host-prohibited

---

### Post by Sarmacid on 2008-10-29
That's not the usual way I read iptables, but you could try posting the output of
```
iptables -L
```

You can learn more about it looking at these links:
[http://ubuntuforums.org/showthread.php?t=159661&highlight=iptables+tutorial](http://ubuntuforums.org/showthread.php?t=159661&highlight=iptables+tutorial)
[https://help.ubuntu.com/community/IptablesHowTo](https://help.ubuntu.com/community/IptablesHowTo)

---

### Post by ravi.786 on 2008-10-29
Chain INPUT (policy ACCEPT)
target     prot opt source               destination
RH-Firewall-1-INPUT  all  --  anywhere             anywhere

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination
RH-Firewall-1-INPUT  all  --  anywhere             anywhere

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination

Chain RH-Firewall-1-INPUT (2 references)
target     prot opt source               destination
ACCEPT     all  --  anywhere             anywhere
ACCEPT     all  --  anywhere             anywhere
ACCEPT     all  --  anywhere             anywhere
ACCEPT     icmp --  anywhere             anywhere            icmp any
ACCEPT     ipv6-crypt--  anywhere             anywhere
ACCEPT     ipv6-auth--  anywhere             anywhere
ACCEPT     udp  --  anywhere             224.0.0.251         udp dpt:5353
ACCEPT     udp  --  anywhere             anywhere            udp dpt:ipp
ACCEPT     all  --  anywhere             anywhere            state RELATED,ESTABLISHED
ACCEPT     tcp  --  anywhere             anywhere            state NEW tcp dpt:http
ACCEPT     tcp  --  anywhere             anywhere            state NEW tcp dpt:https
ACCEPT     tcp  --  anywhere             anywhere            state NEW tcp dpt:ssh
ACCEPT     tcp  --  anywhere             anywhere            state NEW tcp dpt:telnet
ACCEPT     tcp  --  anywhere             anywhere            state NEW tcp dpt:smtp
REJECT     all  --  anywhere             anywhere            reject-with icmp-host-prohibited

---

### Post by ravi.786 on 2008-10-30
Please help me here

---

### Post by hyper_ch on 2008-10-30
are you sure you need the firewall at all?

---

### Post by Sarmacid on 2008-10-30
You have '*ACCEPT all -- anywhere anywhere*' 3 times. If you want just to take incoming connections on port 80, try this(Assuming your network interface is eth0):

```
sudo iptables -F
sudo iptables -A INPUT -i eth0 -p tcp -m tcp --dport 80 -m state --state NEW,ESTABLISHED -j ACCEPT
sudo iptables -A OUTPUT -o eth0 -p tcp -m tcp --sport 80 -m state --state ESTABLISHED -j ACCEPT
sudo iptables -P INPUT DROP
sudo iptables -P OUTPUT DROP
sudo iptables -P FORWARD DROP
```

That won't let anything else come in or out, to take down the firewall, try
```
sudo iptables -F
sudo iptables -P INPUT ACCEPT
sudo iptables -P OUTPUT ACCEPT
sudo iptables -P FORWARD ACCEPT
```

Check out the guides I posted before for more info

---

### Post by ravi.786 on 2008-10-30
Really appreciate your responce...Thanks a lot.

One more help would be really apreciated. I want to open port 443 & port 80 only. But mainly what i like to do here is when ever some one hits my website url via http will be redirected to https from the webserver configuration. 

What help i need here is .
The rule to set in iptables file that will allow both ports 80 & 443.
Also the way i can set my webserver that any request hits at port 80 will be redirected to 443.

Thanks a lot!!

---

### Post by Sarmacid on 2008-10-30
You can take the rules I made before and just change the port to 443 to allow incoming traffic through there, as for redirecting the traffic, I know it can be done, but I don't know how. [Google is your friend]("http://www.google.com")

---

### Post by ravi.786 on 2008-10-30
Thanks a lot for qucik reply.
So what i understand here is i can paste this in my /etc/sysconfig/iptables file
******************************************
sudo iptables -F
sudo iptables -A INPUT -i eth0 -p tcp -m tcp --dport 80 -m state --state NEW,ESTABLISHED -j ACCEPT
sudo iptables -P INPUT DROP
sudo iptables -P OUTPUT DROP
sudo iptables -P FORWARD DROP
********************************************
Which will enbale port 80 & http for the whole world..correct?
And no one can access to my website or machine at all if not hitting port 80..correct?
So before pasting this line can i delete the previous entries to iptables?

******************************************************
Also port forwarding from apache to hit http and redirect to https can be done by adding the following parameter in httpd.conf file
++++++++++++
RewriteEngine   on
RewriteCond     %{SERVER_PORT} ^80$
RewriteRule     ^/(.*)$ https://%{SERVER_NAME}/$1 [L,R,NC]

---

### Post by Sarmacid on 2008-10-30
> **ravi.786 said:**
> Thanks a lot for qucik reply.
So what i understand here is i can paste this in my /etc/sysconfig/iptables file

I've never worked with that file, and I don't have access to ubuntu right now, but I used [COLOR="Blue"]**[this]("https://help.ubuntu.com/community/IptablesHowTo#Configuration%20on%20startup")**[/COLOR] so the rules would load on boot.
> **ravi.786 said:**
> 
******************************************
sudo iptables -F
sudo iptables -A INPUT -i eth0 -p tcp -m tcp --dport 80 -m state --state NEW,ESTABLISHED -j ACCEPT
sudo iptables -P INPUT DROP
sudo iptables -P OUTPUT DROP
sudo iptables -P FORWARD DROP
********************************************
Which will enbale port 80 & http for the whole world..correct?
And no one can access to my website or machine at all if not hitting port 80..correct?
So before pasting this line can i delete the previous entries to iptables?

iptables -F will flush the previous rules, so no need to worry about that. This rule would enable only incoming http access, so no one would be able to see your site, since your firewall would be stopping all the responses from going out. Add```
sudo iptables -A OUTPUT -o eth0 -p tcp -m tcp --sport 80 -m state --state ESTABLISHED -j ACCEPT
```That would allow anyone to access your machine through port 80 only.

---

### Post by ravi.786 on 2008-10-30
Thanks for the help...I will try this..

---

