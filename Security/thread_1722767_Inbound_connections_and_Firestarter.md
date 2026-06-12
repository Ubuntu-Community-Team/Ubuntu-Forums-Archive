---
title: "Inbound connections and Firestarter"
date: 2011-04-06
forum: Security
---

### Post by flokker on 2011-04-06
Hello, I am running Ubuntu 10.10 i have an question about the firewall Firestarter, when checking the firewall it told me there are 9 serious incoming connections what must i do with this info.:confused:

Inbound is normally blocked as standard i have also see that someone with port 1234 and 12345 have trying to attempt mine system but failed all trojan ports are fully blocked.

---

### Post by bodhi.zazen on 2011-04-06
This sort of behavior is fairly standard. If the port is blocked, it is blocked and I do not think you need to do anything more.

You could turn off logging if you aer not going to do anything with the information.

Alternately you could use a service such as denyhosts, fail2ban, psad, or block the offending ip address.

---

### Post by flokker on 2011-04-07
Thanks for the answer i have installed fail2ban and denyhost i am no longer worry that something is going wrong thanks for your help and advice have an nice day.:)

---

