---
title: "Can't see port fowarding"
date: 2012-03-22
forum: Server Platforms
---

### Post by pepe308 on 2012-03-22
Hello,
i just added the following rule on iptables :

sudo iptables -t nat -A PREROUTING -p tcp --dport 25 -i eth0 -j REDIRECT --to-port 55

It works very well.

But when i type sudo iptables -L
i just had :
Chain INPUT (policy ACCEPT)
target     prot opt source               destination         

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination    

I can't see the port fowarding.
Can somebody give me the trick ?

Thanks

---

### Post by Doug S on 2012-03-22
To see the nat table, you need to specify it. Try:```
sudo iptables -t nat -L
```
I also like to see the counters and do not like service looks ups, so I use:```
sudo iptables -t nat -L -n -v -x
``` To see everything all at once try:```
sudo iptables-save -c
```

---

### Post by SeijiSensei on 2012-03-22
That rule is in the nat table; by default "iptables -L" shows only the filter table.  Use "iptables -t nat -L" instead.

---

### Post by pepe308 on 2012-03-23
Thank you a lot.

---

