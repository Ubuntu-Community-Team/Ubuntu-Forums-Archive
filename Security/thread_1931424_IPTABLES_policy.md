---
title: "IPTABLES policy"
date: 2012-02-25
forum: Security
---

### Post by chevloschelios on 2012-02-25
Hi guys,

is it possible to change default policy somehow without reboot ??

```

iptables --policy INPUT DROP
iptables --policy OUTPUT DROP
iptables --policy FORWARD DROP

```i want to change to 

```

iptables --policy INPUT ACCEPT
iptables --policy OUTPUT ACCEPT
iptables --policy FORWARD ACCEPT

```Thank you

---

### Post by Lars Noodén on 2012-02-25
Just run them with sudo and they will take effect the moment you enter them.

---

### Post by chevloschelios on 2012-02-25
Wow, thank you ! :-)

---

### Post by Lars Noodén on 2012-02-25
You're welcome.

If you're sitting physically at the same computer as you are working on, then you can make changes and experiment as you wish and not have to worry.  

If you are working remotely then you have to be a little more careful and might want to look into [iptables-apply](http://manpages.ubuntu.com/manpages/oneiric/en/man8/iptables-apply.8.html).

---

### Post by kevdog on 2012-02-26
Wow Lars -- I learn stuff all the time -- I had no idea about the iptables-apply command for remote updating.  Cool stuff.

---

