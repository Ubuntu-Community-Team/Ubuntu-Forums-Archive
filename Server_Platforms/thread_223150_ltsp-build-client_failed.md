---
title: "ltsp-build-client failed"
date: 2006-07-26
forum: Server Platforms
---

### Post by davidsxls on 2006-07-26
I followed [https://wiki.ubuntu.com/UbuntuLTSP/LTSPQuickInstall](https://wiki.ubuntu.com/UbuntuLTSP/LTSPQuickInstall). 
Both ltsp-server-standalone and openssh-server has been installed successfully. 
DHCP server configured and tested.

When I executed $sudo ltsp-build-client, I got:

I: Retrieving Release
E: Failed getting release file [http://archive.ubuntu.com/ubuntu/dists/dapper/Release](http://archive.ubuntu.com/ubuntu/dists/dapper/Release)

so I check the URL:
$wget --spider [http://archive.ubuntu.com/ubuntu/dists/dapper/Release](http://archive.ubuntu.com/ubuntu/dists/dapper/Release)
--11:00:44--  [http://archive.ubuntu.com/ubuntu/dists/dapper/Release](http://archive.ubuntu.com/ubuntu/dists/dapper/Release)
           => `Release'
Resolving archive.ubuntu.com... 82.211.81.151, 82.211.81.182
Connecting to archive.ubuntu.com|82.211.81.151|:80... connected.
HTTP request sent, awaiting response...
  HTTP/1.0 200 OK
  Date: Tue, 25 Jul 2006 13:54:26 GMT
  Server: Apache/2.0.55 (Ubuntu)
  Last-Modified: Wed, 31 May 2006 18:59:08 GMT
  ETag: "c14544-87be-4151a256bd700"
  Accept-Ranges: bytes
  Content-Length: 34750
  Content-Type: text/plain; charset=UTF-8
  Age: 50773
  X-Cache: HIT from squid
  Via: 1.0 squid:80 (squid/2.6.STABLE1-20060724)
  Connection: close
Length: 34,750 (34K) [text/plain]
200 OK

This post might be related to my problem, [http://www.ubuntuforums.org/showthread.php?t=82053](http://www.ubuntuforums.org/showthread.php?t=82053).

I have 3 NIC:
eth0 - internet
eth1+eth2 - bridged as br0, LAN
The network are configured and work perfectly.

What should I do to get ltsp-build-client working?

TIA

---

