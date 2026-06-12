---
title: "chkrootkit output question?"
date: 2005-10-30
forum: Server Platforms
---

### Post by wargames on 2005-10-30
After doing a "sudo chkrootkit" everything looked fine except this statement:

Searching for suspicious files and directories
/lib/modules/2.6.12-9-386/volatile/.mounted

Should I be worried about this readout?

---

### Post by heimo on 2005-10-30
It's my experience that chkrootkit is sensitive to false positives.  I too got

```
Searching for suspicious files and dirs, it may take a while...
/lib/modules/2.6.12-9-k7/volatile/.mounted

```

It looks like some kind of lock file, zero length, was created at the same time as my computer was last booted, 2.6.12-9-k7=$(uname -r). Of course, if you'd suspect this file, you should not use the binaries / tools on the same machine to check it. However, I'm not worried, I think it's false positive.

---

### Post by wargames on 2005-10-30
[QUOTE=heimo]It's my experience that chkrootkit is sensitive to false positives.  I too got

```
Searching for suspicious files and dirs, it may take a while...
/lib/modules/2.6.12-9-k7/volatile/.mounted

```

It looks like some kind of lock file, zero length, was created at the same time as my computer was last booted, 2.6.12-9-k7=$(uname -r). Of course, if you'd suspect this file, you should not use the binaries / tools on the same machine to check it. However, I'm not worried, I think it's false positive.[/QUOTE]

Thanks heimo.

---

### Post by yottzumm on 2006-03-12
I got the same thing out of chkrootkit, but my snort alert log looks like
the below.  192.168.0.106 is my IP address.  I looked at the other IP addresses,
the first few go to Yahoo and AOL, and the last few go to xlogicgroup, which
I would have no idea why I would be contacting that site.

This is a fresh install, after my debian showed similar things in the snort
log.

I will try again w/o starting up GAIM.

John

[**] [122:3:0] (portscan) TCP Portsweep [**]
03/12-17:38:05.153516 192.168.0.106 -> 66.94.226.22
PROTO255 TTL:0 TOS:0x0 ID:64703 IpLen:20 DgmLen:164 DF

[**] [122:3:0] (portscan) TCP Portsweep [**]
03/12-17:59:51.017418 192.168.0.106 -> 205.188.176.103
PROTO255 TTL:0 TOS:0x0 ID:28321 IpLen:20 DgmLen:165 DF

[**] [122:3:0] (portscan) TCP Portsweep [**]
03/12-18:13:35.120666 192.168.0.106 -> 66.94.226.22
PROTO255 TTL:0 TOS:0x0 ID:10540 IpLen:20 DgmLen:163 DF

[**] [122:3:0] (portscan) TCP Portsweep [**]
03/12-18:28:22.794199 192.168.0.106 -> 64.21.33.9
PROTO255 TTL:0 TOS:0x0 ID:11673 IpLen:20 DgmLen:162 DF

[**] [122:1:0] (portscan) TCP Portscan [**]
03/12-18:28:22.794199 192.168.0.106 -> 64.21.33.9
PROTO255 TTL:0 TOS:0x0 ID:11673 IpLen:20 DgmLen:162 DF

[**] [122:4:0] (portscan) TCP Distributed Portscan [**]
03/12-18:29:20.197423 192.168.0.106 -> 64.21.33.9
PROTO255 TTL:0 TOS:0x0 ID:11726 IpLen:20 DgmLen:164 DF

---

### Post by g-a-c on 2006-03-13
[QUOTE=heimo]It's my experience that chkrootkit is sensitive to false positives.  I too got

```
Searching for suspicious files and dirs, it may take a while...
/lib/modules/2.6.12-9-k7/volatile/.mounted

```

It looks like some kind of lock file, zero length, was created at the same time as my computer was last booted, 2.6.12-9-k7=$(uname -r). Of course, if you'd suspect this file, you should not use the binaries / tools on the same machine to check it. However, I'm not worried, I think it's false positive.[/QUOTE]I agree, the same thing happens when you run chkrootkit on Gentoo, there are lots of 0-length ".keep" files to stop the package manager from deleting certain directories, and these are all flagged as suspicious too.

---

