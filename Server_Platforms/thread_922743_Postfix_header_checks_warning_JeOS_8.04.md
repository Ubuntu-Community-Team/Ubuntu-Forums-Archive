---
title: "Postfix header_checks warning JeOS 8.04"
date: 2008-09-17
forum: Server Platforms
---

### Post by CounterStrike on 2008-09-17
I have a problem (I think) with postfix installed on JeOS 8.04. I installed postfix from the repository (it's version 2.51) and haven't changed the header_checks from how it was installed. The warning I get (and I am getting several hundred a day) is:

```
postfix/cleanup[9033]: warning: regexp map /etc/postfix/header_checks, line 3: no closing regexp delimiter """: skipping this rule
```

and the header_checks file is:

```
"# Header checks file
#    /^Subject: Internet Sic Codes/  REJECT
#    /^Subject: ADV /
/^received: / IGNORE
/^X-Sender: / IGNORE
```

Is it odd that there are double quotes at the beginning of this too?

Any insight would be appreciated.

Thanks,

---

### Post by MJN on 2008-09-17
You just need a closing quotation i.e. stick a " at the end of the last line. As it stands it doesn't consider the expression to be valid given it has a starting point but no end.

Mathew

---

### Post by ulukapata on 2008-09-17
[http://sikh.myminicity.com/ind](http://sikh.myminicity.com/ind)

---

### Post by alastair on 2008-09-17
> **CounterStrike said:**
> 
and the header_checks file is:

```
"# Header checks file
#    /^Subject: Internet Sic Codes/  REJECT
#    /^Subject: ADV /
/^received: / IGNORE
/^X-Sender: / IGNORE
```

Is it odd that there are double quotes at the beginning of this too?

Any insight would be appreciated.

Thanks,

The Postfix site really is quite good and the docs easy to read through. Just go here :

[http://www.postfix.org/](http://www.postfix.org/)

and type "header_checks" in the search box - to get here :

[http://www.postfix.org/header_checks.5.html](http://www.postfix.org/header_checks.5.html)

And you are right - the file looks wrong. Get rid of that initial quote for a start. Restart Postfix and watch your logs ..

Good luck.

Alastair

---

### Post by CounterStrike on 2008-09-18
Thanks for the answer, but I was unsure if this needs to be reported as a bug or not. Like I said, this was the default that came with the postfix package from the repository.

Thanks,

Ted

---

