---
title: "Cannot join Win 2008 R2 domain: connection refused"
date: 2015-12-28
forum: Server Platforms
---

### Post by lorenzo-milesi on 2015-12-28
Hi
I'm trying to join my Ubuntu server (previously running Samba as AD) to a Win 2008R2 AD domain. I've done this before without issues, but in this case I cannot run *kinit*. I installed kerberos and configured it with the domain, after that I changed /etc/krb5.conf setting the kdc and domain admin params with the IP of the Win2k8 server, but when I run kinit:

```
# KRB5_TRACE=/dev/stdout kinit -V  Administrator                                                                         Using default cache: /tmp/krb5cc_0
Using principal: Administrator@MYDOMAIN.LOCAL
[13250] 1451287334.630246: Getting initial credentials for Administrator@MYDOMAIN.LOCAL
[13250] 1451287334.635072: Sending request (182 bytes) to MYDOMAIN.LOCAL
[13250] 1451287334.635138: Resolving hostname 192.168.1.16
[13250] 1451287334.635293: Sending initial UDP request to dgram 192.168.1.16:88
[13250] 1451287334.635865: UDP error receiving from dgram 192.168.1.16:88: 111/Connection refused
[13250] 1451287334.635896: Resolving hostname 192.168.1.16
[13250] 1451287334.636049: Sending initial UDP request to dgram 192.168.1.16:750
[13250] 1451287335.637190: Initiating TCP connection to stream 192.168.1.16:88
[13250] 1451287335.637731: Terminating TCP connection to stream 192.168.1.16:88
[13250] 1451287338.638188: Sending retry UDP request to dgram 192.168.1.16:750
[13250] 1451287338.658269: UDP error receiving from dgram 192.168.1.16:750: 111/Connection refused
kinit: Cannot contact any KDC for realm 'MYDOMAIN.LOCAL' while getting initial credentials

```

I'm in LAN and there is no firewall between the Ubuntu and Windows server! what else could it be? thanks

---

### Post by darkod on 2015-12-28
Was this machine previously a domain controller or not? For any domain...

The reason I am asking is because I believe the instructions are separate for DCs and member servers. You are trying to add the server now as member server but if it was a DC earlier it probably has part of the config that might get in the way.

From the samba wiki on joining as domain member (not DC): [https://wiki.samba.org/index.php/Setup_Samba_as_an_AD_Domain_Member](https://wiki.samba.org/index.php/Setup_Samba_as_an_AD_Domain_Member)

---

### Post by lorenzo-milesi on 2015-12-28
guess what... I was given the WRONG IP for the AD server :(

---

### Post by MAFoElffen on 2015-12-28
> **lorenzo-milesi said:**
> guess what... I was given the WRONG IP for the AD server :(
LOL! So if this is now solved, please revisit this thread > Use the Thread tools links at the upper right and mark this thread as "solved."

---

### Post by darkod on 2015-12-28
That's why you should use DNS ;)

You can have member servers use the DC as DNS, the same like workstations in a windows domain. Then connecting to the DC by hostname will always take you to the right place. :)

---

