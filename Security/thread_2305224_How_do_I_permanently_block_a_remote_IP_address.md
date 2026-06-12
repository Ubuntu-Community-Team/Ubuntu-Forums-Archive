---
title: "How do I permanently block a remote IP address?"
date: 2015-12-03
forum: Security
---

### Post by yoshii on 2015-12-03
How do I permanently block a remote IP address?

I have been using a network traffic monitor to look at some suspicious network activity and I found an IP from an entry.  
I ran a WHOIS on the IP address and it shows a system administrator from Mumbai, India:  1.187.0.0

I live in the USA and I don't use any softwares, services, or programs from India.  
I don't know anybody in India, and I don't go to Indian websites.  
Therefore, I am OK with doing an IP block of the entire country of India if somebody knows how.  

But my main question is how do I block any IP address in Xubuntu or Ubuntu Studio v14.04.3 ?  

I really would like to do this because the number of processes logging in from the remote address is kind of high.  
It seems to start whenever I run any web browser program, Firefox or Chrome.  

I tried running GUFW, but it's too complicated for me.  I don't understand the syntax of IPtables.  

Here's the WHOIS info about the attacking machine:  

$ whois 1.187.0.0
% [whois.apnic.net]
% Whois data copyright terms    [http://www.apnic.net/db/dbcopyright.html](http://www.apnic.net/db/dbcopyright.html)

% Information related to '1.187.0.0 - 1.187.255.255'

inetnum:        1.187.0.0 - 1.187.255.255
netname:        ICL-NET-IN
descr:          Idea Cellular Limited
country:        IN
admin-c:        RC1132-AP
tech-c:         ICLn1-AP
status:         ALLOCATED PORTABLE
mnt-by:         MAINT-IN-IRINN
mnt-lower:      MAINT-ICL-NET-IN
mnt-routes:     MAINT-ICL-NET-IN
mnt-irt:        IRT-ICL-NET-IN
changed:        [email]hm-changed@apnic.net[/email] 20130618
source:         APNIC

irt:            IRT-ICL-NET-IN
address:        5th Floor, Windsor Bldg, Off: CST Road, Kalina, Near : Vidya Nagari, Santacruz (East), Mumbai - 400
e-mail:         [email]m.satyanarayanan@idea.adityabirla.com[/email]
abuse-mailbox:  [email]m.satyanarayanan@idea.adityabirla.com[/email]
admin-c:        ICLn1-AP
tech-c:         ICLn1-AP
mnt-by:         MAINT-ICL-NET-IN
auth:           # Filtered
changed:        [email]hm-changed@apnic.net[/email] 20130904
source:         APNIC

role:           IDEA CELLULAR LIMITED - network administrator
address:        5th Floor, Windsor Bldg, Off: CST Road, Kalina, Near : Vidya Nagari, Santacruz (East), Mumbai - 400
country:        IN
phone:          +912266820311
fax-no:         +912266820499
e-mail:         [email]dwarika.prasad@idea.adityabirla.com[/email]
admin-c:        RC1132-AP
tech-c:         RC1132-AP
nic-hdl:        ICLn1-AP
mnt-by:         MAINT-ICL-NET-IN
changed:        [email]hm-changed@apnic.net[/email] 20080718
changed:        [email]hm-changed@apnic.net[/email] 20080718
source:         APNIC

person:         Ramachandran C
address:        Idea Cellular Limited
address:        5th Floor, Windsor Building
address:        Off CST Road
address:        Kalina, Santacruz (East)
address:        Mumbai 400 098
country:        IN
phone:          +91 9891005959
e-mail:         [email]c.ramachandran@idea.adityabirla.com[/email]
nic-hdl:        RC1132-AP
mnt-by:         MAINT-ICL-NET-IN
changed:        [email]c.ramachandran@idea.adityabirla.com[/email] 20150420
source:         APNIC

% Information related to '1.187.0.0/19AS45271'

route:          1.187.0.0/19
descr:          Idea Cellular Limited
origin:         AS45271
country:        IN
mnt-lower:      MAINT-ICL-NET-IN
mnt-routes:     MAINT-ICL-NET-IN
mnt-by:         MAINT-ICL-NET-IN
changed:        [email]m.satyanarayanan@idea.adityabirla.com[/email] 20130930
source:         APNIC

% Information related to '1.187.0.0/19AS45271'

route:          1.187.0.0/19
descr:          Idea Cellular Limited
origin:         AS45271
country:        IN
mnt-lower:      MAINT-IN-IRINN
mnt-routes:     MAINT-IN-IRINN
mnt-by:         MAINT-IN-IRINN
changed:        [email]m.satyanarayanan@idea.adityabirla.com[/email] 20130930
source:         IRINN

% This query was served by the APNIC Whois Service version 1.69.1-APNICv1r0 (UNDEFINED)

---

### Post by SeijiSensei on 2015-12-03
Run this command:

```
sudo iptables -A INPUT -s 1.187.0.0/16 -j REJECT
```

You can add it to /etc/rc.local so it runs at every reboot.

This command adds  (-A) a rule to the iptables INPUT chain that REJECTs everything arriving with a source address (-s) in 1.187.0.0/16.

---

### Post by yoshii on 2015-12-05
thanks!  is the /16 at the end for port 16?

---

### Post by matt_symes on 2015-12-05
Hi

> **yoshi2 said:**
> thanks!  is the /16 at the end for port 16?

The /16 is the subnet. It will block all incoming IP traffic from that range of IP address encompassed by that subnet.

Kind regards

---

### Post by SeijiSensei on 2015-12-05
[https://www.digitalocean.com/community/tutorials/understanding-ip-addresses-subnets-and-cidr-notation-for-networking](https://www.digitalocean.com/community/tutorials/understanding-ip-addresses-subnets-and-cidr-notation-for-networking)

For example, the subnet 10.10.0.0/16 includes all addresses between 10.10.0.0 through 10.10.255.255.  A standard "class-C" subnet is something like 192.168.1.0/24 which covers 192.168.1.0 through 192.168.1.255.

---

### Post by yoshii on 2015-12-05
Hey thanks so much.  I think the IP got successfully blocked.

---

