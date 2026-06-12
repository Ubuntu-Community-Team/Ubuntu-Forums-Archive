---
title: "Postfix spf error"
date: 2019-04-27
forum: Server Platforms
---

### Post by secooonder on 2019-04-27
Hello 
i setup postfix/mysql/apache server 2 year ago. Postfix server works successfully 2 years.i did mxtoolbox site test  a few day ago.
i took an error " Spf record Deprecated ,no deprecated records found.[COLOR=#333333][FONT=&amp]The DNS record type 99 (SPF) has been deprecated[/FONT][/COLOR]"

But i entered the dns record correctly.

My mail server zone in bind server is ;
> IN      MX      10 xxx.abuse.com.tr.

   abuse.com.tr. IN TXT "v=spf1 a mx ip4:212.a.b.c -all"
   abuse.com.tr. IN SPF "v=spf1 a mx ip4:212.a.b.c -all"


i read many articles on the internet.And i saw ;
[COLOR=#242729][FONT=Arial]According to the latest Proposed Standard ([RFC 7208]("https://tools.ietf.org/html/rfc7208#section-3.1")), you should use TXT records only:
[/FONT][/COLOR]

> [COLOR=#242729][FONT=Arial]3.1. DNS Resource Records
SPF records MUST be published as a DNS TXT (type 16) Resource Record (RR) [RFC1035] only. The character content of the record is encoded as [US-ASCII]. Use of alternative DNS RR types was supported in SPF's experimental phase but has been **discontinued.**[/FONT][/COLOR]


i deleted abuse.com.tr. IN SPF "v=spf1 a mx ip4:212.a.b.c -all",and finally my zone file is;
> 
IN      MX      10 xxx.abuse.com.tr.
abuse.com.tr. IN TXT "v=spf1 a mx ip4:212.a.b.c -all"


And the i test mxtoolbox my mail server,i dont took an error :)


But when i saw bind log ; i see ;
"abuse.com.tr' found SPF/TXT record but no SPF/SPF record found, add matching type SPF record"


According to RFC 7208,i must delete spf line in bind zone.But when i deleted,i took en error in bind log

Which is true. ? 
Thank you

---

### Post by jbamford92 on 2019-04-28
> **secooonder said:**
> Hello 
i setup postfix/mysql/apache server 2 year ago. Postfix server works successfully 2 years.i did mxtoolbox site test  a few day ago.
i took an error " Spf record Deprecated ,no deprecated records found.[COLOR=#333333][FONT=&amp]The DNS record type 99 (SPF) has been deprecated[/FONT][/COLOR]"

But i entered the dns record correctly.

My mail server zone in bind server is ;


i read many articles on the internet.And i saw ;
[COLOR=#242729][FONT=Arial]According to the latest Proposed Standard ([RFC 7208]("https://tools.ietf.org/html/rfc7208#section-3.1")), you should use TXT records only:
[/FONT][/COLOR]



i deleted abuse.com.tr. IN SPF "v=spf1 a mx ip4:212.a.b.c -all",and finally my zone file is;



And the i test mxtoolbox my mail server,i dont took an error :)


But when i saw bind log ; i see ;
"abuse.com.tr' found SPF/TXT record but no SPF/SPF record found, add matching type SPF record"


According to RFC 7208,i must delete spf line in bind zone.But when i deleted,i took en error in bind log

Which is true. ? 
Thank you


Hi, this is taken out of my zone change you-domain with your correct domain. add SPF like this,


```
[FONT=Verdana]; SPF[/FONT]
[FONT=Verdana]your-domain. IN TXT "v=spf1 mx ~all"[/FONT]
```

---

### Post by secooonder on 2019-04-28
jbamford thank you.

i added as you said.i restart bind service but i took an error.
tailf /var/log/syslog ;
> 
zone abuse.com.tr/IN/external: 'abuse.com.tr' found SPF/TXT record but no SPF/SPF record found, add matching type SPF record



This error is normal.Because i deleted  "[COLOR=#000000][I]abuse.com.tr. IN SPF "v=spf1 a mx ip4:212.a.b.c -all"

According to mxtoolbox.com, i must delete this line?

i am so confused.[/I][/COLOR]

---

### Post by SeijiSensei on 2019-04-28
I've only ever had TXT records for SPF without any issues for well over a decade now.

---

### Post by secooonder on 2019-05-01
SeijiSensei
Thank you for your help

---

