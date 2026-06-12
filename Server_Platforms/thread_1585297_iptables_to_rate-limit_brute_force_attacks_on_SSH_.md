---
title: "iptables to rate-limit brute force attacks on SSH server"
date: 2010-09-30
forum: Server Platforms
---

### Post by buntolith on 2010-09-30
I have a SSH server set up at home listening on port 22. I have hardened the server so it is pretty secure but I want to make it even safer by editing my iptables to rate-limit incoming connections and DROP false login attempts. I have tried these tutorials but I just cant get it to work:

[http://www.debian-administration.org/articles/187](http://www.debian-administration.org/articles/187)
[http://www.la-samhna.de/library/brutessh.html](http://www.la-samhna.de/library/brutessh.html)
[http://www.sollers.ca/blog/2008/iptables_recent/](http://www.sollers.ca/blog/2008/iptables_recent/)

I want the debian-administration.org tutorial to work but when I try to add the first rule in terminal:

sudo iptables -I INPUT -p tcp --dport 22 -i eth0 -m state --state NEW -m recent \ --set

I get the following:

Bad argument --set'

I am new to iptables and I'm not sure if I'm doing something wrong when I try to set it up. I'm using Ubuntu 10.04.1 LTS with iptables v1.4.4. 

Any help is much appreciated...

---

### Post by buntolith on 2010-09-30
I managed to load these rules OK:

iptables -A INPUT -p tcp --dport 22 -m state --state ESTABLISHED,RELATED -j ACCEPT

iptables -A INPUT -p tcp --dport 22 -m state --state NEW -m limit --limit 3/min --limit-burst 3 -j ACCEPT

iptables -A INPUT -p tcp --dport 22 -j DROP

from [http://serverfault.com/questions/4188/preventing-brute-force-attacks-against-ssh](http://serverfault.com/questions/4188/preventing-brute-force-attacks-against-ssh)

with this output:

Chain INPUT (policy ACCEPT)
target     prot opt source               destination         
ACCEPT     tcp  --  anywhere             anywhere            tcp dpt:ssh state RELATED,ESTABLISHED 
ACCEPT     tcp  --  anywhere             anywhere            tcp dpt:ssh state NEW limit: avg 3/min burst 3 
DROP       tcp  --  anywhere             anywhere            tcp dpt:ssh 

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination

I hope this will work. Does it seem OK?

---

### Post by KiLaHuRtZ on 2010-10-01
Check out fail2ban.

---

### Post by buntolith on 2010-10-06
Thanks, but I want to keep it more simple. As I understand you need to run another deamon when using fail to ban. Iptables are already part of the kernel.

I have tried the rules above and they work great. I have a couple of brute force attacks per day but they quickly get weeded out after 3 attempts. I can really recommend the rules I mentioned above. Here is a copy from my /var/log/auth.log showing a brute force attack on my server today. They get DROPped after 3 attempts:

Oct  6 10:51:18 kevinisha sshd[5109]: Connection from 211.241.149.126 port 38305
Oct  6 10:51:21 kevinisha sshd[5109]: User root from 211.241.149.126 not allowed because not listed in AllowUsers
Oct  6 10:51:21 kevinisha sshd[5112]: Connection from 211.241.149.126 port 38420
Oct  6 10:51:25 kevinisha sshd[5112]: User root from 211.241.149.126 not allowed because not listed in AllowUsers
Oct  6 10:51:26 kevinisha sshd[5116]: Connection from 211.241.149.126 port 38579
Oct  6 10:51:31 kevinisha sshd[5116]: User root from 211.241.149.126 not allowed because not listed in AllowUsers
Oct  6 10:51:41 kevinisha sshd[5118]: Connection from 211.241.149.126 port 38807

(-:

---

### Post by CharlesA on 2010-10-06
I'm running these three rules in iptables-save (which I apply with iptables-restore):

```
-A INPUT -p tcp --dport 22 -m state --state NEW -m recent --set --name  SSH --rsource
-A INPUT -m recent --update --seconds 600 --hitcount 4 --rttl --name SSH  --rsource -j DROP
-A INPUT -p tcp -m tcp --dport 22 -j ACCEPT

```

I've only had a few hits over the last couple days:

```
Oct  5 14:12:39 atlantis sshd[914]: Invalid user ftptest from 208.109.86.178
Oct  5 14:12:40 atlantis sshd[917]: Invalid user oracle from 208.109.86.178
Oct  5 14:12:40 atlantis sshd[919]: Invalid user weblogic from 208.109.86.178
Oct  5 14:50:16 atlantis sshd[926]: User root from 211.245.23.188 not allowed because not listed in AllowUsers
Oct  5 14:50:17 atlantis sshd[929]: User root from 211.245.23.188 not allowed because not listed in AllowUsers
Oct  5 14:50:19 atlantis sshd[932]: User root from 211.245.23.188 not allowed because not listed in AllowUsers
Oct  6 11:26:23 atlantis sshd[1491]: User root from wpc0287.amenworld.com not allowed because not listed in AllowUsers
Oct  6 11:26:25 atlantis sshd[1495]: Invalid user toor from 62.193.234.37
Oct  6 11:36:48 atlantis sshd[1497]: Invalid user ron from 77.243.225.166

```

Without those rules in place it was a bit more..messy.

---

### Post by buntolith on 2010-10-09
I have changed to the rules you posted CharlesA because I needed to increase the hitcount and it was easier to do that with your rules. I am backing up with rsync and if all the files are synchronized I got blocked by the firewall.  

Thanks.

---

### Post by CharlesA on 2010-10-09
Yeah, I believe rsync does one file per hit like scp, but I could be wrong.

---

