---
title: "Iptables entries: * in-f99.google.com"
date: 2009-01-07
forum: Security
---

### Post by Xamiga on 2009-01-07
:confused:Why do I have references to *in-f99.google.com in my iptables?

from iptables:

Chain OUTBOUND (3 references)
target     prot opt source               destination         
ACCEPT     icmp --  anywhere             anywhere            
ACCEPT     tcp  --  anywhere             anywhere            state RELATED,ESTABLISHED 
ACCEPT     udp  --  anywhere             anywhere            state RELATED,ESTABLISHED 
LSO        all  --  anywhere             ag-in-f99.google.com 
LSO        all  --  anywhere             od-in-f99.google.com 
ACCEPT     all  --  anywhere             anywhere

---

### Post by hyper_ch on 2009-01-08
> **Xamiga said:**
> :confused:Why do I have references to *in-f99.google.com in my iptables?

Very likely because you added it - somehow.

---

### Post by Xamiga on 2009-01-08
Thanks,
I didn't knowingly add - or modify - my iptables.
What does the 'LSO' entry mean, and how do I remove them?

---

### Post by Xamiga on 2009-01-08
Thanks,
I didn't knowingly add to - or modify - my iptables.
What does the 'LSO' entry mean, and how do I remove them?
Could this be related to the Ubuntu extensions for Firefox?

---

### Post by Xamiga on 2009-01-08
removed networkmanager
removed firestarter
rebooted
cleaned iptables
rebooted
installed networkmanager
rebooted
sudo iptables -L -v
- no *-in-f99.google.com entries
installed firestarter
rebooted
*****
*-in-f99.google.com entries REAPPEARED 

firestarter is the culprit?  Can anyone recreate this?

---

### Post by hyper_ch on 2009-01-09
why instal firestarter?

---

### Post by Xamiga on 2009-01-09
My internet connection is ppp0, this machine is gateway for wifes XP (wired).  Without installing firestarter I have no internet connectivity and no connection from wifes machine.  There must be a way to accomplish this without firestarter, but thats not my question/point.  Why is firestarter doing this to my machine?

---

