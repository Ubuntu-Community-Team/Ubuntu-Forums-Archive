---
title: "Example of Bind9 Zone File for DC and ADC"
date: 2022-09-18
forum: Server Platforms
---

### Post by secooonder on 2022-09-18
Hello


We will show Bind9 on the Linux machine as the DNS Server for the DC and ADC we have installed.


I couldn't find a healthy example anywhere for the zone file it should be.


Do I have a chance to get some help from those who have such a configuration?


 


DC: company.local


1.DC


Full Computer name: companydcsrv.company.local


Domain:company.local


Rope: 192.168.1.2


2.DC


Full Computer name: companyadcsrv.company.local


Domain:company.local


Rope: 192.168.1.3


Zone file I have;


$TTL 86400
$ORIGIN company.local.
@ IN SOA company.local. hostmaster.company.local. (
2022091701 ; serial
8H ; Refresh
1H ; Retry
1W ; Expire
1D ); Minimum
;name servers -NS Records
IN NS companydcsrv.company.local.
IN A 192.168.1.2
;A Records
companydcsrv A 192.168.1.2
companyadcsrv A 192.168.1.3
_ldap._tcp.company.local. SRV 0 0 389 companydcsrv.company.local.
_kerberos._tcp.company.local. SRV 0 0 88 companydcsrv.company.local.
_ldap._tcp.dc._msdcs.company.local. SRV 0 0 389 companydcsrv.company.local.
_kerberos._tcp.dc._msdcs.company.local. SRV 0 0 88 companydcsrv.company.local.
430820bc-7d7f-4c45-b554-4f3dbe7c3085._msdcs.company.local. CNAME companydcsrv.company.local.
913c53cb-44f8-448f-9f7f-4d863cd97324._msdcs.company.local. CNAME companydcsrv.company.local


 


I don't get any error when I do "named-checkzone".


But I don't know what is missing.


Can you help me ?


Thank you so much

---

