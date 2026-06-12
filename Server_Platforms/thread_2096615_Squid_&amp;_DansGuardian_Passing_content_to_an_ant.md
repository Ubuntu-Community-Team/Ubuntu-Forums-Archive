---
title: "Squid &amp; DansGuardian: Passing content to an antivirus product for scanning"
date: 2012-12-20
forum: Server Platforms
---

### Post by fitzroy87 on 2012-12-20
I have an Ubuntu Server12.04 installation acting as a proxy server using Squid 3.1.19.  

Squid has been configured to pass content to SquidClamAV 6.10 to check for viruses (using icap):
  ```

icap_service service_req reqmod_precache bypass=1 
icap://127.0.0.1:1344/squidclamav adaptation_access service_req allow all 
icap_service service_resp respmod_precache bypass=1 
icap://127.0.0.1:1344/squidclamav adaptation_access service_resp allow all

```The current setup works perfectly well, but now I&#8217;d like to install DansGuardian to provide content filtering.

  Like Squid, the DansGuardian config file  (/etc/dansguardian/dansguardian.conf) can also be integrated with  anti-virus products using the 'contentscanner' directive. 
  

Should I ignore the 'contentscanner' directive in DansGuardian and  leave Squid in charge of passing content to SquidClamAV for virus scanning. Or should I  have DansGuardian pass content to an anti-virus product? Or should they  both be passing content to anti-virus products?
  

What&#8217;s considered best practice? Are there any advantages/disadvantages either way?

---

### Post by fitzroy87 on 2013-01-03
*polite bump*

Is there any additional info I can add to this question to make it clearer? Or can anyone PM me with suggestions of an alternative forum with a few Squid enthusiasts?

Many thanks,
Fitzroy87

---

### Post by Ms. Daisy on 2013-01-03
This is dated but I imagine the basic architecture still stands true

[http://www.howtoforge.com/squid-proxy-server-on-ubuntu-9.04-server-with-dansguardian-clamav-and-wpad-proxy-auto-detection](http://www.howtoforge.com/squid-proxy-server-on-ubuntu-9.04-server-with-dansguardian-clamav-and-wpad-proxy-auto-detection)

---

