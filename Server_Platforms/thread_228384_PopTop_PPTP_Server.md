---
title: "PopTop PPTP Server"
date: 2006-08-03
forum: Server Platforms
---

### Post by soon82 on 2006-08-03
Have somebody used Poptop pptp server before.. Because i had meet a problem.

Example: my office network id is = 172.16.0.1 255.255.0.0
         my pptp server ip address is 172.16.0.1
         my remote host ip range is 172.16.0.20-30
         my windows server 2003 is 172.16.0.100

When i try to connect my home pc to my office. my pc obtain the ip address from my pptp-server was 172.16.0.20

After successfully establish the connection to my office network, i can't even ping my windows server 2003. But i can ping to my pptp server.

---

### Post by elias@cpaefs.com on 2006-08-03
Make sure Ip fowarding is enable in the ubuntu box.

echo "1" > /proc/sys/net/ipv4/ip_forward


You can also learn more at this [link]("http://www.members.optushome.com.au/~wskwok/poptop_ads_howto_1.htm")

---

### Post by cantormath on 2006-08-03
> **soon82 said:**
> Have somebody used Poptop pptp server before.. Because i had meet a problem.

Example: my office network id is = 172.16.0.1 255.255.0.0
         my pptp server ip address is 172.16.0.1
         my remote host ip range is 172.16.0.20-30
         my windows server 2003 is 172.16.0.100

When i try to connect my home pc to my office. my pc obtain the ip address from my pptp-server was 172.16.0.20

After successfully establish the connection to my office network, i can't even ping my windows server 2003. But i can ping to my pptp server.

Where is the Windows Server 2003, at your work or home?
Is your home router pointing the outside ip to your home computer?

---

