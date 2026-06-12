---
title: "How can I disable ping &amp; icmp requests?"
date: 2013-08-02
forum: Security
---

### Post by koda2 on 2013-08-02
Does anybody know how can I disable ping & icmp requests? like, if somebody is PINGing my IP-Address, he/she should see nothing, but I SHOULD be able to ping websites/IPs though.  Any idea how can I do this? perhaps via gufw, or ufw..or any other similiar method?  If yes, please give me the exact command to disable ping & icmp requests.

---

### Post by GwL3eNC on 2013-08-02
Hi, 

the only way i know to do this is iptables.
I allow some things, you have to set -j DENY or DROP. I have made that on my own and i'm not pro.
You have to think about it on your own.

set $fw=iptables in your script

$fw -A FORWARD -p icmp --icmp-type echo-request -m limit --limit 1/s -j ACCEPT
$fw -A INPUT -p icmp --icmp-type echo-request -m limit --limit 1/s -j ACCEPT

$fw -A INPUT -p icmp --icmp-type destination-unreachable -j ACCEPT
$fw -A INPUT -p icmp --icmp-type time-exceeded -j ACCEPT
$fw -A INPUT -p icmp --icmp-type echo-reply -j ACCEPT

$fw -A OUTPUT  -p icmp --icmp-type destination-unreachable -j ACCEPT
$fw -A OUTPUT  -p icmp --icmp-type time-exceeded -j ACCEPT
$fw -A OUTPUT  -p icmp --icmp-type echo-reply -j ACCEPT
$fw -A OUTPUT  -p icmp --icmp-type echo-request -j ACCEPT

Also you can use in newer ubuntu ufw firewall. It's simple to use as iptables. It has an gui
you can use.

---

### Post by CharlesA on 2013-08-02
> **koda2 said:**
> Does anybody know how can I disable ping & icmp requests? like, if somebody is PINGing my IP-Address, he/she should see nothing, but I SHOULD be able to ping websites/IPs though.  Any idea how can I do this? perhaps via gufw, or ufw..or any other similiar method?  If yes, please give me the exact command to disable ping & icmp requests.

Is there a reason you want to disable this? If it's because of "security" - it is stupidly easy to tell if a host is there even if it does not reply to pings.

If you really want to stop your system from sending echo replies, read here:
[http://www.cyberciti.biz/faq/howto-drop-block-all-ping-packets/](http://www.cyberciti.biz/faq/howto-drop-block-all-ping-packets/)

---

### Post by Soul-Sing on 2013-08-04
Is this because of Shields-up/GRC your asking about disabling ping?

---

### Post by raja.genupula on 2013-08-04
Its worth reading [http://serverfault.com/questions/448541/how-to-know-who-ping-my-computer](http://serverfault.com/questions/448541/how-to-know-who-ping-my-computer)

---

