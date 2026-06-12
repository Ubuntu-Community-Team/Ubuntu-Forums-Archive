---
title: "iptables &amp; Linux - How is it being handle in the real world?"
date: 2015-06-30
forum: Security
---

### Post by Drenriza on 2015-06-30
Hi all

I am currently using iptables on a raspberry pi with two rj-45 interfaces (eth0 and eth1) with an adapter on one usb port,
so data can traverse through the device instead of in and out of the same interface.

My question in this regard is, what is done in the real world when we are talking firewalls and linux.
Does big enterprise corporations sit and hand type their firewall rules in iptables or do they use a wrapper?

Are their some Linux distro's better at being used as a firewall instead of Debian / Ubuntu?

I am no stranger to access security (what do we call it?) with ACL's on Cisco devices and Cisco Pix's.
But i am not that into iptables.

Its a quite open question.

Hope you all will send me feedback on the subject.

Thanks on advance.
Kind regards

---

### Post by SeijiSensei on 2015-06-30
I use a lengthy custom bash script to generate the rules.  There are also third-party iptables scripts if you search the Internet.

Iptables is supported in the Linux kernel itself.  What distro is being used really doesn't matter.

Most large installations are using Ciscos or similar routers, not Linux boxes running iptables, though they certainly could use those if they chose.  "Nobody ever got fired for using [s]IBM[/s] Cisco."

---

### Post by slickymaster on 2015-06-30
*Moved to the ***Security*** sub-forum*

---

### Post by Drenriza on 2015-06-30
> **SeijiSensei said:**
> I use a lengthy custom bash script to generate the rules.  There are also third-party iptables scripts if you search the Internet.

Thanks for the reply Seiji!

Can i ask what your script does and if its seen as a wrapper.
Do you for example say

***"allow ssh from eth1 to eth0 and back"***

And the script implements the rules for you based of that, or how does it work?

---

### Post by SeijiSensei on 2015-07-02
Mostly it consists of iterating over lists of IP addresses and specifying rules for them.
```

for a in $(cat /path/to/some/address/list) 
do
   /sbin/iptables -A INPUT -s $a  -j REJECT
done

```
For one client, we have a large number of such lists.  For instance, the PR staff can visit Facebook, but not ordinary office staff.

I also run a script overnight that compiles the number of apparent spam emails sent from each remote IP address and adds iptables rules blocking access by the more egregious spammers.  

All of these scripts use the iptables commands themselves without any wrapper.

---

### Post by CharlesA on 2015-07-02
I do what Seiji does on my home server, but for production, I use [CSF]("http://www.configserver.com/cp/csf.html") to manage my firewall rules.

---

### Post by limbenjamin on 2015-07-04
> [COLOR=#000000]Does big enterprise corporations sit and hand type their firewall rules in iptables or do they use a wrapper?[QUOTE][/COLOR][/QUOTE]

Firewalls are normally placed only are trust boundaries. Most enterprises have at most 2-3 such boundaries. e.g. 1 for VPN access, 1 for normal use and 1 for redundancy.

Therefore, there are less scalability issues compared to processes like patching which involves the majority of hosts on the network.

As mentioned earlier, shell scripts would normally suffice. If you really need to, there are a number of tools such as Puppet which can help manage iptables rules across many hosts.

---

