---
title: "Bind help for Partial Class C RDNS"
date: 2008-10-04
forum: Server Platforms
---

### Post by Twinkie on 2008-10-04
I have successfully setup my first linux server using Ubuntu and Bind9. All of my dns settings are working great until reverse dns checks. I am not a dns guru and think the fact that I am using a partial class C is the cause. Can someone review and show me my error. Thank you.

For this sample domain my IP range is 1.18.2.160/27

/etc/bind/zones/rev.160.2.18.1.in-addr.arpa
$ttl 38400
@ IN SOA nsa.sample.net. root.sample.net. (
2008091001;
28800;
604800;
604800;
86400;
)

@ IN NS nsa.sample.net.
171 IN PTR nsa.sample.net.
170 IN PTR smtp.sample.net. ; ‘future secondary for later’
161 IN PTR mail.sample.net.
Or maybe it should be:
171.160/27.2.18.1 IN PTR nsa.sample.net.
170.160/27.2.18.1 IN PTR smtp.sample.net. ; ‘future secondary for later’
161.160/27.2.18.1 IN PTR mail.sample.net.


vi /etc/bind/named.conf.local
zone "160.2.18.1.in-addr.arpa" {
type master;
notify no;
file "/etc/bind/zones/rev.160.2.18.1.in-addr.arpa";
allow-transfer { 1.18.2.170; };
allow-update { none; };
allow-query { any; };
};

Thanks for any help

---

### Post by RealPSL on 2008-10-05
I am not sure I understand you problem but I will try to repeat it first. You have the configuration in place for reverse DNS for what you think is your "segment" of a class C subnet. Is the configuration working? Does named-checkconf and named-checkzone confirm your configuration?

I assume that you do not own this class C subnet you just own a few addresses. If this is the case I believe the person owning the class C is the only one that can setup reverse entries unless they delegate a segment of the network to you in a "classless" scheme. Has this been done?

---

### Post by Twinkie on 2008-10-05
Thanks for the reply but I am afraid I am more of a newbie than you think.  I am trying to figure out the syntax for named-checkconf and named-checkzone right now.

Their was a fee involved for my provider to manage the rdns records for my small segment.  I decided to just do it myself and had them transfer authority to my name servers.  Earlier when checking via DNS sleuth I got error NXDOMAIN but at least now the error is SERVFAIL so I guess I am making progress I think...

---

### Post by Twinkie on 2008-10-05
Okay, I had a chance to read up on the two utilities and both came back with no errors.  

Still no idea what is wrong...

---

### Post by RealPSL on 2008-10-19
Looking into this it would appear that webmin can do it fairly easily. I am not a huge fan of tools like Webmin but I think there is learning value in seeing what it does and then building you configuration based on that lesson. There is just not a lot of information out there about this.

---

