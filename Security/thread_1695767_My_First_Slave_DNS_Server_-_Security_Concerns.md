---
title: "My First Slave DNS Server - Security Concerns"
date: 2011-02-26
forum: Security
---

### Post by gamma1983 on 2011-02-26
I've built my first slave dns server last week using ubuntu. I used the book "The Official Ubuntu Server Book Second Edition" to setup bind and ufw. 

The only services I have is ssh and bind. I've changed the default port that ssh listens on. 
My ufw rules denies by default and allowed port 53 for dns. Also this is a cloud server.

I have no other security in place. How concerned should I be worried about being compromised.

---

### Post by SeijiSensei on 2011-02-26
Presuming that you've locked down TCP transfers to the DNS master with the "allow-transfers" directive in named.conf you're probably okay.  I'd add rules to iptables that allow only the transfer hosts TCP access to port 53, but that's icing on the cake.  

However you need to pay attention to security updates for BIND.  There was a [new exploit]("http://www.securityweek.com/high-severity-bind-vulnerability-advisory-issued") discovered the other day and a patch released.  It appears to apply to versions in the 9.7 series; my CentOS servers run 9.3.6 with various patches added by RedHat.

---

### Post by gamma1983 on 2011-02-26
Yes, I allowed zone transfer to just that ip address. SeijiSensei, thanks for reassuring me.

---

