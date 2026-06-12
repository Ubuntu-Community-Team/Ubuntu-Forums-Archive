---
title: "2 servers for one domain"
date: 2008-03-26
forum: Server Platforms
---

### Post by android6011 on 2008-03-26
If I have 2 servers at different locations is it possible to setup the servers/domain to go the other as a backup server in case of any problems?

---

### Post by koenn on 2008-03-26
sure

---

### Post by android6011 on 2008-03-26
how?

---

### Post by smileypaul on 2008-03-26
secondary dns?

---

### Post by koenn on 2008-03-26
> **android6011 said:**
> how?
you leave 1 server in the first location and put the 2nd server in the other location.


If you want an answer that's useful, maybe try giving some information that's useful. 
Are you talking about DNS servers ? dhcp servers ? file servers ? ...
DNS domains ? Active directory domains ? different physical locations ?  public networks ?  private networks ? or just 2 home servers, 1 in your bedroom and one in the kitchen but all on the same private LAN ?

---

### Post by android6011 on 2008-03-26
i have a web server mapped to mysite.com, if the server goes down i want to know if there is a way to have mysite.com automatically point to the second server. the first would be at home, the second would be a free server in another state.

---

### Post by koenn on 2008-03-26
[http://www.autofailover.com/Features/Autofailover.htm](http://www.autofailover.com/Features/Autofailover.htm)

---

