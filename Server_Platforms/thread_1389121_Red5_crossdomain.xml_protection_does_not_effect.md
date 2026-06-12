---
title: "Red5 crossdomain.xml protection does not effect"
date: 2010-01-24
forum: Server Platforms
---

### Post by kojis_ on 2010-01-24
I installed red5 0.9.0 RC1 and it work well.

But now i have problem, i'm trying to protect my red5 server with crossdomain.xml/flashpolicy.xml, only allowed domain is able to stream in to my server.

**conf/flashpolicy.xml** :
```

<?xml version="1.0"?> 
<!DOCTYPE cross-domain-policy SYSTEM "/xml/dtds/cross-domain-policy.dtd"> 
 
<cross-domain-policy>  
    <site-control permitted-cross-domain-policies="master-only"/>
    <allow-access-from domain="alloweddomain.com" to-ports="20-65535" /> 
     
</cross-domain-policy>

```AND

**webapps/root/crossdomain.xml** :
```

<?xml version="1.0"?> 
<cross-domain-policy> 
    <site-control permitted-cross-domain-policies="master-only"/> 
    <allow-access-from domain="alloweddomain.com" to-ports="20-65535"/> 
</cross-domain-policy> 

```But i'm still able to stream to server with demo publisher in NOTalloweddomain.com.

Can somebody help me whats wrong?

---

