---
title: "GproFTPD questions"
date: 2008-09-24
forum: Security
---

### Post by SINZAR on 2008-09-24
I run an ftp server using gproftpd, last night there was an attempt to hack it. Since I'm confident this will not be the last time I want to take some measures to protect it further.

The attacker was simply trying to brute force a login/pass. Luckily he was trying the administrator login which doesn't exist so there was no chance, but he was flooding the server for 3 hours.

My first question is: how the heck do you ban an ip? Sure you can ban users, but I can't seem to find an option to ban just an ip.

Secondly, from the logs I see that even though the max tries is set at 2, the attacker only had to wait 2 seconds before the attacks could start again. This is unacceptable. How can I change the disconnection time limit or how can I set it so that after a certain number of failed tries, the ip is automatically banned?

Any help would be appreciated.

---

### Post by SINZAR on 2008-09-24
After some research, I found that in this case to ban the IP from not only logging in but connecting to the machine in general I added it to the /etc/hosts.deny file.

Going to look into a way to prevent the flooding though. I'm thinking some kind of script will be the solution. I have basic scripting knowledge so if anybody could provide me with some kind of guide or even a base script that would be very helpful.

---

### Post by The Cog on 2008-09-24
I have seen mentions of fail2ban which may do what you need. It monitors logs and automatically blocks addresses that repeatedly fail.

You can manually enter offending addresses into iptables, or install a firewall GUI which will block their connection attempts.

---

### Post by SINZAR on 2008-09-24
Thanks for the tip I'm going to look in to fail2ban.

---

