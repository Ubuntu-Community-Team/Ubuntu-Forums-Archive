---
title: "Cname for non www"
date: 2010-08-31
forum: Server Platforms
---

### Post by xkaliburx on 2010-08-31
ok, running bind 9 on a U9.04 server and need to make a change which I did, but it's failing a looking.  I am moving from an A -> public IP to a CNAME -> amazon load balancer and having an issue with the domain.com record.

I have moved the www easily using the syntax;

```
www  14400  IN  CNAME  domain-1965389820.us-east-1.elb.amazonaws.com.
```

A restart/dig against the nameserver shows it fine;
;; ANSWER SECTION:
[www.domain.com](www.domain.com).	14400	IN	CNAME	domain-1965389820.us-east-1.elb.amazonaws.com.

Now if someone hit [www.domain.com](www.domain.com) it works, but I want domain.com to do the same.  I have tried both;

```
             14400  IN  CNAME  domain-1965389820.us-east-1.elb.amazonaws.com.
domain.com.  14400  IN  CNAME  domain-1965389820.us-east-1.elb.amazonaws.com.

```

Both of those don't work, so what is the syntax to create a CNAME for domain.com?  As a temp workaround, I have it going to an A record static IP but do need this resolved.

Thanks.

---

### Post by Bachstelze on 2010-08-31
We'd need your whole zone file. Normally, the second version should work.

---

### Post by xkaliburx on 2010-08-31
Was going to send it all, then thought really didn't need it, sorry and thanks.  So right now the domain.com. as I said has the 'a' record set to the static, but that should be changed to the loadbalancer.



domain.com.   IN SOA  nsserver.domain.com. support.domain.com. (
                                        2007021345       ; Serial
                                        10800   ; Refresh after 3 hours
                                        3600    ; Retry after 1 hour
                                        604800  ; Expire after 1 week
                                        86400 ) ; Minimum TTL of 1 day

;
; Name Servers
;
                        IN      NS      ns1.nsserver.com.
                        IN      NS      ns2.nsserver.com.

;
; Mail Exchangers
;
;                        IN      MX      10      mail.domain.com.
;                        IN      MX      20      mail2.domain.com.
domain.com.        86400   IN      MX      100     domain.com.s8a1.psmtp.com.
domain.com.        86400   IN      MX      200     domain.com.s8a2.psmtp.com.
domain.com.        86400   IN      MX      300     domain.com.s8b1.psmtp.com.
domain.com.        86400   IN      MX      400     domain.com.s8b2.psmtp.com.

;
; Addresses for the canonical names
;
domain.com.          IN      A       184.73.111.111
staging                 IN      A       38.101.111.111
cloud                   IN      A       184.73.111.111

;;;;;;;;;;;;;;;;;;;
;;;  Cname
;;;;;;;;;;;;;;;;;;;;

cblb  14400  IN  CNAME  domain-1965389820.us-east-1.elb.amazonaws.com.
www  14400  IN  CNAME  domain-1965389820.us-east-1.elb.amazonaws.com.

---

### Post by Bachstelze on 2010-08-31
```
firas@aoba ~ % named-checkzone domain.com domain.com.zone
domain.com.zone:1: no TTL specified; using SOA MINTTL instead
zone domain.com/IN: has no NS records

```

First, you should have a TTL define on your first line, like

```
$TTL 3600 ; 1 hour
```

Second, you have nsserver.domain.com. in your SOA record, but it doesn't appear in your NS records, and has no A.

---

