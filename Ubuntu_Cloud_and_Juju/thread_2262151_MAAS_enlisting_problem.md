---
title: "MAAS enlisting problem"
date: 2015-01-23
forum: Ubuntu Cloud and Juju
---

### Post by christophe-caillet on 2015-01-23
Hi all,

I'm currently doing some tests about openstack deployment using MAAS and Juju and I don't understand why since about 4 or 5 days I'm unable to add a new node. I try to reinstall all my lab server with a maas on a 14.10 server and the new node (virtual node) is freezing with the hostname "maas-enlisting-node". I trace the problem to maas-proxy with following messages :

1422019553.843 120100 192.168.1.3 TCP_MISS_ABORTED/000 0 GET [http://archive.ubuntu.com//ubuntu/dists/trusty-updates/InRelease](http://archive.ubuntu.com//ubuntu/dists/trusty-updates/InRelease) - HIER_DIRECT/2001:67c:1360:8c01::18 -
1422019673.944 120100 192.168.1.3 TCP_MISS_ABORTED/000 0 GET [http://archive.ubuntu.com//ubuntu/dists/trusty-updates/InRelease](http://archive.ubuntu.com//ubuntu/dists/trusty-updates/InRelease) - HIER_DIRECT/2001:67c:1360:8c01::19 -
1422019794.047 120102 192.168.1.3 TCP_MISS_ABORTED/000 0 GET [http://archive.ubuntu.com//ubuntu/dists/trusty-security/InRelease](http://archive.ubuntu.com//ubuntu/dists/trusty-security/InRelease) - HIER_DIRECT/2001:67c:1360:8c01::19 -
1422019914.149 120100 192.168.1.3 TCP_MISS_ABORTED/000 0 GET [http://archive.ubuntu.com//ubuntu/dists/trusty-security/InRelease](http://archive.ubuntu.com//ubuntu/dists/trusty-security/InRelease) - HIER_DIRECT/2001:67c:1360:8c01::19 -

Before this date I've no problem and I will be able to deploy an openstack with MAAS and Juju with 26 nodes (23 virtual nodes and 3 physical nodes).

Any help will be appreciated.

Thanks by advance for your replies.

[addition]

I try again with ubuntu 14.04.1 and using ppa:maas-maintainers/stable repository for MAAS and I've the same probem

Trying with maas admin nodes accept-all ... auto enlisting is freezed
Trying with manual addition and the commisionning part is blocked

version for MAAS is 1.7.0bzr3299

[addition 01/26/2015]

adding /var/log/maas/proxy.store.log

1422272105.039 RELEASE -1 FFFFFFFF 9EFDB6CA9746629F361EEF19AAF9E97A    0        -1        -1        -1 unknown -1/-1 GET [http://archive.ubuntu.com//ubuntu/dists/trusty/universe/i18n/Translation-en.bz2](http://archive.ubuntu.com//ubuntu/dists/trusty/universe/i18n/Translation-en.bz2)
1422272225.090 RELEASE -1 FFFFFFFF 2B11760A47B93DAF06F42AF26018BBD2    0        -1        -1        -1 unknown -1/-1 GET [http://archive.ubuntu.com//ubuntu/dists/trusty/universe/i18n/Translation-en.bz2](http://archive.ubuntu.com//ubuntu/dists/trusty/universe/i18n/Translation-en.bz2)
1422272345.192 RELEASE -1 FFFFFFFF E4EFADB2A56891D3683715BAE6E33E11    0        -1        -1        -1 unknown -1/-1 GET [http://archive.ubuntu.com//ubuntu/dists/trusty-updates/main/source/Sources.bz2](http://archive.ubuntu.com//ubuntu/dists/trusty-updates/main/source/Sources.bz2)
1422272465.293 RELEASE -1 FFFFFFFF C6B73351F21D5D4F796B7942CF7745DC    0        -1        -1        -1 unknown -1/-1 GET [http://archive.ubuntu.com//ubuntu/dists/trusty-updates/main/source/Sources.bz2](http://archive.ubuntu.com//ubuntu/dists/trusty-updates/main/source/Sources.bz2)
1422272585.394 RELEASE -1 FFFFFFFF 3A73EE75F0DF62535E61E834B973202B    0        -1        -1        -1 unknown -1/-1 GET [http://archive.ubuntu.com//ubuntu/dists/trusty-updates/universe/source/Sources.bz2](http://archive.ubuntu.com//ubuntu/dists/trusty-updates/universe/source/Sources.bz2)
1422272705.496 RELEASE -1 FFFFFFFF 06797F09A6B002A51EB40F3966C6CCF9    0        -1        -1        -1 unknown -1/-1 GET [http://archive.ubuntu.com//ubuntu/dists/trusty-updates/universe/source/Sources.bz2](http://archive.ubuntu.com//ubuntu/dists/trusty-updates/universe/source/Sources.bz2)
1422272825.568 RELEASE -1 FFFFFFFF E80C68FF204689E78D89390B9DDFCFAA    0        -1        -1        -1 unknown -1/-1 GET [http://archive.ubuntu.com//ubuntu/dists/trusty-updates/main/binary-amd64/Packages.diff/Index](http://archive.ubuntu.com//ubuntu/dists/trusty-updates/main/binary-amd64/Packages.diff/Index)
1422272945.670 RELEASE -1 FFFFFFFF 15F9A4D29B924CF9209C75B3BB9B5921    0        -1        -1        -1 unknown -1/-1 GET [http://archive.ubuntu.com//ubuntu/dists/trusty-updates/main/binary-amd64/Packages.diff/Index](http://archive.ubuntu.com//ubuntu/dists/trusty-updates/main/binary-amd64/Packages.diff/Index)
1422273065.772 RELEASE -1 FFFFFFFF 2A8F85C985A7BC3A2724181B5D037B9F    0        -1        -1        -1 unknown -1/-1 GET [http://archive.ubuntu.com//ubuntu/dists/trusty-updates/universe/binary-amd64/Packages.diff/Index](http://archive.ubuntu.com//ubuntu/dists/trusty-updates/universe/binary-amd64/Packages.diff/Index)
1422273185.816 RELEASE -1 FFFFFFFF 4863DD827D05A54F8508F6050906FAFF    0        -1        -1        -1 unknown -1/-1 GET [http://archive.ubuntu.com//ubuntu/dists/trusty-updates/universe/binary-amd64/Packages.diff/Index](http://archive.ubuntu.com//ubuntu/dists/trusty-updates/universe/binary-amd64/Packages.diff/Index)
1422273305.839 RELEASE -1 FFFFFFFF 3BEE950D94ABE12D9E8383700EA34DF2    0        -1        -1        -1 unknown -1/-1 GET [http://archive.ubuntu.com//ubuntu/dists/trusty-updates/main/i18n/Translation-en.bz2](http://archive.ubuntu.com//ubuntu/dists/trusty-updates/main/i18n/Translation-en.bz2)
1422273425.939 RELEASE -1 FFFFFFFF 119811A89B481C7F16A6F01A8EBFB820    0        -1        -1        -1 unknown -1/-1 GET [http://archive.ubuntu.com//ubuntu/dists/trusty-updates/main/i18n/Translation-en.bz2](http://archive.ubuntu.com//ubuntu/dists/trusty-updates/main/i18n/Translation-en.bz2)
1422273546.040 RELEASE -1 FFFFFFFF 09E678805949675463137A5C6598ABFB    0        -1        -1        -1 unknown -1/-1 GET [http://archive.ubuntu.com//ubuntu/dists/trusty-updates/universe/i18n/Translation-en.bz2](http://archive.ubuntu.com//ubuntu/dists/trusty-updates/universe/i18n/Translation-en.bz2)
1422273666.138 RELEASE -1 FFFFFFFF BD17BF6A3B03B79AB1CC328445B29DC3    0        -1        -1        -1 unknown -1/-1 GET [http://archive.ubuntu.com//ubuntu/dists/trusty-updates/universe/i18n/Translation-en.bz2](http://archive.ubuntu.com//ubuntu/dists/trusty-updates/universe/i18n/Translation-en.bz2)
1422273786.240 RELEASE -1 FFFFFFFF 98B4B3F9F682BAA5CD93B8165ADDC7F0    0        -1        -1        -1 unknown -1/-1 GET [http://archive.ubuntu.com//ubuntu/dists/trusty-security/main/source/Sources.bz2](http://archive.ubuntu.com//ubuntu/dists/trusty-security/main/source/Sources.bz2)
1422273906.266 RELEASE -1 FFFFFFFF D0DF8F5BB7E028807A3E858472F58BA8    0        -1        -1        -1 unknown -1/-1 GET [http://archive.ubuntu.com//ubuntu/dists/trusty-security/main/source/Sources.bz2](http://archive.ubuntu.com//ubuntu/dists/trusty-security/main/source/Sources.bz2)
1422274026.367 RELEASE -1 FFFFFFFF EC9B6BAE4F8992469327315C7672EB4F    0        -1        -1        -1 unknown -1/-1 GET [http://archive.ubuntu.com//ubuntu/dists/trusty-security/universe/source/Sources.bz2](http://archive.ubuntu.com//ubuntu/dists/trusty-security/universe/source/Sources.bz2)
1422274146.398 RELEASE -1 FFFFFFFF 4D6F50EF070665066340BA7148D77FD1    0        -1        -1        -1 unknown -1/-1 GET [http://archive.ubuntu.com//ubuntu/dists/trusty-security/universe/source/Sources.bz2](http://archive.ubuntu.com//ubuntu/dists/trusty-security/universe/source/Sources.bz2)

I've also some pinger error

2015/01/26 11:33:11| Pinger exiting.
*** Error in `(pinger)': free(): invalid next size (normal): 0x00007f483ff3ddf0 ***

Maybe it is due to pyhton package upgrade for example before the upgrade of python-requests ... I've no problem ... maybe it's not in correllation ...

Is anybody have the same probem ?

PS: Finally the node is enslisting BUT it takes about 30 or maybe 45 minutes instead of 30 or 45 secondes. I have no network problem (apt is working correctly and I can join archive.ubuntu.com or other ubuntu sites without problems)

[addition 01/27/2015]

FInally I found ... the problem is due to IPv6 connectvity, the default behavour for Squid is using the v6 connectivty if the site announces IPv6 and apparently the v6 connectivity was activated on archive.ubuntu.com during the end of december so Squid wasn't been able to retrieve the files. For adressing my issue I add the followinf directive into the file /etc/maas/maas-proxy.conf and now it works perfectly.

dns_v4_first on

Regards
Christophe Caillet / SFR

---

### Post by brand2 on 2015-01-27
Thank you for posting your solution! I had the same problem with a fresh 14.04 MAAS server that I was testing. I spent a few days without being able to successfully commission any nodes. Adding the "dns_v4_first on" line to maas-proxy.conf fixed it for me too.

---

