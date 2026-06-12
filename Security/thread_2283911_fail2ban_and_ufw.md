---
title: "fail2ban and ufw"
date: 2015-06-25
forum: Security
---

### Post by nicky5 on 2015-06-25
I have installed fail2ban and ufw on my server. Everything was working fine. Since this morning, I have received many complaints that many of the users can't access the server. I am afraid that maybe ufw or fail2ban has banned their access. 

What I did:

1 - I looked in the log files to see if an IP of a user was banned. IP doesn't exist of the people who can't access the server. 
2 - Disabled ufw and stopped fail2ban. Still those users can't access the server. 
3 - Used command iptables -nvL --line-numbers to check iptables ban. None of the users' ip listed there.

I asked users to use proxy and they able to access the server. However, with their original IPs they can't. Maybe their IPs have been blocked somewhere.

Is there any other place where I can check that why those users' IP can't access my server?

Thanks!

---

### Post by Habitual on 2015-06-25
check /var/log/fail2ban.log

---

### Post by nicky5 on 2015-06-25
> **Habitual said:**
> check /var/log/fail2ban.log

Thanks for a prompt reply. Yes, I already checked and those IPs are not there.

Is there way to limit ufw ban time? Also how to unban all the IPs banned by ufw and fail2ban?

---

### Post by Habitual on 2015-06-25
you can disable it as you've shown you know how, or reset using ```
sudo ufw reset
```
but I'd save /etc/iptables/rules.v4 somewhere before you do.

---

### Post by ddesanti on 2015-07-04
Hi:
You could do the following:

- check if the IP addresses are block by UFW
           cat /var/log/ufw.log |grep "IP address"
- check the status of UFW
            sudo ufw status or sudo ufw staus verbose
- If you find the IP address or range you will need to delete so not to block it.

Also have you checked your ports are not being blocked?

---

