---
title: "Unblock an IP address (IPTables)"
date: 2013-07-20
forum: Security
---

### Post by alfirdaous on 2013-07-20
Hello everybody,

I tried this command:

```

iptables -L INPUT -n --line-numbers

// some outputs here then I found an IP address

30   DROP       all  --  XX.XX.XX.XX       0.0.0.0/0           

```

I used this command to delete:

```

iptables -D INPUT 30

```

I did:

```

iptables -L

Chain fail2ban-apache-overflows (1 references)
target     prot opt source               destination         
DROP       all  --  XX.XX.XX.XX       anywhere            
RETURN     all  --  anywhere             anywhere  

```

The IP address is still there, How can I delete it (unblock).

Thx in advance

---

### Post by prodigy_ on 2013-07-20
> **alfirdaous said:**
> ```
Chain fail2ban-apache-overflows (1 references)
```
I think you need to delete from the fail2ban-apache-overflows chain, not from the INPUT chain.

---

### Post by alfirdaous on 2013-07-20
result:

```

iptables: Bad rule (does a matching rule exist in that chain?).

```

---

### Post by alfirdaous on 2013-07-20
sorry, thanks, it works, it was my mistake

---

### Post by prodigy_ on 2013-07-20
You're welcome. :)

---

### Post by alfirdaous on 2013-07-20
I reversed chain aith the IP, just a cross checking question: fail2ban-apache-overflows is it protecting against DDOS Attacks? or it has another role

---

