---
title: "Server Signature Coming in Response headers how to disable that"
date: 2010-07-18
forum: Server Platforms
---

### Post by tapas_mishra on 2010-07-18
On my Ubuntu Server 10.04

I have in apache2.conf
```


ServerTokens Prod
ServerSignature Off

```

I also tried
```


ServerTokens Off
ServerSignature Off

```
but in Response headers I can see 
```

[Server:Apache/2.2.14 (Ubuntu) mod_jk/1.2.28 PHP/5.3.2-1ubuntu4.2 with Suhosin-Patch proxy_html/3.0.1
Vary:Accept-Encoding

```
Is there a way to disable that ?

---

### Post by tapas_mishra on 2010-07-18
Can not say what was the problem also disabled in /etc/apache2/conf.d/security
rebooted every thing is working fine now.

---

