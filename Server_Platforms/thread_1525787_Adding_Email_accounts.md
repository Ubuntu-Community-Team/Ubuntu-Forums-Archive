---
title: "Adding Email accounts"
date: 2010-07-07
forum: Server Platforms
---

### Post by Nixforce on 2010-07-07
> Invalid domain eastcoastrecruitment.co.za, and/or not discoverable in DNS.

This is a error message i get when creating a email account on postfix admin .

Any advice would be greatly appreciated.

---

### Post by Bachstelze on 2010-07-07
Pretty self-explanatory: the domain [font=monospace]eastcoastrecruitment.co.za[/font] does not exist.

---

### Post by HermanAB on 2010-07-07
Hmmmm....

```
$ dig  mail.eastcoastrecruitment.co.za A

; <<>> DiG 9.6.1-P3 <<>> mail.eastcoastrecruitment.co.za A
;; global options: +cmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 44445
;; flags: qr rd; QUERY: 1, ANSWER: 1, AUTHORITY: 0, ADDITIONAL: 0
;; WARNING: recursion requested but not available

;; QUESTION SECTION:
;mail.eastcoastrecruitment.co.za. IN    A

;; ANSWER SECTION:
mail.eastcoastrecruitment.co.za. 10000 IN A     74.53.46.139

;; Query time: 45 msec
;; SERVER: 192.168.1.1#53(192.168.1.1)
;; WHEN: Wed Jul  7 22:12:16 2010
;; MSG SIZE  rcvd: 65
```

```
$ dig  mail.eastcoastrecruitment.co.za MX

; <<>> DiG 9.6.1-P3 <<>> mail.eastcoastrecruitment.co.za MX
;; global options: +cmd
;; connection timed out; no servers could be reached
```

Aha!

Your mail server doesn't have a MX record.

```
$ dig  mail.eastcoastrecruitment.co.za PTR

; <<>> DiG 9.6.1-P3 <<>> mail.eastcoastrecruitment.co.za PTR
;; global options: +cmd
;; connection timed out; no servers could be reached
```

and it doesn't have a PTR record either.

---

