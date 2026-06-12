---
title: "Host command?"
date: 2011-05-23
forum: The Cafe
---

### Post by CptSnork on 2011-05-23
Hello!

Does anyone know what the equivalent for this command would be in MS cmd (nslookup?) or a online tool that actually uses the host command???

I'm have a real problem trying to explain this to my ISP. They use online tools to look up DNS stuff and they just don't understand what I'm trying to say. 

WHEN you do this (using google as an example) >> #host  74.125.155.103 you get an answer and therein you'll see the CNAME (right?).

NOW you do >> #host WHATEVERCANAME there should be additional answer saying blahblahblahCNAME with this address or hey i'm official... 

The problem with my ISP is that there is no answer when you use the host command on the CNAME. I don't know if I'm ranting, pissed off, or just plain wrong. All I want is that my emails don't get rejected or go straight to spam:cry:

Anybody have similar problems or experiences?

---

### Post by CharlesA on 2011-05-23
You can use dig to check name resolution.

I think it's almost the same thing as nslookup.

---

### Post by timZZ on 2011-05-23
I use dig

---

### Post by Austin25 on 2011-05-23
For dns lookup:
```

dig google.com

```
For reverse dns lookup:
```

dig -x 74.125.225.19

```

---

### Post by CptSnork on 2011-05-23
> **CharlesA said:**
> You can use dig to check name resolution.

I think it's almost the same thing as nslookup.

> **timZZ said:**
> I use dig

> **Austin25 said:**
> For dns lookup:
```

dig google.com

```For reverse dns lookup:
```

dig -x 74.125.225.19

```


Thank you all for your help! Dig gives back waaay more info than host does. Is the host command outdated? By what means does an email server usually authenticate where the received email comes from? Do they use the dig command as well?

---

### Post by CharlesA on 2011-05-23
IIRC an email server will do a DNS look up of the domain mail is coming from to help filter spam.

Not sure if it does a reverse dns or not tho.

---

### Post by CptSnork on 2011-05-23
> **CharlesA said:**
> IIRC an email server will do a DNS look up of the domain mail is coming from to help filter spam.

Not sure if it does a reverse dns or not tho.


OK, that's straightforward enough. A simple DNS look up should reveal everything it needs to know. Just would like to know if the server would be happy with the MX record from that result or if it keeps digging... I need to stop obsessing though! Thanks CharlesA!

---

### Post by CharlesA on 2011-05-23
> **CptSnork said:**
> OK, that's straightforward enough. A simple DNS look up should reveal everything it needs to know. Just would like to know if the server would be happy with the MX record from that result or if it keeps digging... I need to stop obsessing though! Thanks CharlesA!
No problem. :)

---

