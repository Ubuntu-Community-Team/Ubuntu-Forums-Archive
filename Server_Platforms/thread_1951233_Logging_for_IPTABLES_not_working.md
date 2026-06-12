---
title: "Logging for IPTABLES not working?"
date: 2012-04-02
forum: Server Platforms
---

### Post by BorisTheMidget on 2012-04-02
Hi Folks,

i need a little bit of help. I've switched on IPTABLES (dropping input connections by default) on my ubuntu install and i was having trouble with trying to identify why my crashplan client wasnt working.

When tailed the /var/log/messages file, i'm not seeing anything getting logged there.

Could i politely ask for some guidance on working through why the logging is busted for iptables? I'm guessing it could be something busted further down in my ubuntu install :(

Below is how i have logging setup on iptables:

thanks,

-boris

[FONT=Courier New]root@bridget:/var/www# iptables -L
Chain INPUT (policy ACCEPT)
target     prot opt source               destination         
ACCEPT     all  --  X.Y.0.0/16           anywhere            
ACCEPT     all  --  W.X.Y.Z              anywhere            
ACCEPT     tcp  --  anywhere             anywhere            tcp dpt:ssh 
ACCEPT     tcp  --  anywhere             anywhere            tcp dpt:www 
ACCEPT     tcp  --  anywhere             anywhere            tcp dpt:https 
LOG        all  --  anywhere             anywhere            LOG level warning 

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination  [/FONT]

---

### Post by Doug S on 2012-04-02
Your INPUT chain default policy is ACCEPT, not DROP as your text suggested it would be. Set the policy with:```
sudo iptables -P INPUT DROP
```
 
I would suggest to add some unique prefix to your log statement, as it will make it easier to find or extract information later on. Example:```
sudo iptables -A INPUT -j LOG --log-prefix "ICATCH:" --log-level warning
```
 
Before going off and looking into why you couldn't find any log entries, my suggestion is to know for certain that there should have been some entries. By looking at the packet counters, you will know for sure.```
sudo ipables -v -x -n -L
``` And yes, by default the entries should be in /var/log/messages, but also look in /var/log/kern.log and /var/log/syslog

---

### Post by dharmavir on 2012-04-03
> **BorisTheMidget said:**
> Hi Folks,

i need a little bit of help. I've switched on IPTABLES (dropping input connections by default) on my ubuntu install and i was having trouble with trying to identify why my crashplan client wasnt working.

When tailed the /var/log/messages file, i'm not seeing anything getting logged there.

Could i politely ask for some guidance on working through why the logging is busted for iptables? I'm guessing it could be something busted further down in my ubuntu install :(

Below is how i have logging setup on iptables:

thanks,

-boris

[FONT=Courier New]root@bridget:/var/www# iptables -L
Chain INPUT (policy ACCEPT)
target     prot opt source               destination         
ACCEPT     all  --  X.Y.0.0/16           anywhere            
ACCEPT     all  --  W.X.Y.Z              anywhere            
ACCEPT     tcp  --  anywhere             anywhere            tcp dpt:ssh 
ACCEPT     tcp  --  anywhere             anywhere            tcp dpt:www 
ACCEPT     tcp  --  anywhere             anywhere            tcp dpt:https 
LOG        all  --  anywhere             anywhere            LOG level warning 

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination  [/FONT]

You should try ufw (Uncomplicated Firewall) which is simpler way of managing iptable rules. 
[https://wiki.ubuntu.com/UncomplicatedFirewall](https://wiki.ubuntu.com/UncomplicatedFirewall)
Also with ufw you can simply enable logging and I think that should serve your purpose.
 $ sudo ufw logging on

I hope this helps..!

---

### Post by BorisTheMidget on 2012-04-07
HI guys, turns out it was much more complicated in the end. My dependencies were hosed and killed the logging daemon.

but got it all fixed up.

the UCF app is pretty good! thanks for tip!

---

### Post by Vishal Agarwal on 2012-04-07
infect the log rules should be at the top of the rule that needs to be logged in log file.

---

