---
title: "About input iptables rule"
date: 2009-05-03
forum: Security
---

### Post by satimis on 2009-05-03
Hi folks,

Ubuntu 8.04


To input a rule whether run;

$ sudo iptables -A INPUT -m state --state ESTABLISHED,RELATED -j ACCEPT

Then run;

$ sudo iptables-save > rules-saved

to save that rule ?


To display/check it;

$ sudo iptables -L
the rule will be displayed

If to remove above rule whether run;

$ sudo iptables -P INPUT DROP INPUT -m state --state ESTABLISHED,RELATED -j ACCEPT

Then run again;

$ sudo iptables-save > rules-saved

$ sudo iptables -L
the rule will disappear
???

TIA


B.R.
satimis

---

### Post by bodhi.zazen on 2009-05-03
Yes, that will work.

When you re-boot, your changes will NOT be saved or restored.

So you either need to use iptables-restore, or write a script to configure iptables or use a configuration tool , such as ufw .

Let us assume you have your firewall configured the way you like ...

iptables-save > /etc/iptables.save

Now add

iptabels-restore < /etc/iptables.save 

into /etc/rc.local and your settings will be restored, from /etc/iptables.save, on reboot.

You can make changes with iptables -A or iptables -D

Unless you save those changes (iptables-save, edit yoru script, make changes in ufw) you will lose them when your reboot.

So there are two things you are doing with those commands :

1. Configuring iptables.

2. Saving your changes.

---

