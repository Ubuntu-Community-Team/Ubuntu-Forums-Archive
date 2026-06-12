---
title: "Allow internet between certain hours using iptables"
date: 2011-01-06
forum: Security
---

### Post by toolmania1 on 2011-01-06
I typed this into the command line:

sudo iptables -A INPUT -p tcp --dport 80 -m time --timestart 12:00:00 --timestop 23:59:59 --days Sat, Sun -j ACCEPT

I get this error:

iptables v1.4.4: unknown option '--days'

How do I do something similar above in which I allow the internet to start at 12 o clock on Saturdays and Sundays?

Thanks in advance

---

### Post by FuturePilot on 2011-01-06
You probably want --weekdays

> [!] --weekdays day[,day...]
Only match on the given weekdays. Possible values are Mon, Tue, Wed, Thu, Fri, Sat, Sun,  or  values  from  1  to  7, respectively. You may also use two-character variants (Mo, Tu, etc.).

---

### Post by toolmania1 on 2011-01-06
sudo iptables -A INPUT -p tcp --dport 80 -m time --timestart 12:00:00 --timestop 23:59:59 --weekdays Sat, Sun -j ACCEPT

That worked, thanks!

---

### Post by bodhi.zazen on 2011-01-06
As I think I advised you in your other thread ....


I find these setting are MUCH more reliable in the OUTPUT chain (rather then the INPUT chain).

I also am guessing your syntax is off.

You may well want (take note of sport vs dport). Your rules would apply if you are running a server and from your other posts you are running a client.

sudo iptables -A INPUT -p tcp --sport 80 -m time --timestart 12:00:00 --timestop 23:59:59 --weekdays Sat, Sun -j ACCEPT

sudo iptables -A OUTPUT -p tcp --dport 80 -m time --timestart 12:00:00 --timestop 23:59:59 --weekdays Sat, Sun -j ACCEPT

---

### Post by toolmania1 on 2011-01-07
So, I should put the OUTPUT line only since I am using a client ( my home pc )?


sudo iptables -A OUTPUT -p tcp --dport 80 -m time --timestart 12:00:00 --timestop 23:59:59 --weekdays Sat, Sun -j ACCEPT

---

### Post by fraser_john on 2011-10-20
How can I add a MAC Address to the OUTPUT posted above? I want to restrict my childrens access to the internet via the Ubuntu Server that I have running as the router.

Would adding -m mac --mac-source xx:xx:xx:xx:xx:xx to the above work? Though it looks to me (reading other posts) that MAC filtering wont work on OUTPUT?

Thanks.

---

### Post by bodhi.zazen on 2011-10-20
> **fraser_john said:**
> How can I add a MAC Address to the OUTPUT posted above? I want to restrict my childrens access to the internet via the Ubuntu Server that I have running as the router.

Would adding -m mac --mac-source xx:xx:xx:xx:xx:xx to the above work? Though it looks to me (reading other posts) that MAC filtering wont work on OUTPUT?

Thanks.

Just match on owner.

---

