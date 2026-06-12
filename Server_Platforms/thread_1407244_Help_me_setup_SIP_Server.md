---
title: "Help me setup SIP Server"
date: 2010-02-15
forum: Server Platforms
---

### Post by dipeshmehta on 2010-02-15
Hello all,

I have been using Ubuntu 8.04LTS server mainly for internal emails and XMPP IM Server, VPN Server etc.

I want to deploy SIP/VoIP services to run for my organisation.  I want some simple setup to enable company users to communicate each other.  I do not want to connect my PSTN lines to this SIP server.

Please point me to some good resource regarding the same.  Also please tell me which kind of SIP phone would be better... softphone or USB SIP phone?

Thanks in advance.

Dipesh

---

### Post by iponeverything on 2010-02-15
"simple" and sip servers often don't go well together. But then again, it is a relative term.

---

### Post by kiranmurari on 2010-02-15
Hi Dipesh,

You can use Asterisk ([http://www.asterisk.org/](http://www.asterisk.org/)) to setup your SIP server.
   
For installing, you can run the following command:
```
$ sudo apt-get install asterisk
```or compile Asterisk from source [http://www.asterisk.org/downloads](http://www.asterisk.org/downloads)
   
For configuration, please see: 
[http://www.asterisk.org/astdocs/node16.html](http://www.asterisk.org/astdocs/node16.html)
   
You can use the X-Lite-3.0 softphone available from Counterpath
[http://www.counterpath.com/x-lite.html](http://www.counterpath.com/x-lite.html)

Hope this helps.

---

