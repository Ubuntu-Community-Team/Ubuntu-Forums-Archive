---
title: "Port redirection problem"
date: 2008-09-23
forum: Security
---

### Post by prateek19 on 2008-09-23
In the IPTable, I have following port redirection:-
-A PREROUTING -p tcp -m tcp --dport 80 -j REDIRECT --to-ports 8080
-A OUTPUT -d 127.0.0.1 -p tcp -m tcp --dport 80 -j DNAT --to-destination :8080
-A OUTPUT -d 100.50.244.122 -p tcp -m tcp --dport 80 -j DNAT --to-destination :8080

This will redirect the packets coming to port number 80 to port number 8080.

My problem is to redirect port number 1234 to port number 8080. To do so, I have redirected the port number 1234 to port number 80 as below:-
-A PREROUTING -p tcp -m tcp --dport 1234 -j REDIRECT --to-ports 80
-A OUTPUT -d 127.0.0.1 -p tcp -m tcp --dport 1234 -j DNAT --to-destination :80
-A OUTPUT -d 100.50.244.122 -p tcp -m tcp --dport 1234 -j DNAT --to-destination :80

Since 80 is being redirected to 8080 so ultimately 1234 should also get redirected to 1234(1234->80 and 80->8080). But somehow it is not working, can somebody tell me what wrong am I doing here?

I can also make an entry to directly redirect port 1234 to 8080 but somehow that also is not working.

Thanks in advance,
Prateek

---

### Post by regala on 2008-09-23
> **prateek19 said:**
> 

My problem is to redirect port number 1234 to port number 8080. To do so, I have redirected the port number 1234 to port number 80 as below:-
-A PREROUTING -p tcp -m tcp --dport 1234 -j REDIRECT --to-ports 80
-A OUTPUT -d 127.0.0.1 -p tcp -m tcp --dport 1234 -j DNAT --to-destination :80
-A OUTPUT -d 100.50.244.122 -p tcp -m tcp --dport 1234 -j DNAT --to-destination :80

Since 80 is being redirected to 8080 so ultimately 1234 should also get redirected to 1234(1234->80 and 80->8080). But somehow it is not working, can somebody tell me what wrong am I doing here?



Just redirect it to 8080 in your rules, and it should work...
The reason why it fails seems to be the order of your rules. If rules redirecting 80 to 8080 are **above** the ones redirecting 1234 to 80, they will not match the first ones and never be redirected.

anyway, you should just redirect it to 8080, no need to "chain" rules that don't need to.

Cheers,

Mathieu

---

### Post by prateek19 on 2008-09-23
Hi Mathieu,

Thanks for your suggestions.
I tried doing this too, now the IPTables entries look like following:-

-A PREROUTING -p tcp -m tcp --dport 1234 -j REDIRECT --to-ports 8080
-A OUTPUT -d 127.0.0.1 -p tcp -m tcp --dport 1234 -j DNAT --to-destination :8080
-A OUTPUT -d 100.50.244.122  -p tcp -m tcp --dport 1234 -j DNAT --to-destination :8080
-A PREROUTING -p tcp -m tcp --dport 443 -j REDIRECT --to-ports 8443
-A OUTPUT -d 127.0.0.1 -p tcp -m tcp --dport 443 -j DNAT --to-destination :8443
-A OUTPUT -d 100.50.244.122  -p tcp -m tcp --dport 443 -j DNAT --to-destination :8443
-A PREROUTING -p tcp -m tcp --dport 80 -j REDIRECT --to-ports 8080
-A OUTPUT -d 127.0.0.1 -p tcp -m tcp --dport 80 -j DNAT --to-destination :8080
-A OUTPUT -d 100.50.244.122  -p tcp -m tcp --dport 80 -j DNAT --to-destination :8080

But still it is not working.
To test this change, I am trying to invoke the URL [http://100.50.244.122:6293/](http://100.50.244.122:6293/) but it is showing "The page cannot be displayed" error. But if I invoke [http://100.50.244.122:80/](http://100.50.244.122:80/) OR [http://100.50.244.122:8080/](http://100.50.244.122:8080/) they are working fine.

One more doubt, after changing the /etc/sysconfig/iptables file, what else we need to do so as to bring the changes effective into firewall? As of now am just changing and saving this file and not doing anything else.

Thanks again for your help!
Prateek

---

### Post by cdenley on 2008-09-23
```

man iptables

```
> 
It specifies that the destination address of the packet should be  modified (and all future packets in this connection will also be mangled), and **rules should cease being examined**.


---

### Post by kevdog on 2008-09-23
Im not sure if this will work but you could try the following:

-A PREROUTING -p tcp -m multiport --destination-port 80,1234 -j REDIRECT --to-ports 8080

---

