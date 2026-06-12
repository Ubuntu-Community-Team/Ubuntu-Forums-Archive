---
title: "DNS help"
date: 2009-10-08
forum: Server Platforms
---

### Post by bventura on 2009-10-08
Hello I've set up as follows:


$TTL	604800
@	IN	SOA	dns1.mydomain.com. root.mydomain.com. (
			      7		; Serial
			 604800		; Refresh
			  86400		; Retry
			2419200		; Expire
			 604800 )	; Negative Cache TTL
;
@	IN	NS	dns1.mydomain.com.
@	IN	A	127.0.0.1
@	IN	AAAA	::1
dns1	IN	A	12.34.56.78


ubuntusvr2	IN	A	12.34.56.78


mail		IN	CNAME	ubuntusvr2



but when i try to ping or dig my CNAME'd host I can't:

ping mail.mydomain.com
ping: cannot resolve mail.mydomain.com: Unknown host


dig mail.mydomain.com

;; ANSWER SECTION:
mail.mydomain.com.	529373	IN	CNAME	ubuntusvr2.mydomain.com.mydomain.com.


That dig response must be a hint: "ubuntusvr2.mydomain.com.mydomain.com"...

How can I fix this, my db.mydomain.com must have an error but I'm not sure what it is.  Any ideas?

---

### Post by koenn on 2009-10-08
> **bventura said:**
> Hello I've set up as follows:

```

$TTL	604800
@	IN	SOA	dns1.mydomain.com. root.mydomain.com. (
			      7		; Serial
			 604800		; Refresh
			  86400		; Retry
			2419200		; Expire
			 604800 )	; Negative Cache TTL
;
@	IN	NS	dns1.mydomain.com.
@	IN	A	127.0.0.1
@	IN	AAAA	::1
dns1	IN	A	12.34.56.78


ubuntusvr2	IN	A	12.34.56.78


mail		IN	CNAME	ubuntusvr2

```


but when i try to ping or dig my CNAME'd host I can't:

ping mail.mydomain.com
ping: cannot resolve mail.mydomain.com: Unknown host


dig mail.mydomain.com

;; ANSWER SECTION:
mail.mydomain.com.	529373	IN	CNAME	ubuntusvr2.mydomain.com.mydomain.com.


That dig response must be a hint: "ubuntusvr2.mydomain.com.mydomain.com"...

How can I fix this, my db.mydomain.com must have an error but I'm not sure what it is.  Any ideas?

this is bind, right ?
I'm a bit rusty on bind. 

"ubuntusvr2.mydomain.com.mydomain.com"... would appear if you had an entry for "ubuntusvr2.mydomain.com" without a terminating '**.**' somewhere, but I can't see it. It might be in a different file. $ORIGIN in your named.conf may be wrong, or something along those lines.

try replacing 
```
mail		IN	CNAME	ubuntusvr2
```
with
```
mail		IN	CNAME	ubuntusvr2.mydomain.com.
```
and see what that gives.

---

