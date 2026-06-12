---
title: "PHP SOAP Extension Not Working"
date: 2011-07-08
forum: Server Platforms
---

### Post by waffleguy4 on 2011-07-08
Hi there!

I am having issues getting the SOAP extension to work in Ubuntu 11.04. I am using the same code that works on our Redhat server and on WAMP in Windows, but does not work in Ubuntu. I've search all over these forums and Google to no avail. My co-worker also confirms this problem in Ubuntu 10. The error I get is:

```
Warning: SoapClient::SoapClient(http://_____.com/wsdls/Registration.svc.wsdl): failed to open stream: HTTP request failed!

Warning: 
SoapClient::SoapClient(): I/O warning : failed to load external entity 

Fatal error: 
SOAP-ERROR: Parsing WSDL: Couldn't load from 'http://____.com/wsdls/Registration.svc.wsdl' : failed to load external entity 
```

I have the latest LAMP version installed. Info from phpinfo():

```
PHP Version 5.3.5-1ubuntu7.2

```
Soap Info:

```
Soap Client	enabled
Soap Server	enabled

Directive	Local Value	Master Value
soap.wsdl_cache	1	1
soap.wsdl_cache_dir	/tmp	/tmp
soap.wsdl_cache_enabled	1	1
soap.wsdl_cache_limit	5	5
soap.wsdl_cache_ttl	86400	86400

```


Thanks!

---

### Post by waffleguy4 on 2011-07-26
Still no luck :-( 
Anyone?

---

